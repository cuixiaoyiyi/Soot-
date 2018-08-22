```
jimple_method = local_declarations identity_stmts
stmts exception_ranges;
local_declarations = local_declaration local_declarations | ;
stmts = label ":" stmt ";" stmts |
stmt ";" smts | ;
exception_ranges = exception_range exception_ranges | ;
local_declaration = type name ";";
identity_stmts = identity_stmt identity_stmts | ;
stmt = breakpoint_stmt | assign_stmt | enter_monitor_stmt |
goto_stmt | if_stmt | invoke_stmt | lookup_switch_stmt | nop_stmt | ret_stmt |
return_stmt | return_void_stmt | table_switch_stmt | throw_stmt;
breakpoint_stmt = "breakpoint";
assign_stmt = variable "=" rvalue;
identity_stmt = local ":=" identity_value;
enter_monitor_stmt = "entermonitor" immediate;
exit_monitor_stmt = "exitmonitor" immediate;
goto_stmt = "goto" label;
if_stmt = "if" condition "then" label;
invoke_stmt = invoke_expr;
lookup_switch_stmt = "lookupswitch(" immediate ") {" cases " default: goto " label "}"
nop_stmt = "nop";
ret_stmt = "ret" local;
return_stmt = "return" immediate;
return_void_stmt = "return" ;
table_switch_stmt = "tableswitch(" immediate ") {" cases " default: goto " label "}"
throw_stmt = "throw" immediate;
cases = case cases | ;
case = "case " int_constant ": goto " label;
condition = eq_expr | ge_expr | le_expr | lt_expr | ne_expr | gt_expr;
rvalue = array_ref | constant | expr | instance_field_ref | local | next_next_stmt_address | static_field_ref;
identity_value = caught_exception_ref | parameter_ref | this_ref;
variable = array_ref | instance_field_ref | static_field_ref | local;
immediate = constant | local;
expr = binop_expr | cast_expr | instance_of_expr | invoke_expr | new_array_expr |
new_expr | new_multi_array_expr | unop_expr;
binop_expr = add_expr | and_expr | cmp_expr | cmpg_expr | cmpl_expr | div_expr |
eq_expr | ge_expr | gt_expr | le_expr | lt_expr | mul_expr | ne_expr | or_expr |
rem_expr | shl_expr | shr_expr | sub_expr | ushr_expr | xor_expr;
add_expr = immediate "+" immediate;
and_expr = immediate "&" immediate;
cmp_expr = immediate "cmp" immediate;
cmpg_expr = immediate "cmpg" immediate;
cmpl_expr = immediate "cmpl" immediate;
div_expr = immediate "/" immediate;
eq_expr = immediate "==" immediate;
ge_expr = immediate ">=" immediate;
gt_expr = immediate ">" immediate;
le_expr = immediate "<=" immediate;
lt_expr = immediate "<" immediate;
mul_expr = immediate "*" immediate;

ne_expr = immediate "!=" immediate;
or_expr = immediate "|" immediate;
rem_expr = immediate "%" immediate;
shl_expr = immediate "<<" immediate;
shr_expr = immediate ">>" immediate;
sub_expr = immediate "-" immediate;
ushr_expr = immediate "ushr" immediate;
xor_expr = immediate "xor" immediate;
cast_expr = "(" type ")" immediate;
instance_of_expr = immediate "instanceof" ref_type;
invoke_expr = interface_invoke_expr | special_invoke_expr | static_invoke_expr |
virtual_invoke_expr;
static_invoke_expr = "staticinvoke" "[" method_signature "](" immediate_list ")";
interface_invoke_expr = "interfaceinvoke" immediate ".[" + method_signature "]"
"(" immediate_list ")";
special_invoke_expr = "specialinvoke" immediate ".[" method_signature "]"
"(" immediate_list ")";
virtual_invoke_expr = "virtualinvoke" immediate ".[" method_signature "]"
"(" immediate_list ")";
immediate_list = immediate | immediate immediate_next_list | ;
immediate_next_list = "," immediate immediate_next_list | ;
new_array_expr = "new" type "[" immediate "]";
new_expr = "new" ref_type "()";
new_multi_array_expr = "new multiarray " type sized_dims empty_dims;
sized_dims = "[" immediate "]" next_sized_dims;
next_sized_dims = "[" immediate "]" next_sized_dims | ;
empty_dims = "[]" empty_dims | ;
unop_expr = length_expr | neg_expr;
length_expr = "length" immediate;
neg_expr = "-" immediate;
array_ref = immediate "[" immediate "]";
instance_field_ref = immediate ".[" field_signature "]";
static_field_ref = "[" field_signature "]";
method_signature = identifier "(" type_list "):" type;
field_signature = identifier ":" type;
type_list = type type_next_list | ;
type_next_list = "," type type_next_list | ;
caught_exception_ref = "@caughtexception";
parameter_ref = "@parameter" int_constant;
this_ref = "@this";
label = identifier;
local = identifier;
constant = double_constant | float_constant | int_constant | long_constant |
string_constant | null_constant;
type = int_type | long_type | float_type | double_type | ref_type |
stmt_address_type | void_type;
exception_range = ".catch" ref_type "from" label "to" label "using" label;
```

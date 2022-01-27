<html>
	<body>
		<h1 style="font-family: Arial; text-align: center;">Zend_Op_Array</h1>
		<p style="text-align:center;">Modify by:MG193.7
		<p style="text-align:center;"><a href="https://www.cnblogs.com/aldys4">My Blog</a>
		<p style="text-align:center;"><a href="https://github.com/MG1937">My Github</a>
		<p style="text-align:center;">Base on <a href="https://php.uz/manual/en/internals2.opcodes.php">vld document</a>
		<p>
		<table style="text-align: left; font-family: Arial; width: 100%;table-layout: fixed;word-break: break-all;" border="1" cellpadding="2" cellspacing="2">
			<tbody>
				<tr style="text-align:left; vertical-align: top;font-family: Arial;font-weight: bold;">
					<td width="20%">Opcode name</td>
					<td>Explanation</td>
					<td>Example (phpdbg)</td>
				</tr>
				<tr>
					<td>NOP</td>
					<td>no operation</td>
					<td>NOP</td>
				</tr>
				<tr>
					<td>ADD</td>
					<td>Adds "value1" to "value2" and stores the result into "result".</td>
					<td>ADD 1 2 ~0<br>
					$a = 1+2;</td>
				</tr>
				<tr>
					<td>SUB</td>
					<td>Subtracts "value2" from "value1" and stores the result into "result".</td>
					<td>SUB 2 1 ~0<br>
					$a = 2-1;</td>
				</tr>
				<tr>
					<td>MUL</td>
					<td>Multiplys "value1" by "value2" and stores the result into "result".</td>
					<td>MUL 1 2 ~0<br>
					$a = 1*2;</td>
				</tr>
				<tr>
					<td>DIV</td>
					<td>Divides "value1" by "value2" and stores the result into "result".</td>
					<td>DIV 6 3 ~0<br>
					$a = 6/3;</td>
				</tr><tr>
					<td>MOD</td>
					<td>Makes the value of "result" congruent to "value1" modulo "value2".</td>
					<td>MOD 6 3 ~0<br>
					$a = 6%3;</td>
				</tr><tr>
					<td>SL</td>
					<td>Shift bits of value1 to the left value2 steps (each step means "multiply by two")</td>
					<td>SL 8 2 ~0<br>
						$a = 8<<2;</td>
				</tr><tr>
					<td>SR</td>
					<td>Shift bits of value1 to the right value2 steps (each step means "divide by two")</td>
					<td>SR 8 2 ~0<br>
						$a = 8>>2;</td>
				</tr><tr>
					<td>CONCAT</td>
					<td>Concats string values string1 and string2</td>
					<td>CONCAT "A" "B" ~0<br>
					echo "A"."B";</td>
				</tr><tr>
					<td>BW_OR</td>
					<td>Bit-wise or of value1 and value2</td>
					<td>BW_OR 1 2 ~0<br>
					echo 1|2;</td>
				</tr><tr>
					<td>BW_AND</td>
					<td>Bit-wise and of value1 and value2</td>
					<td>BW_AND 1 2 ~0<br>
					echo 1&2;</td>
				</tr><tr>
					<td>BW_XOR</td>
					<td>Bit-wise xor of value1 and value2</td>
					<td>BW_XOR 1 2 ~0<br>
					echo 1^2;</td>
				</tr><tr>
					<td>BW_NOT</td>
					<td>Bit-wise not of "value"</td>
					<td>BW_NOT 15 ~0<br>
					echo ~15;</td>
				</tr><tr>
					<td>BOOL_NOT</td>
					<td>Boolean (logical) not of "value"</td>
					<td>BOOL_NOT 1 ~0<br>
					echo !1;</td>
				</tr><tr>
					<td>BOOL_XOR</td>
					<td>Boolean (logical) xor of value1</td>
					<td>BOOL 1 2 ~0<br>
					echo 1 xor 2;</td>
				</tr><tr>
					<td>IS_IDENTICAL</td>
					<td>Compares value1 and value2 to see if they are equal AND have the same type</td>
					<td>IS_IDENTICAL 1 1 ~0<br>
					echo (1===1);</td>
				</tr><tr>
					<td>IS_NOT_IDENTICAL</td>
					<td>compares value1 and value2 to see if they are unequal or of different types</td>
					<td>IS_NOT_IDENTICAL 1 1 ~0<br>
					echo (1!==1);</td>
				</tr><tr>
					<td>IS_EQUAL</td>
					<td>compares if value1 and value2 are equal</td>
					<td>IS_EQUAL 1 1 ~0<br>
					echo (1==1);</td>
				</tr><tr>
					<td>IS_NOT_EQUAL</td>
					<td>compares if value1 and value2 are not equal</td>
					<td>IS_NOT_EQUAL 1 1 ~0<br>
					echo (1!=1);</td>
				</tr><tr>
					<td>IS_SMALLER</td>
					<td>compares if value1 is less than value2</td>
					<td>IS_SMALLER1 1 2 ~0<br>
						echo (1 < 2);</td>
				</tr><tr>
					<td>IS_SMALLER_OR_EQUAL</td>
					<td>compares if value1 is less than or equal to value2</td>
					<td>IS_SMALLER_OR_EQUAL 2 1 ~0<br>
						echo (2<=1);</td>
				</tr><tr>
					<td>CAST</td>
					<td>casts value1 as type value2 (type in extended_value)</td>
					<td>CAST<4> 1 ~0<br>
					echo (int)1;</td>
				</tr><tr>
					<td>QM_ASSIGN</td>
					<td>Question Mark Assign, used twice inside a question mark assign to temporarily assign result as value1  (this is followed up with an ASSIGN bytecode)</td>
					<td>
						JMPZ 1 J3<br>
						QM_ASSIGN 1 ~0<br>
						JMP J4<br>
						QM_ASSIGN 2 ~0<br>
						ECHO ~0<br>
						echo (1?1:2);
					</td>
				</tr><tr>
					<td>ASSIGN_ADD</td>
					<td>Add value1 to value2 and store in variable indicated by value1</td>
					<td>ASSIGN_ADD $a 2<br>
					$a+=2;</td>
				</tr><tr>
					<td>ASSIGN_SUB</td>
					<td>Subtract value1 from value2 and store in variable indicated by value1</td>
					<td>ASSIGN_SUB $a 2<br>
					$a-=2;</td>
				</tr><tr>
					<td>ASSIGN_MUL</td>
					<td>Multiply result by value1 and store in variable indicated by result</td>
					<td>ASSIGN_MUL $a 2<br>
					$a*=2;</td>
				</tr><tr>
					<td>ASSIGN_DIV</td>
					<td>Divide result by value1and store in variable indicated by result.</td>
					<td>ASSIGN_DIV $a 2<br>
					$a/=2;</td>
				</tr><tr>
					<td>ASSIGN_MOD</td>
					<td>Perform result mod value1 and store in variable indicated by result</td>
					<td>ASSIGN_MOD $a 2<br>
					$a%=2;</td>
				</tr><tr>
					<td>ASSIGN_SL</td>
					<td>Shift result by value1 bits to left and store in variable indicated by result</td>
					<td>ASSIGN_SL $a 2<br>
						$a<<=2;</td>
				</tr><tr>
					<td>ASSIGN_SR</td>
					<td>Shift result by value1 bits to right and store in variable indicated by result</td>
					<td>ASSIGN_SR $a 2<br>
						$a>>=2;</td>
				</tr><tr>
					<td>ASSIGN_CONCAT</td>
					<td>Concats string values result and value1 and store in variable indicated by result</td>
					<td>ASSIGN_CONCAT $a 'z'<br>
					$a.='z';</td>
				</tr><tr>
					<td>ASSIGN_BW_OR</td>
					<td>Performs binary OR on result and value1 and stores in variable indicated by result.</td>
					<td>ASSIGN_BW_OR $a 64<br>
					$a|=64;</td>
				</tr><tr>
					<td>ASSIGN_BW_AND</td>
					<td>Performs binary AND on result and value1 and stores in variable indicated by result.</td>
					<td>ASSIGN_BW_AND $a 64<br>
					$a &=64;</td>
				</tr><tr>
					<td>ASSIGN_BW_XOR</td>
					<td>Performs binary XOR on result and value1and stores in variable indicated by result.</td>
					<td>ASSIGN_BW_XOR $a 64<br>
					$a ^=64;</td>
				</tr><tr>
					<td>PRE_INC</td>
					<td>increments variable indicated by value1 by 1 (before performing other operations) and stores in result</td>
					<td>PRE_INC $a<br>
					++$a;</td>
				</tr><tr>
					<td>PRE_DEC</td>
					<td>decrements variable indicated by value1 by 1 (before performing other operations) and stores in results</td>
					<td>PRE_DEC $a<br>
					--$a;</td>
				</tr><tr>
					<td>POST_INC</td>
					<td>increments variable indicated by value1 by 1 (after performing other operations) and stores in result</td>
					<td>POST_INC $a ~0<br>
					$a++;</td>
				</tr><tr>
					<td>POST_DEC</td>
					<td>decrements variable indicated by value1 by 1 (after performing other operations) and stores in result</td>
					<td>POST_DEC $a ~0<br>
					$a--;</td>
				</tr><tr>
					<td>ASSIGN</td>
					<td>assigns value1 to result</td>
					<td>ASSIGN $a $b<br>
					$a=$b;</td>
				</tr><tr>
					<td>ASSIGN_REF</td>
					<td>UNKNOW in phpdbg.<br>
						Maybe you could refer to <a href="https://php.uz/manual/en/internals2.opcodes.assign-ref.php">ASSIGN_REF</a></td>
					<td>UNKNOW</td>
				</tr><tr>
					<td>ECHO</td>
					<td>Dump text</td>
					<td>ECHO "hello world"<br>
					echo "hello world";</td>
				</tr><tr>
					<td>PRINT</td>
					<td>Same as ECHO?</td>
					<td>ECHO<1> "hello world"<br>
						print 'hello world';<br>
						If you want to refer the opcodes in vld,<br>you could see <a href="https://php.uz/manual/en/internals2.opcodes.print.php">PRINT</a>
					</td>
				</tr><tr>
					<td>JMP</td>
					<td>Unconditonally jump to the address</td>
					<td>#0 IS_EQUAL $a "a" ~0<br>
						#1 JMPZ ~0 J4<br>
						#2 ECHO 1<br>
						#3 JMP J5<br>
						#4 ECHO 2<br>
						#5 RETURN<-1> 1<br><br>
						if($a=="a"){echo 1;}else{echo 2;}</td>
				</tr><tr>
					<td>JMPZ</td>
					<td>Jump to the address if the value is zero</td>
					<td>You could see the opcodes in JMP</td>
				</tr><tr>
					<td>JMPNZ</td>
					<td>Jump to the address if the value is not zero</td>
					<td>...<br>
						JMPNZ ~0 JX<br>
						...<br><br>
						if($b!=0){...}
					</td>
				</tr><tr>
					<td>JMPZNZ</td>
					<td>Jump to the address given in the operands if the value is zero;<br>jump to the address given in extended data if nonzero.</td>
					<td>UNKNOW in phpdbg<br>
						You could refer to <a href="https://php.uz/manual/en/internals2.opcodes.jmpznz.php">JMPZNZ</a></td>
				</tr><tr>
					<td>JMPZ_EX</td>
					<td>Jump to the address if the value is zero.</td>
					<td>#0 JMPZ_EX $a J2 ~0<br>
						#1 BOOL true ~0<br>
						#2 JMPZ ~0<br>
						#3 RETURN<-1> 1<br><br>
						if($a&&true){}</td>
				</tr><tr>
					<td>JMPNZ_EX</td>
					<td>Jump to the address if the value is not zero.</td>
					<td>#0 JMPZ_EX $a J2 ~0<br>
						#1 BOOL true ~0<br>
						#2 JMPZ ~0<br>
						#3 RETURN<-1> 1<br><br>
						if($a||true){}</td>
				</tr><tr>
					<td>CASE</td>
					<td>UNKNOW</td>
					<td>Do not found CASE opcode in phpdbg,<br>
						You could refer to <a href="https://php.uz/manual/en/internals2.opcodes.case.php">CASE</a></td>
				</tr><tr>
					<td>SWITCH_FREE</td>
					<td>Release the allocated space of "value"?</td>
					<td>Do not found SWITCH_FREE in phpdbg,<br>
						You could refer to <a href="https://php.uz/manual/en/internals2.opcodes.switch-free.php">SWITCH_FREE</a>
					</td>
				</tr><tr>
					<td>BRK</td>
					<td>It means "break" in vld,<br>But not found this opcode in phpdbg.<br>
					If you want to break in while-loop(or something else),phpdbg will simply use JMP opcode jump out the loop,instead of use "BRK" opcode.</td>
					<td>#0 JMP J2<br>
						#1 JMP J3<br>
						#2 JMPNZ 1 J1<br>
						#3 RETURN<-1> 1<br><br>
						while(1){break;}<br>
						You also could see <a href="https://php.uz/manual/en/internals2.opcodes.brk.php">BRK</a></td>
				</tr><tr>
					<td>CONT</td>
					<td>Same as BRK opcode,<br>
						this opcode means "continue" in vld,<br>
						But not found this opcode in phpdbg.<br>
					phpdbg still use JMP to control the flow in loop.</td>
					<td>You could refer to <a href="https://php.uz/manual/en/internals2.opcodes.cont.php">CONT</a></td>
				</tr><tr>
					<td>BOOL</td>
					<td>convert value to boolean and store in result</td>
					<td>#0 JMPZ_EX $a J2 ~0<br>
						#1 BOOL true ~0<br>
						#2 JMPZ ~0<br>
						#3 RETURN<-1> 1<br><br>
						if($a&&true){}</td>
				</tr><tr>
					<td>ROPE_INIT</td>
					<td>when create a string that cotains variable,<br>
					this opcode used to init this string and store the string of begining part to result</td>
					<td>ROPE_INIT<3> "Test" ~1<br>
						ROPE_ADD<1> ~1 $a ~1<br>
						ROPE_END<2> ~1 " Test" ~0<br>
						ECHO ~0<br><br>
						echo "Test$a Test";</td>
				</tr><tr>
					<td>ROPE_ADD</td>
					<td>after ROPE_INIT opcode,continue add a variable to string,and store the string to result.</td>
					<td>Could see ROPE_INIT part</td>
				</tr><tr>
					<td>ROPE_END</td>
					<td>after ROPE_INIT opcode,continue add a string to the whole string,and treat the string just added as the end of the whole string.</td>
					<td>Could see ROPE_INIT part</td>
				</tr><tr>
					<td>FAST_CONCAT</td>
					<td>concats value1 and value2,than stored it to the result</td>
					<td>
						FAST_CONCAT "Test" $a ~0<br>
						ECHO ~0<br><br>
						echo "Test$a";
					</td>
				</tr><tr>
					<td>BEGIN_SILENCE</td>
					<td>prepare to perform function call without displaying error messages</td>
					<td>BEGIN_SILENCE ~0<br>
						INIT_FCALL<1> 96 "file"<br>SEND_VAL"non_existent_file" 1<br>
						DO_ICALL @1<br>
						END_SILENCE ~0<br>
						ASSIGN $a @1<br>
						RETURN<-1> 1<br><br>
						$a = @file("non_existent_file");</td>
				</tr><tr>
					<td>END_SILENCE</td>
					<td>no longer surpress error messages</td>
					<td>See BEGIN_SILENCE part</td>
				</tr><tr>
					<td>INIT_FCALL</td>
					<td>init a function going to call</td>
					<td>INIT_FCALL<1> 96 "abs"<br>
						SEND_VAL 2 1<br>
						DO_ICALL<br><br>
						abs(2);</td>
				</tr><tr>
					<td>INIT_DYNAMIC_CALL</td>
					<td>call to function dynamicly</td>
					<td>ASSIGN $x "phpinfo"<br>
						INIT_DYNAMIC_CALL $x<br>
						DO_FCALL<br><br>
						$x = 'phpinfo';<br>$x();</td>
				</tr><tr>
					<td>INIT_FCALL_BY_NAME</td>
					<td>call to function</td>
					<td>INIT_FCALL_BY_NAME "test"<br>
						DO_FCALL @1<br>
						ASSIGN $a @1<br><br>
						$a = test();</td>
				</tr><tr>
					<td>DO_FCALL</td>
					<td>Call a function.<br>
					If the result of called function was stored to a variable,this opcode must take a result!</td>
					<td>See INIT_DYNAMIC_CALL and INIT_FCALL_BY_NAME part</td>
				</tr><tr>
					<td>DO_FCALL_BY_NAME</td>
					<td>Call a function by name.</td>
					<td>UNKNOW in phpdbg,<br>
						You could see <a href="https://php.uz/manual/en/internals2.opcodes.do-fcall-by-name.php">DO_FCALL_BY_NAME</a></td>
				</tr><tr>
					<td>RETURN</td>
					<td>Return value from a funciton.</td>
					<td>RETURN 1<br>
					return 1;</td>
				</tr><tr>
					<td>RECV</td>
					<td>Receive the number of functoin arguments</td>
					<td>RECV 1 $a<br>
						RETURN<-1> null<br><br>
						function test($a){}</td>
				</tr><tr>
					<td>RECV_INIT</td>
					<td>Initialize a function argument with "value" if not received from caller.<br>
					Otherwise same as RECV.</td>
					<td>RECV_INIT 1 "test" $t<br>
						RETURN<-1> null<br><br>
						function a($t="test"){}</td>
				</tr><tr>
					<td>SEND_VAL</td>
					<td>Pass the constant value as an actual parameter to a function.</td>
					<td>INIT_FCALL<2> 112 "hello"<br>
						SEND_VAL "world" 1<br>
						SEND_VAL "ok" 2<br>
						DO_FCALL<br><br>
						hello("world","ok");</td>
				</tr><tr>
					<td>SEND_VAL_EX</td>
					<td>Pass the constant value as an actual parameter to a function.Same as SEND_VAL_EX</td>
					<td>INIT_FCALL_BY_NAME<2> "hello"<br>
						SEND_VAL_EX "world" 1<br>
						SEND_VAL_EX "ok" 2<br>
						DO_FCALL<br><br>
						hello("world","ok");</td>
				</tr><tr>
					<td>SEND_VAR</td>
					<td>Pass the variable value as an actual parameter to a function.</td>
					<td>ASSIGN $a 1<br>
						INIT_FCALL<1> 96 "abs"<br>
						SEND_VAR $a 1<br>
						DO_ICALL<br><br>
						$a=1;abs($a);</td>
				</tr><tr>
					<td>SEND_VAR_EX</td>
					<td>Pass the variable value as an actual parameter to a function.Same as SEND_VAR.</td>
					<td>ASSIGN $a 1<br>
						INIT_FCALL_BY_NAME<1> "test"<br>
						SEND_VAR_EX $a 1<br>
						DO_ICALL<br><br>
						$a=1;test($a);</td>
				</tr><tr>
					<td>SEND_REF</td>
					<td>Pass the reference value as an actual parameter to a function.</td>
					<td>INIT_FCALL<1> 96 "each"<br>
						SEND_REF $a 1<br>
						DO_ICALL<br><br>
					@each($a);</td>
				</tr><tr>
					<td>NEW</td>
					<td>Construct an instance of "type" and store the reference to the object into "result".</td>
					<td>NEW<2> "A" @1<br>
						SEND_VAL_EX "a" 1<br>
						DO_FCALL<br>
						FREE @1<br><br>
						new A("a");
					</td>
				</tr><tr>
					<td>INIT_NS_FCALL_BY_NAME</td>
					<td>No sample in vld or phpdbg.</td>
					<td>UNKNOW</td>
				</tr><tr>
					<td>FREE</td>
					<td>Release the allocated space of the value.</td>
					<td>Could see NEW part</td>
				</tr><tr>
					<td>INIT_ARRAY</td>
					<td>Allocate a new array with elem-value as the first element of the array.</td>
					<td>UNKNOW in phpdbg,<br>
						You could refer to <a href="https://php.uz/manual/en/internals2.opcodes.init-array.php">INIT_ARRAY</a></td>
				</tr><tr>
					<td>ADD_ARRAY_ELEMENT</td>
					<td>Add elem-value as an element to array-value</td>
					<td>UNKNOW in phpdbg,<br>
						You could refer to <a href="https://php.uz/manual/en/internals2.opcodes.add-array-element.php">ADD_ARRAY_ELEMENT</a></td>
				</tr><tr>
					<td>INCLUDE_OR_EVAL</td>
					<td>Include the file specified by filename and eval it.</td>
					<td>INCLUDE_OR_EVAL<2> "test.php"<br>
						INCLUDE_OR_EVAL<1> "echo 1;"<br><br>
							include "test.php";<br>
						eval("echo 1;");</td>
				</tr><tr>
					<td>UNSET_CV</td>
					<td>Unset the variable.</td>
					<td>UNSET_CV $A<br>
					unset($A);</td>
				</tr><tr>
					<td>UNSET_VAR</td>
					<td>Unset the variable.</td>
					<td>ASSIGN $A "x"<br>
						UNSET_VAR<4> $A<br><br>
							$A="x";<br>
						unset($$A);</td>
				</tr><tr>
					<td>UNSET_DIM</td>
					<td>Unset the entry of array-value, which is specified by index</td>
					<td>UNSET_DIM $A 0<br>
					unset($A[0]);</td>
				</tr><tr>
					<td>UNSET_OBJ</td>
					<td>Unset the property of the current object</td>
					<td>UNSET_OBJ<8> $A "test"<br>
						unset($A->test);</td>
				</tr><tr>
					<td>FE_RESET_R</td>
					<td>Initialize an iterator on array-value.  If the array is empty, jump to address.</td>
					<td>#0 ASSIGN $a array(3)<br>
						#1 FE_RESET_R $a J5 @1<br>
						#2 FE_FETCH_R<96> @1 $num<br>
							#3 ECHO<1> $num<br>
								#4 JMP J2<br>
								#5 FE_FREE @1<br><br>
								$a = array(1,2,3);<br>
								foreach($a as $num){<br>
								    print $num;<br>}</td>
				</tr><tr>
					<td>FE_FETCH_R</td>
					<td>Fetch an element from iterator.<br>If no element is available, jump to the address that FE_RESET_R opcode setted.</td>
					<td>Could see FE_RESET_R part.</td>
				</tr><tr>
					<td>EXIT</td>
					<td>Exit running after dumping "message".</td>
					<td>EXIT "foo"<br>
					die("foo");</td>
				</tr><tr>
					<td>FETCH_R</td>
					<td>fetch <a href="https://www.php.net/manual/en/language.variables.variable.php">Variable variables.</a></td>
					<td>ASSIGN $a "x"<br>
						FETCH_R<4> $a ~1<br>
							ECHO ~1<br><br>
							$a="x";<br>
						echo $$a;</td>
				</tr><tr>
					<td>FETCH_DIM_R</td>
					<td>fetch value of variables by index.</td>
					<td>FETCH_R<4> $a ~1<br>
						FETCH_DIM_R ~1 0 ~2<br>
						ECHO ~2<br><br>
					echo $$a[0];<br><br>
					FETCH_DIM_R $x 0<br>
				$x[0];</td>
				</tr><tr>
					<td>FETCH_OBJ_R</td>
					<td>fetch property value of Variable variables</td>
					<td>FETCH_R<4> $a ~1<br>
						FETCH_OBJ_R ~1 "test" ~2<br>
						ECHO ~2<br><br>
						echo($$a->test);
						</td>
				</tr><tr>
					<td>FETCH_W</td>
					<td>fetch Variable variables and make it writable.</td>
					<td>ASSIGN $x 1<br>
						ASSIGN $a "x"<br>
						FETCH_W<4> $a @2<br>
							ASSIGN @2 2<br><br>
							$x=1;<br>
							$a="x";<br>
						$$a=2;</td>
				</tr><tr>
					<td>FETCH_DIM_W</td>
					<td>fetch Variable variables by index and make it writable.</td>
					<td>FETCH_DIM_W $x 0 @0<br>
						ASSIGN_DIM @0 1<br>
						OP_DATA 2<br><br>
					$x[0][1]=2;</td>
				</tr><tr>
					<td>FETCH_OBJ_W</td>
					<td>fetch property value of Variable variables and make it writable.</td>
					<td>FETCH_OBJ_W $x "t" @0<br>
						ASSIGN_OBJ<16> @0 "test"<br>
							OP_DATA 1<br><br>
							$x->t->test=1;</td>
				</tr><tr>
					<td>FETCH_RW</td>
					<td>fetch value of Variable variables.</td>
					<td>FETCH_RW<4> $a @0<BR>
						POST_INC @0;<br><br>
					$$a++;</td>
				</tr><tr>
					<td>FETCH_DIM_RW</td>
					<td>fetch value of Variable variables by index.</td>
					<td>FETCH_DIM_RW $a 0 @0<br>
					POST_INC @0<br><br>
				$a[0]++;</td>
				</tr><tr>
					<td>FETCH_OBJ_RW</td>
					<td>fetch property value of Variable variables</td>
					<td>FETCH_OBJ_RW $a "b" @0<br>
						POST_INC_OBJ<16> @0 "c"<br><br>
							$a->b->c++;</td>
				</tr><tr>
					<td>FETCH_IS</td>
					<td>Fetch the value from variable which is to be used to test if it is set or not, through isset()/isempty().</td>
					<td>FETCH_IS<2> "_GET" ~0<br>
						ISSET_ISEMPTY_DIM_OBJ ~0 0<br><br>
					isset($_GET[0]);</td>
				</tr><tr>
					<td>FETCH_DIM_IS</td>
					<td>No php sample.</td>
					<td></td>
				</tr><tr>
					<td>FETCH_OBJ_IS</td>
					<td>No php sample.</td>
					<td></td>
				</tr><tr>
					<td>FETCH_FUNC_ARG</td>
					<td>fetch value of Variable variables as arg of function</td>
					<td>INIT_FCALL_BY_NAME<1> "test"<br>
						CHECK_FUNC_ARG 1<BR>
						FETCH_FUNC_ARG<4> $a @0<br>
							SEND_FUNC_ARG @0 1<br>
							DO_FCALL<br><br>
						test($$a);</td>
				</tr><tr>
					<td>FETCH_DIM_FUNC_ARG</td>
					<td>fetch value of variable by index as arg of function</td>
					<td>INIT_FCALL_BY_NAME<1> "test"<br>
						CHECK_FUNC_ARG 1<BR>
							FETCH_DIM_FUNC_ARG $a 0 @0<BR>
							SEND_FUNC_ARG @0 1<br>
							DO_FCALL<br><br>
						test($a[0]);</td>
				</tr><tr>
					<td>FETCH_OBJ_FUNC_ARG</td>
					<td>fetch property value of variable as arg of function</td>
					<td>INIT_FCALL_BY_NAME<1> "test"<br>
						CHECK_FUNC_ARG 1<BR>
							FETCH_OBJ_FUNC_ARG $a "b" @0<BR>
							SEND_FUNC_ARG @0 1<br>
							DO_FCALL<br><br>
						test($a->b);</td>
				</tr><tr>
					<td>FETCH_UNSET</td>
					<td>Fetch a variable for the purpose of unset() operation.</td>
					<td>FETCH_UNSET<4> $A @1<br>
						UNSET_DIM @1 0<br><br>
						unset($$A[0]);</td>
				</tr><tr>
					<td>FETCH_DIM_UNSET</td>
					<td>Fetch a variable by index for the purpose of unset() operation.</td>
					<td>FETCH_DIM_UNSET $a 0 @0<br>
						UNSET_OBJ @0 "b"<br><br>
						unset($a[0]->b);</td>
				</tr><tr>
					<td>FETCH_OBJ_UNSET</td>
					<td>Fetch a property value of variable for the purpose of unset() operation.</td>
					<td>FETCH_OBJ_UNSET $a "b" @0<br>
						UNSET_OBJ<16> @0 "c"<BR><BR>
							unset($a->b->c);</td>
				</tr><tr>
					<td>FETCH_LIST_R</td>
					<td>Fetch array list.</td>
					<td>FETCH_LIST_R array(2) 0 @0<br>
						ASSIGN $x @0<br>
						FETCH_LIST_R array(2) 1 @2<br>
						ASSIGN $b @2<br><br>
						list($x,$b) = array("x","b"); 
					</td>
				</tr><tr>
					<td>FETCH_DIM_TMP_VAR</td>
					<td>No php sample in phpdbg</td>
					<td>You could refer to <a href="https://php.uz/manual/en/internals2.opcodes.fetch-dim-tmp-var.php">FETCH_DIM_TMP_VAR</a></td>
				</tr><tr>
					<td>FETCH_CONSTANT</td>
					<td>fetch value by const name.</td>
					<td>FETCH_CONSTANT "A" ~0<br>
						ECHO ~0<br><br>
					echo A;</td>
				</tr><tr>
					<td>GOTO</td>
					<td>No sample in phpdbg and vld,<br>
					phpdbg use JMP opcode to control flow.</td>
					<td></td>
				</tr><tr>
					<td>EXT_STMT</td>
					<td>No php sample</td>
					<td></td>
				</tr><tr>
					<td>EXT_FCALL_BEGIN</td>
					<td>No php sample</td>
					<td></td>
				</tr><tr>
					<td>EXT_FCALL_END</td>
					<td>No php sample</td>
					<td></td>
				</tr><tr>
					<td>EXT_NOP</td>
					<td>No php sample</td>
					<td></td>
				</tr><tr>
					<td>TICKS</td>
					<td></td>
					<td>TICKS<100><br>
					declare(ticks=100);</td>
				</tr><tr>
					<td>SEND_VAR_NO_REF</td>
					<td>No php sample</td>
					<td></td>
				</tr><tr>
					<td>CATCH</td>
					<td>catch when Exception get throw.</td>
					<td>#0 THROW $t<br>
						#1 JMP J4<br>
						#2 CATCH<1> "A" $e<br>
						#3 ECHO "catch"<br>
						#4 RETURN<-1> 1<br><br>
							try{throw $t}<br>
							catch(A $e){echo "catch";}
					</td>
				</tr><tr>
					<td>THROW</td>
					<td>throw some Exception.</td>
					<td>THROW $t<br>
					throw $t;</td>
				</tr><tr>
					<td>FETCH_CLASS</td>
					<td>fetch static class</td>
					<td>FETCH_CLASS $obj @0<br>
						FETCH_CLASS_CONSTANT @0 "a"<br><br>
					$obj::a;</td>
				</tr><tr>
					<td>FETCH_CLASS_CONSTANT</td>
					<td>fetch static constant from class</td>
					<td>Could see FETCH_CLASS part.</td>
				</tr><tr>
					<td>FETCH_STATIC_PROP_R</td>
					<td>fetch static property value from class</td>
					<td>FETCH_CLASS $obj @0<br>
						FETCH_STATIC_PROP_R "a" @0 ~1<br><br>
					$obj::$a;</td>
				</tr><tr>
					<td>FETCH_STATIC_PROP_RW</td>
					<td>fetch static property value from class,same as FETCH_STATIC_PROP_R but make it readable and writable.</td>
					<td>FETCH_CLASS $obj @0<br>
						FETCH_STATIC_PROP_RW "a" @0 @1<br>
						POST_INC @1 ~2<BR><br>
					$obj::$a++;</td>
				</tr><tr>
					<td>FETCH_STATIC_PROP_W</td>
					<td>fetch static property value from class  AND make it writable.</td>
					<td>FETCH_CLASS $obj @0<br>
						FETCH_STATIC_PROP_W "a" @0 @1<br>
						ASSIGN @1 1<BR><br>
					$obj::$a=1;</td>
				</tr><tr>
					<td>CLONE</td>
					<td>clone an object</td>
					<td>CLONE $t ~0<br>
					clone $t;</td>
				</tr><tr>
					<td>RETURN_BY_REF</td>
					<td>No sample in phpdbg</td>
					<td></td>
				</tr><tr>
					<td>INIT_METHOD_CALL</td>
					<td>Prepare for a method call. Followed by DO_FCALL.</td>
					<td>INIT_METHOD_CALL $obj "a"<br>
						DO_FCALL<br><br>
						$obj->a();</td>
				</tr><tr>
					<td>INIT_STATIC_METHOD_CALL</td>
					<td>Prepare for a static method call. Followed by DO_FCALL.</td>
					<td>FETCH_CLASS $obj @0<br>
						INIT_STATIC_METHOD_CALL @0 "a"<BR>
						DO_FCALL<BR><br>
					$obj::a();</td>
				</tr><tr>
					<td>ISSET_ISEMPTY_CV</td>
					<td>check wether a variable is setted and store the result.</td>
					<td>ISSET_ISEMPTY_CV $a ~0<br>
					isset($a);</td>
				</tr><tr>
					<td>ISSET_ISEMPTY_VAR</td>
					<td>check wether a variable is setted and store the result.</td>
					<td>ISSET_ISEMPTY_VAR<4> $a ~0<br>
					isset($$a);</td>
				</tr><tr>
					<td>ISSET_ISEMPTY_DIM_OBJ</td>
					<td>check wether a variable is setted by its index and store the result.</td>
					<td>ISSET_ISEMPTY_DIM_OBJ $a 0 ~0<br>
					isset($a[0]);</td>
				</tr><tr>
					<td>ZEND_SEND_VAL_EX</td>
					<td></td>
					<td>Could see SEND_VAL_EX part.</td>
				</tr><tr>
					<td>ZEND_SEND_VAR</td>
					<td></td>
					<td>Could see SEND_VAR part.</td>
				</tr><tr>
					<td>ZEND_INIT_USER_CALL</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_SEND_ARRAY</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_SEND_USER</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>STRLEN</td>
					<td>get length of string and store the result</td>
					<td>STRLEN $a<BR>strlen($a);</td>
				</tr><tr>
					<td>DEFINED</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_TYPE_CHECK</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_VERIFY_RETURN_TYPE</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FE_RESET_RW</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FE_FETCH_RW</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FE_FREE</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_INIT_DYNAMIC_CALL</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_DO_ICALL</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_DO_UCALL</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_DO_FCALL_BY_NAME</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>PRE_INC_OBJ</td>
					<td>Same as PRE_INC but operate to an object</td>
					<td>PRE_INC_OBJ $obj "a"<br>
						++$obj->a;</td>
				</tr><tr>
					<td>PRE_DEC_OBJ</td>
					<td>Same as PRE_DEC but operate to an object</td>
					<td>PRE_DEC_OBJ $obj "a"<br>--$obj->a;</td>
				</tr><tr>
					<td>POST_INC_OBJ</td>
					<td>Same as POST_INC but operate to an object</td>
					<td>POST_INC_OBJ $obj "a" ~0<br>
						$obj->a++;</td>
				</tr><tr>
					<td>POST_DEC_OBJ</td>
					<td>Same as POST_DEC but operate to an object</td>
					<td>POST_DEC_OBJ $obj "a" ~0<br>
						$obj->a--;</td>
				</tr><tr>
					<td>ASSIGN_OBJ</td>
					<td>fetch an object and wait for OP_DATA opcode.</td>
					<td>ASSIGN_OBJ $obj "a"<br>
						OP_DATA $t<br><br>
						$obj->a=$t;</td>
				</tr><tr>
					<td>INSTANCEOF</td>
					<td></td>
					<td>INSTANCEOF $a "A" ~0<br>
					$a instanceof A;</td>
				</tr><tr>
					<td>DECLARE_CLASS</td>
					<td>declare a class by name</td>
					<td>JMPZ true JX<br>
						DECLARE_CLASS "a" @0<br><br>
					if(true){class A{}}</td>
				</tr><tr>
					<td>DECLARE_INHERITED_CLASS</td>
					<td>when declare a class by name,if declared class extends other class,will execute this opcode.</td>
					<td>JMPZ true JX<br>
						DECLARE_INHERITED_CLASS "a" "C" @0<br><br>
						if(true){<br>
						class a extends C{}<br>}</td>
				</tr><tr>
					<td>DECLARE_FUNCTION</td>
					<td>declare function by name</td>
					<td>JMPZ true JX<br>
						DECLARE_FUNCTION "test"<br><br>
						if(true){<br>
						function test(){}<br>
					}</td>
				</tr><tr>
					<td>RAISE_ABSTRACT_ERROR</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>DECLARE_CONST</td>
					<td>declare a const value</td>
					<td>DECLARE_CONST "a" 1<BR>
					const a=1;</td>
				</tr><tr>
					<td>ADD_INTERFACE</td>
					<td>when declare class by name,if declared class implements other interface,will execute this opcode.</td>
					<td>JMPZ true JX<br>
						DECLARE_CLASS "a" @0<br>
						ADD_INTERFACE @0 "C"<br>
						VERIFY_ABSTRACT_CLASS @0<br><br>
						if(true){<br>
						class a implements C{}<br>}</td>
				</tr><tr>
					<td>DECLARE_INHERITED_CLASS_DELAYED</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>VERIFY_ABSTRACT_CLASS</td>
					<td></td>
					<td>Could see ADD_INTERFACE part.</td>
				</tr><tr>
					<td>ASSIGN_DIM</td>
					<td>set value of variable by index,followed by OP_DATA.</td>
					<td>ASSIGN_DIM $x 0<br>
						OP_DATA 2<br><br>
					$x[0]=2;</td>
				</tr><tr>
					<td>OP_DATA</td>
					<td>set value after "ASSIGN" opcodes(such as ASSIGN_DIM,ASSIGN_OBJ...) executed.</td>
					<td>Could see ASSIGN_DIM part.</td>
				</tr><tr>
					<td>ISSET_ISEMPTY_PROP_OBJ</td>
					<td>check wether a property value of an object is setted and store the result</td>
					<td>ISSET_ISEMPTY_PROP_OBJ $a "b" ~0<br>
						isset($a->b);</td>
				</tr><tr>
					<td>HANDLE_EXCEPTION</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>USER_OPCODE</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_ASSERT_CHECK</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>JMP_SET</td>
					<td>set the variable if value is not zero,otherwise jump to address</td>
					<td>JMP_SET $b JX ~0<br>
						QM_ASSIGN 2 ~0<br>
						ASSIGN $t ~0<br><br>
					$t=$b?:2;</td>
				</tr><tr>
					<td>ZEND_DECLARE_LAMBDA_FUNCTION</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ADD_TRAIT</td>
					<td>followed by BIND_TRAITS</td>
					<td>DECLARE_CLASS "a" @0<br>
						ADD_TRAIT @0 "B"<br>
						BIND_TRAITS @0<br><br>
						class A{<br>
						use B;<br>
					}</td>
				</tr><tr>
					<td>BIND_TRAITS</td>
					<td>bind trait in class.</td>
					<td>Could see ADD_TRAIT part.</td>
				</tr><tr>
					<td>ZEND_SEPARATE</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FETCH_CLASS_NAME</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_CALL_TRAMPOLINE</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_DISCARD_EXCEPTION</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_YIELD</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_GENERATOR_RETURN</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FAST_CALL</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FAST_RET</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_RECV_VARIADIC</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_SEND_UNPACK</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_POW</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_ASSIGN_POW</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_BIND_GLOBAL(vld)<br>BIND_GLOBAL</td>
					<td>declare an global variable</td>
					<td>BIND_GLOBAL $a "a"<br>
					global $a;</td>
				</tr><tr>
					<td>ZEND_COALESCE</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_SPACESHIP</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_DECLARE_ANON_CLASS</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_DECLARE_ANON_INHERITED_CLASS</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FETCH_STATIC_PROP_R</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FETCH_STATIC_PROP_W</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FETCH_STATIC_PROP_RW</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FETCH_STATIC_PROP_IS</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FETCH_STATIC_PROP_FUNC_ARG</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FETCH_STATIC_PROP_UNSET</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_UNSET_STATIC_PROP</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_ISSET_ISEMPTY_STATIC_PROP</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FETCH_CLASS_CONSTANT</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_BIND_LEXICAL</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_BIND_STATIC</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FETCH_THIS</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_SEND_FUNC_ARG</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_ISSET_ISEMPTY_THIS</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_SWITCH_LONG</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_SWITCH_STRING</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_IN_ARRAY</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_COUNT</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_GET_CLASS</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_GET_CALLED_CLASS</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_GET_TYPE</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FUNC_NUM_ARGS</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_FUNC_GET_ARGS</td>
					<td></td>
					<td></td>
				</tr><tr>
					<td>ZEND_UNSET_CV</td>
					<td></td>
					<td></td>
				</tr>
			</tbody>
		</table>
	</body>
</html>

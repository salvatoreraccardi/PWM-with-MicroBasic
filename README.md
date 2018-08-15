# PWM-with-mikroBasic
Manage eight LEDs via PWM
### Declarations Zone
```sh
  dim k,h,t_on,t_off as byte
```
### Main
```sh
main:
trisa=255
trisb=0
portb=0

while true
if (porta.0=1) and (porta.1=0) then
'LIGHT ON EQUAL LED (effect fade) and LIGHT OFF ODD LED (NO EFFECT)
  for t_on = 0 to 100
    t_off=100-t_on
    for h=0 to 6 step 2
    portb.h=1
    next h
    for k=0 to t_on
    delay_us(1)
    next k
    for h=0 to 6 step 2
    portb.h=0
    next h
    for k=0 to t_off
    delay_us(1)
    next k
  next t_on
    for h=0 to 6 step 2
    portb.h=1
    next h
    for h=1 to 7 step 2
    portb.h=0
    next h
end if
if (porta.0=0) and (porta.1=1) then
'LIGHT ON ODD LED (effect fade) and LIGHT OFF EQUAL LED (NO EFFECT)
for t_on = 0 to 100
  t_off=100-t_on
  for h=1 to 7 step 2
  portb.h=1
  next h
  for k=0 to t_on
  delay_us(1)
  next k
  for h=1 to 7 step 2
  portb.h=0
  next h
  for k=0 to t_off
  delay_us(1)
  next k
next t_on
  for h=1 to 7 step 2
  portb.h=1
  next h
  for h=0 to 6 step 2
  portb.h=0
  next h
end if
delay_ms(200)
wend
end.
```

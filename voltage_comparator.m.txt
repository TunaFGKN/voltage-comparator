

Vref = 3.3;         
Vcc = 12;           
Vee = -12;          

Vin = input('Enter Vin value (0 to 12V): ');

if Vin < Vref
    Vout = Vcc;   
    disp('>> Vin < Vref: Output = +12V → D5 (RED) LED is ON');
elseif Vin > Vref
    Vout = Vee;   
    disp('>> Vin > Vref: Output = -12V → D2 (BLUE) LED is ON');
else
    Vout = 0;     
    disp('>> Vin == Vref: Output = 0V → No LED is ON');
end

fprintf('Vin = %.2f V\n', Vin);
fprintf('Vref = %.2f V\n', Vref);
fprintf('Vout = %.2f V\n', Vout);



%%
Vref = 3.3;         
Vcc = 12;           
Vee = -12;          

Vin = 0:0.01:12;    
Vout = zeros(size(Vin));  

for i = 1:length(Vin)
    if Vin(i) < Vref
        Vout(i) = Vcc;  
    elseif Vin(i) > Vref
        Vout(i) = Vee;  
    else
        Vout(i) = 0;    
    end
end

figure;
plot(Vin, Vout, 'LineWidth', 2);
grid minor;
xlabel('Vin (V)');
ylabel('Vout (V)');
title('Voltage Comparator Output (LM741)');
ylim([-15 15]);
xline(Vref, '--r', 'Vref = 3.3V');  % Eşik çizgisi
legend('Vout', 'Reference Voltage (Vref)', 'Location', 'northeast');
%%
Vref = 3.3;         
Vcc = 12;           
Vee = -12;          

t = 0:0.001:2;                         
Vin = 6 + 3*sin(2*pi*1*t);             

Vout = zeros(size(Vin));
for i = 1:length(Vin)
    if Vin(i) < Vref
        Vout(i) = Vcc;   
    elseif Vin(i) > Vref
        Vout(i) = Vee;    
    else
        Vout(i) = 0;
    end
end

figure;

subplot(2,1,1);
plot(t, Vin, 'b', 'LineWidth', 1.5);
yline(Vref, '--r', 'Vref = 3.3V');
title('Vin (Input Signal)');
xlabel('Time (s)');
ylabel('Vin (V)');
grid minor;

subplot(2,1,2);
plot(t, Vout, 'm', 'LineWidth', 2);
ylim([-15 15]);
title('Vout (Comparator Output)');
xlabel('Time (s)');
ylabel('Vout (V)');
grid minor;
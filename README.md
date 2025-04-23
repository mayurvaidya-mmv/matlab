

INPUT 

% Input Parameters
kerb_weight_kg = 1500; 
payload_kg = 200; 
drag_coefficient = 0.3; 
rolling_resistance_coefficient = 0.015; 
tyre_radius_m = 0.33; 
target_speed_kmph = 72; 
incline_angle_deg = 5;
frontal_area_m2 = 2.5; 
air_density_kg_m3 = 1.225; 
 
% Conversions and Constants
target_speed_mps = target_speed_kmph / 3.6; 
total_weight_N = (kerb_weight_kg + payload_kg) * 9.81; 
 
% Force Calculations
rolling_resistance = rolling_resistance_coefficient * total_weight_N; 

air_drag_force = 0.5 * drag_coefficient * air_density_kg_m3 * frontal_area_m2 * target_speed_mps^2; 

incline_angle_rad = deg2rad(incline_angle_deg); 

hill_climbing_force = total_weight_N * sin(incline_angle_rad); 
 
% Total Tractive Force
total_tractive_force = rolling_resistance + air_drag_force + hill_climbing_force;
 
% Motor Power Calculations
motor_power_watts = total_tractive_force * target_speed_mps; 

peak_power_watts = motor_power_watts * 1.2; 

% Display Results
fprintf('--- Electric Vehicle Motor Sizing ---\n');
fprintf('Rolling Resistance Force: %.2f N\n', rolling_resistance);
fprintf('Air Drag Force: %.2f N\n', air_drag_force);
fprintf('Hill Climbing Force: %.2f N\n', hill_climbing_force);
fprintf('Total Tractive Force: %.2f N\n', total_tractive_force);
fprintf('Motor Power Required: %.2f Watts\n', motor_power_watts);
fprintf('Peak Motor Power: %.2f Watts\n', peak_power_watts);
fprintf('-------------------------------------\n');




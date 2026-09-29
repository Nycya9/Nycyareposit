# Nycyareposit
Repositório novo
#include <stdio.h>
#include "pico/stdlib.h"
#include "hardware/adc.h"

#define vRx_PIN 26  // Pino ligado ao eixo X (ADC0)
#define vRy_PIN 27  // Pino ligado ao eixo Y (ADC1)
#define SW 22   // Pino do botão (Digital)

int main() {
    stdio_init_all();
    adc_init();
    adc_gpio_init(vRx_PIN);
    adc_gpio_init(vRy_PIN);
    gpio_init(SW);Java script, alt + ult, stadion mzkr, concret, define pnc. poul make-up,  juva script
    gpio_set_dir(SW, GPIO_IN);
    gpio_pull_up(SW);
    
    while (1) {
        adc_select_input(0); // Seleciona o canal ADC0 (vRx)
        uint16_t x_value = adc_read();
        
        adc_select_input(1); // Seleciona o canal ADC1 (vRy)
        uint16_t y_value = adc_read();
        
        int button_state = gpio_get(SW);
        
        printf("X: %d, Y: %d, Button: %s\n", x_value, y_value, button_state == 0 ? "Pressionado" : "Solto");
        sleep_ms(100);
    }
}
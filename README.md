ackage com.mycompanysena.banco_ejemplo;

import java.util.Random;
import javax.swing.JOptionPane;

public class cajero {

    private int saldo = 700000, saldoC = 20000000, retiroD = 2100000;
    private boolean continuar = true;

    public cajero() {
    }

    public int getSaldo() {
        return saldo;
    }

    public void setSaldo(int saldo) {
        this.saldo = saldo;
    }

    public int getSaldoC() {
        return saldoC;
    }

    public void setSaldoC(int saldoC) {
        this.saldoC = saldoC;
    }

    public int getRetiroD() {
        return retiroD;
    }

    public void setRetiroD(int retiroD) {
        this.retiroD = retiroD;
    }

    public void Cajeroautomatico() {
        while (continuar) {
            try {
                StringBuilder menu = new StringBuilder("MENU CAJERO AUTOMATICO \n\n");
                menu.append("selecione una opcion del 1 al 4: \n")
                        .append("1. consultar saldo \n")
                        .append("2. consignar dinero \n ")
                        .append("3. retirar dinero \n")
                        .append("4. salir ");
                String opcion = JOptionPane.showInputDialog(null, menu,
                        "cajero automatico", JOptionPane.QUESTION_MESSAGE);

                if (opcion == null) {
                    if (Confirmarsalida()) {
                        continuar = false;
                    }
                    continue;
                }
                int opc = Integer.parseInt(opcion);
                switch (opc) {
                    case 1:
                        cosultarsaldo();
                        break;
                    case 2:
                        consiGnardinero();
                        break;
                    case 3:

                        break;
                    case 4:
                        break;
                    default:
                        throw new AssertionError();
                }
            } catch (Exception e) {
            }

        }
    }

    public boolean Confirmarsalida() {
        int confirmar = JOptionPane.showConfirmDialog(null, "¿estas seguro que deseas salir?", "confirmar salida",
                JOptionPane.YES_NO_OPTION);
        return confirmar == JOptionPane.YES_OPTION;
    }

    public String idValidacion() {
        Random random = new Random();
        int numero = random.nextInt(9000) + 1000;
        return "ID #" + numero;
    }

    public void cosultarsaldo() {
        String validacion = idValidacion();
        StringBuilder mensaje = new StringBuilder("consultar saldo");
        mensaje.append(validacion).append("\n\n")
                .append("saldo actual: $")
                .append(String.format("%,d",saldo));
        JOptionPane.showMessageDialog(null, mensaje,
                "consultar saldo",JOptionPane.INFORMATION_MESSAGE);
    }

    public void consiGnardinero() {
        try{
            
        
        StringBuilder consi = new StringBuilder();
        consi.append("cosignar dinero");
        String sig = JOptionPane.showInputDialog(null, consi, "cosignar saldo", JOptionPane.DEFAULT_OPTION);
        int consig = Integer.parseInt(sig);
        if (consig < 10000) {
            JOptionPane.showInternalConfirmDialog(null, "error nose puden consignar menos de 10000", "error", JOptionPane.WARNING_MESSAGE);
            return;
           
        }
        saldo = consig + saldo;
        }catch(Exception e){
            JOptionPane.showInternalMessageDialog(null,"solo pude ingresar valores numericos ","VALOR INVALIDO",JOptionPane.WARNING_MESSAGE);
        }
        
        
    }   
}

import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

public class CalculadoraTest {

    private Calculadora calc;

    @BeforeEach
    public void setUp() {
        calc = new Calculadora();
    }

    @Test
    public void testSomar() {
        assertEquals(5.0, calc.somar(2.0, 3.0), "Soma de positivos falhou");
        assertEquals(-5.0, calc.somar(-2.0, -3.0), "Soma de negativos falhou");
        assertEquals(2.0, calc.somar(2.0, 0.0), "Soma com zero falhou");
    }

    @Test
    public void testSubtrair() {
        assertEquals(1.0, calc.subtrair(3.0, 2.0), "Subtração de positivos falhou");
        assertEquals(1.0, calc.subtrair(-2.0, -3.0), "Subtração de negativos falhou");
        assertEquals(2.0, calc.subtrair(2.0, 0.0), "Subtração com zero falhou");
    }

    @Test
    public void testMultiplicar() {
        assertEquals(6.0, calc.multiplicar(2.0, 3.0), "Multiplicação de positivos falhou");
        assertEquals(6.0, calc.multiplicar(-2.0, -3.0), "Multiplicação de negativos falhou");
        assertEquals(0.0, calc.multiplicar(5.0, 0.0), "Multiplicação por zero falhou");
    }

    @Test
    public void testDividirSucesso() {
        assertEquals(2.0, calc.dividir(6.0, 3.0), "Divisão de positivos falhou");
        assertEquals(2.0, calc.dividir(-6.0, -3.0), "Divisão de negativos falhou");
    }

    @Test
    public void testDividirPorZero() {
        Exception exception = assertThrows(ArithmeticException.class, () -> {
            calc.dividir(5.0, 0.0);
        }, "Deveria lançar ArithmeticException ao dividir por zero");

        assertEquals("Divisão por zero não é permitida.", exception.getMessage());
    }
}


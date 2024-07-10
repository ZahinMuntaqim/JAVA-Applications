import javax.swing.*;
import java.awt.*;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class SystemInfoDisplay extends JFrame {

    private JLabel cpuLabel;
    private JLabel gpuLabel;
    private JLabel resolutionLabel;

    public SystemInfoDisplay() {
        super("System Information");

        // Initialize components
        cpuLabel = new JLabel("CPU: " + getCPUInfo());
        gpuLabel = new JLabel("GPU: " + getGPUInfo());
        resolutionLabel = new JLabel("Resolution: " + getScreenResolution());

        // Set layout
        setLayout(new GridLayout(3, 1));

        // Add components to the frame
        add(cpuLabel);
        add(gpuLabel);
        add(resolutionLabel);

        // Set frame properties
        setSize(400, 300); // Set frame size
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // Exit when close button is clicked
        setLocationRelativeTo(null); // Center the frame on the screen
        setVisible(true); // Make the frame visible
    }

    private String getCPUInfo() {
        // Example method to get CPU information using system commands (Windows specific)
        String command = "wmic cpu get name";
        return executeSystemCommand(command);
    }

    private String getGPUInfo() {
        // Example method to get GPU information using system commands (Windows specific)
        String command = "wmic path win32_videocontroller get caption";
        return executeSystemCommand(command);
    }

    private String getScreenResolution() {
        // Example method to get screen resolution using Java's AWT Toolkit
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        return screenSize.width + "x" + screenSize.height;
    }

    private String executeSystemCommand(String command) {
        StringBuilder output = new StringBuilder();
        Process process;
        try {
            process = Runtime.getRuntime().exec(command);
            process.waitFor();
            BufferedReader reader = new BufferedReader(new InputStreamReader(process.getInputStream()));
            String line;
            while ((line = reader.readLine()) != null) {
                output.append(line).append("\n");
            }
        } catch (IOException | InterruptedException e) {
            e.printStackTrace();
        }
        return output.toString().trim();
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> new SystemInfoDisplay());
    }
}

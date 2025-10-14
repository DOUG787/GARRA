package com.example.afinal;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.LinearLayout;
import android.widget.TextView;

import androidx.appcompat.app.AlertDialog;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    Button btnNovoProduto, btnTroca, btnIniciar;
    TextView txtNomeUsuario;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btnNovoProduto = findViewById(R.id.btnNovoProduto);
        btnTroca = findViewById(R.id.btnTroca);
        btnIniciar = findViewById(R.id.btnIniciar);
        txtNomeUsuario = findViewById(R.id.txtNomeUsuario);

        // --- BOTÃO INICIAR ---
        btnIniciar.setOnClickListener(v -> showWelcomeDialog());

        // --- BOTÃO TROCA ---
        btnTroca.setOnClickListener(v -> showProdutoDialog("Troca de Produto"));

        // --- BOTÃO DEVOLUÇÃO ---
        btnNovoProduto.setOnClickListener(v -> showProdutoDialog("Devolução de Produto"));
    }

    // =========================
    // DIALOG BOAS-VINDAS
    // =========================
    private void showWelcomeDialog() {
        LinearLayout layout = new LinearLayout(this);
        layout.setOrientation(LinearLayout.VERTICAL);
        layout.setPadding(40, 20, 40, 20);

        EditText editTextNome = new EditText(this);
        editTextNome.setHint("Digite seu nome");
        layout.addView(editTextNome);

        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Seja Muito Bem-vindo(a) ao GARRA");
        builder.setMessage("Digite seu nome para continuar:");
        builder.setView(layout);

        builder.setNegativeButton("Prefiro não dizer", (dialog, which) -> {
            txtNomeUsuario.setText("Bem-vindo!!!");
            Intent intent = new Intent(MainActivity.this, NovoAtendimentoActivity.class);
            intent.putExtra("nomeUsuario", "Usuário");
            startActivity(intent);
        });

        builder.setPositiveButton("Confirmar", (dialog, which) -> {
            String nome = editTextNome.getText().toString().trim();
            if (!nome.isEmpty()) {
                txtNomeUsuario.setText("Olá, " + nome + "!");
                Intent intent = new Intent(MainActivity.this, NovoAtendimentoActivity.class);
                intent.putExtra("nomeUsuario", nome);
                startActivity(intent);
            } else {
                editTextNome.setError("Digite seu nome ou clique em 'Prefiro não dizer'");
            }
        });

        AlertDialog dialog = builder.create();
        dialog.show();
    }



    // =========================
    // DIALOG PARA TROCA / DEVOLUÇÃO
    // =========================
    private void showProdutoDialog(String titulo) {
        LinearLayout layout = new LinearLayout(this);
        layout.setOrientation(LinearLayout.VERTICAL);
        layout.setPadding(40, 20, 40, 20);

        EditText editTextNome = new EditText(this);
        editTextNome.setHint("Digite seu nome");
        layout.addView(editTextNome);

        EditText editTextProduto = new EditText(this);
        editTextProduto.setHint("Digite o produto");
        layout.addView(editTextProduto);

        EditText editTextModelo = new EditText(this);
        editTextModelo.setHint("Digite o modelo");
        layout.addView(editTextModelo);

        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle(titulo);
        builder.setMessage("Preencha os campos abaixo:");
        builder.setView(layout);

        builder.setNegativeButton("Cancelar", (dialog, which) -> dialog.dismiss());

        builder.setPositiveButton("Confirmar", (dialog, which) -> {
            String nome = editTextNome.getText().toString().trim();
            String produto = editTextProduto.getText().toString().trim();
            String modelo = editTextModelo.getText().toString().trim();

            if (nome.isEmpty() || produto.isEmpty() || modelo.isEmpty()) {
                AlertDialog.Builder errorDialog = new AlertDialog.Builder(this);
                errorDialog.setMessage("Por favor, preencha todos os campos!");
                errorDialog.setPositiveButton("OK", null);
                errorDialog.show();
            } else {
                Intent intent = new Intent(MainActivity.this, ResumoActivity.class);
                intent.putExtra("nomeUsuario", nome);
                intent.putExtra("produto", produto);
                intent.putExtra("modelo", modelo);
                intent.putExtra("tamanho", "N/A");
                intent.putExtra("presente", "N/A");
                intent.putExtra("pagamento", "N/A");
                startActivity(intent);
            }


        });



        AlertDialog dialog = builder.create();
        dialog.show();
    }
}

# Thandi-s-Farm-House

package vcmsa.ci.thandisfarmhouse

import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)


        val edtEggs= findViewById<EditText>(R.id.edtEggs)
        val txtResult = findViewById<TextView>(R.id.txtResult)
        val btnCompute1 = findViewById<Button>(R.id.btnCompute1)
        val btnClear = findViewById<Button>(R.id.btnClear)


        btnCompute1.setOnClickListener {



         val edtEggs = edtEggs.text.toString().toIntOrNull() ?: 0
         val dozenCount = edtEggs /12
         val looseEggs = edtEggs%12
         val dozenPrice = 16.0
         val looseEggsPrice = 1.50
         val totalCost = (dozenCount*dozenPrice)+(looseEggs*looseEggsPrice)


          txtResult.text="You ordered $edtEggs eggs. /n" +
                          "that's $dozenCount dozen(s) at R16 per doze/n"+
                           "and $looseEggs loose egg(s) at R1.50 each /n" +
                            "Total cost:R $totalCost"



        }














        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.edtEggs)) { v, insets ->
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)
            insets
        }
    }

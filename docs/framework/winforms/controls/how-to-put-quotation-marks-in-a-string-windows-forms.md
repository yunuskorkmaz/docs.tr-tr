---
title: 'Nasıl yapılır: (Windows Forms) dizeye tırnak işaretleri koyma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: a8822c9a26db445080668b1b493803369ccbae4d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714820"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Nasıl yapılır: (Windows Forms) dizeye tırnak işaretleri koyma
Bazen tırnak işareti yerleştirmek isteyebilirsiniz ("") içinde bir metin dizesi. Örneğin:  
  
 O söyledi, "Müthiş hak ediyor!"  
  
 Alternatif olarak, ayrıca kullanabileceğiniz <xref:Microsoft.VisualBasic.ControlChars.Quote> alan bir sabit olarak.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Kodunuzda bir dizedeki tırnak işareti yerleştirmek için  
  
1.  Visual Basic'te, iki tırnak bir satır içine katıştırılmış bir tırnak işareti ekleyin. Görselde C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], kaçış dizisi Ekle \\"olarak gömülü bir tırnak işareti. Örneğin, önceki dize oluşturmak için aşağıdaki kodu kullanın.  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     -veya-  
  
2.  Tırnak işareti için ASCII veya Unicode karakteri Ekle. Visual Basic'te, ASCII karakter (34) kullanın. Görselde C#, Unicode karakter (\u0022) kullanın.  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  Bu örnekte, bir evrensel karakter adı temel karakter kümesindeki bir karakteri belirler kullanamadığından \u0022 kullanamazsınız. Aksi takdirde, C3851 üretir. Daha fazla bilgi için [derleyici hatası C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
     -veya-  
  
3.  Ayrıca, bir sabit karakter tanımlamak ve kullanmak gerektiğinde.  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt okunur metin kutusu oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde birden çok satır görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)

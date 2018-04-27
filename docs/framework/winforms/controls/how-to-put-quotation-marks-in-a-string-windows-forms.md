---
title: Nasıl yapılır Dizeye Tırnak İşaretleri Koyma (Windows Forms)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd7c6a460f24b1406ad914e20b9113920814737c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Nasıl yapılır Dizeye Tırnak İşaretleri Koyma (Windows Forms)
Bazen tırnak işaretleri yerleştirmeyi isteyebilirsiniz ("") bir metin dizesi içinde. Örneğin:  
  
 O söyledi, "Müthiş hak!"  
  
 Alternatif olarak, ayrıca kullanabileceğiniz <xref:Microsoft.VisualBasic.ControlChars.Quote> bir sabit olarak alan.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Kodunuzu içindeki bir dizeye tırnak işaretleri yerleştirmek için  
  
1.  Visual Basic'te bir satır iki tırnak işaretleri katıştırılmış bir tırnak işareti ekleyin. Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], kaçış sırası Ekle \\"olarak katıştırılmış bir tırnak işareti. Örneğin, önceki dizesi oluşturmak için aşağıdaki kodu kullanın.  
  
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
  
2.  Tırnak işareti ASCII veya Unicode karakteri ekler. Visual Basic'te ASCII karakter (34) kullanın. Visual C# projesinde, Unicode karakter (\u0022) kullanın.  
  
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
    >  Bu örnekte, temel karakter kümesinde bir karakter atayan evrensel karakter adları kullanamadığından \u0022 kullanamazsınız. Aksi takdirde C3851 üretir. Daha fazla bilgi için bkz: [derleyici hatası C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [TextBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox Denetimi](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)

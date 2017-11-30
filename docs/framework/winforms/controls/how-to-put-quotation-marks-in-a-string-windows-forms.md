---
title: "Nasıl yapılır Dizeye Tırnak İşaretleri Koyma (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a4141a27a3b195dbb747a827d2bd9426a948f83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Nasıl yapılır Dizeye Tırnak İşaretleri Koyma (Windows Forms)
Bazen tırnak işaretleri yerleştirmeyi isteyebilirsiniz ("") bir metin dizesi içinde. Örneğin:  
  
 O söyledi, "Müthiş hak!"  
  
 Alternatif olarak, ayrıca kullanabileceğiniz <xref:Microsoft.VisualBasic.ControlChars.Quote> bir sabit olarak alan.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Kodunuzu içindeki bir dizeye tırnak işaretleri yerleştirmek için  
  
1.  İçinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], iki tırnak işareti katıştırılmış bir tırnak işareti olarak bir satır ekleyin. İçinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], kaçış sırası Ekle \\"olarak katıştırılmış bir tırnak işareti. Örneğin, önceki dizesi oluşturmak için aşağıdaki kodu kullanın.  
  
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
  
     veya  
  
2.  Tırnak işareti ASCII veya Unicode karakteri ekler. İçinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], ASCII karakter (34) kullanın. İçinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], Unicode karakter (\u0022) kullanın.  
  
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
  
     veya  
  
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
 [TextBox denetimine genel bakış](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını denetleme](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: salt okunur metin kutusu oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Nasıl yapılır: metni seçme Windows Forms TextBox denetiminde](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: birden çok satır Windows Forms TextBox denetiminde görünümü](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox denetimi](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)

---
title: 'Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error icons
- ErrorProvider component [Windows Forms], displaying error icons
- error messages [Windows Forms], displaying icons
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
ms.openlocfilehash: 237a61cc21a18805fa502c9870d8ea472ac54d71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527306"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme
Windows Forms kullanabilirsiniz <xref:System.Windows.Forms.ErrorProvider> kullanıcı geçersiz veri girdiğinde bir hata simgesi görüntülemek için bileşen. Aralarında sekmesinde ve böylece doğrulama kodu çağırmak için form üzerinde en az iki denetimleri olması gerekir.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Bir denetimin değeri geçersiz bir hata simgesi görüntülemek için  
  
1.  İki denetimleri ekleme — Örneğin, metin kutuları — Windows formu.  
  
2.  Ekleme bir <xref:System.Windows.Forms.ErrorProvider> forma bileşen.  
  
3.  İlk denetimi seçin ve kodu ekleyin, <xref:System.Windows.Forms.Control.Validating> olay işleyicisi. Düzgün çalışması bu kodun çalışması, yordam olaya bağlı olmanız gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: olay işleyicileri oluşturma çalıştırma süresi için Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Aşağıdaki kod, kullanıcının girdiği verileri geçerlilik testleri; Veri geçersizse <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemi çağrılır. İlk bağımsız değişkeni <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemini belirtir, yanındaki simge görüntülemek için denetim. İkinci bağımsız değişkeni, görüntülenecek hata metindir.  
  
    ```vb  
    Private Sub TextBox1_Validating(ByVal Sender As Object, _  
       ByVal e As System.ComponentModel.CancelEventArgs) Handles _  
       TextBox1.Validating  
          If Not IsNumeric(TextBox1.Text) Then  
             ErrorProvider1.SetError(TextBox1, "Not a numeric value.")  
          Else  
             ' Clear the error.  
             ErrorProvider1.SetError(TextBox1, "")  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void textBox1_Validating (object sender,  
       System.ComponentModel.CancelEventArgs e)  
    {  
       try  
       {  
          int x = Int32.Parse(textBox1.Text);  
          errorProvider1.SetError(textBox1, "");  
       }  
       catch (Exception ex)  
       {  
          errorProvider1.SetError(textBox1, "Not an integer value.");  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void textBox1_Validating(System::Object ^  sender,  
          System::ComponentModel::CancelEventArgs ^  e)  
       {  
          try  
          {  
             int x = Int32::Parse(textBox1->Text);  
             errorProvider1->SetError(textBox1, "");  
          }  
          catch (System::Exception ^ ex)  
          {  
             errorProvider1->SetError(textBox1, "Not an integer value.");  
          }  
       }  
    ```  
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  Projeyi çalıştırın. İlk denetim ve ardından sekme ikinci (Bu örnekte, sayısal olmayan) geçersiz veri türü. Hata simgesi görüntülendiğinde, hem hata metni görmek için fare işaretçisini gelin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>  
 [ErrorProvider Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)

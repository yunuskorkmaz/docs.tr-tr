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
ms.openlocfilehash: 2af8d3b9ea97b678c493de8a58d439b62f448387
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053705"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme
Bir Windows Forms kullanabileceğiniz <xref:System.Windows.Forms.ErrorProvider> kullanıcı geçersiz veri girdiğinde bir hata simgesi görüntülenecek bileşeni. Bunlar arasında sekme ve böylece bir doğrulama kodu çağırmak için form üzerinde en az iki denetimleri olması gerekir.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Bir denetimin değeri geçersiz bir hata simgesi görüntülemek için  
  
1. İki denetimler ekleme — Örneğin, metin kutuları: bir Windows Form.  
  
2. Ekleme bir <xref:System.Windows.Forms.ErrorProvider> forma bileşen.  
  
3. Birinci denetimi seçin ve kod ekleyin, <xref:System.Windows.Forms.Control.Validating> olay işleyicisi. Düzgün çalışması için bu kodu için sırada yordamı olaya bağlı olması gerekir. Daha fazla bilgi için [nasıl yapılır: Windows Forms için çalışma zamanında olay işleyicileri oluşturma](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Aşağıdaki kod, kullanıcının girdiği verileri geçerliliğini sınar; Veri geçersizse <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemi çağrılır. İlk bağımsız değişkeni <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemi yanındaki simge görüntülenecek denetleyen belirtir. İkinci bağımsız değişkeni, görüntülenecek hata metindir.  
  
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
  
     (Visual C#, Visual C++) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. Projeyi çalıştırın. İlk denetim ve ardından ikinci için sekmesinde (Bu örnekte, sayısal olmayan) geçersiz veri türü. Hata simgesi görüntülendiğinde, hem hata metnini görmek için fare işaretçisi ile işaretleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [ErrorProvider Bileşenine Genel Bakış](errorprovider-component-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ErrorProvider bileşeni ile DataSet içindeki hataları görüntüleme](view-errors-within-a-dataset-with-wf-errorprovider-component.md)

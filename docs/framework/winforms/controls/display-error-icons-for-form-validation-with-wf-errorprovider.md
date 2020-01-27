---
title: ErrorProvider bileşeniyle form doğrulaması için hata simgelerini görüntüle
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
ms.openlocfilehash: a1e346e332db489351f59c9a0c03ae731baf3dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745915"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme
Kullanıcı geçersiz veri girdiğinde bir hata simgesi göstermek için Windows Forms <xref:System.Windows.Forms.ErrorProvider> bileşenini kullanabilirsiniz. Aralarında sekme almak ve bu nedenle doğrulama kodunu çağırmak için formda en az iki denetim olması gerekir.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Bir denetimin değeri geçersiz olduğunda bir hata simgesi göstermek için  
  
1. Bir Windows formuna iki denetim (örneğin, metin kutuları) ekleyin.  
  
2. Forma bir <xref:System.Windows.Forms.ErrorProvider> bileşeni ekleyin.  
  
3. İlk denetimi seçin ve <xref:System.Windows.Forms.Control.Validating> olay işleyicisine kod ekleyin. Bu kodun düzgün çalışması için, yordamın olaya bağlı olması gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: çalışma zamanında olay Işleyicileri oluşturma Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Aşağıdaki kod, kullanıcının girdiği verilerin geçerliliğini sınar; veriler geçersizse <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemi çağrılır. <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yönteminin ilk bağımsız değişkeni, öğesinin yanında simgenin görüntüleneceği denetimi belirtir. İkinci bağımsız değişken, görüntülenecek hata metni.  
  
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
  
     (Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. Projeyi çalıştırın. İlk denetime geçersiz (Bu örnekte sayısal olmayan) veriler yazın ve ardından ikinci sekmeye sürükleyin. Hata simgesi görüntülendiğinde, hata metnini görmek için fare işaretçisiyle üzerine gelin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [ErrorProvider Bileşenine Genel Bakış](errorprovider-component-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme](view-errors-within-a-dataset-with-wf-errorprovider-component.md)

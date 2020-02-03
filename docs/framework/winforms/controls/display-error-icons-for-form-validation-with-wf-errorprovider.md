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
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="95b24-102">Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="95b24-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="95b24-103">Kullanıcı geçersiz veri girdiğinde bir hata simgesi göstermek için Windows Forms <xref:System.Windows.Forms.ErrorProvider> bileşenini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95b24-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="95b24-104">Aralarında sekme almak ve bu nedenle doğrulama kodunu çağırmak için formda en az iki denetim olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95b24-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="95b24-105">Bir denetimin değeri geçersiz olduğunda bir hata simgesi göstermek için</span><span class="sxs-lookup"><span data-stu-id="95b24-105">To display an error icon when a control's value is invalid</span></span>  
  
1. <span data-ttu-id="95b24-106">Bir Windows formuna iki denetim (örneğin, metin kutuları) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95b24-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2. <span data-ttu-id="95b24-107">Forma bir <xref:System.Windows.Forms.ErrorProvider> bileşeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95b24-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3. <span data-ttu-id="95b24-108">İlk denetimi seçin ve <xref:System.Windows.Forms.Control.Validating> olay işleyicisine kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95b24-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="95b24-109">Bu kodun düzgün çalışması için, yordamın olaya bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95b24-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="95b24-110">Daha fazla bilgi için bkz. [nasıl yapılır: çalışma zamanında olay Işleyicileri oluşturma Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="95b24-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="95b24-111">Aşağıdaki kod, kullanıcının girdiği verilerin geçerliliğini sınar; veriler geçersizse <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="95b24-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="95b24-112"><xref:System.Windows.Forms.ErrorProvider.SetError%2A> yönteminin ilk bağımsız değişkeni, öğesinin yanında simgenin görüntüleneceği denetimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="95b24-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="95b24-113">İkinci bağımsız değişken, görüntülenecek hata metni.</span><span class="sxs-lookup"><span data-stu-id="95b24-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="95b24-114">(Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="95b24-114">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. <span data-ttu-id="95b24-115">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="95b24-115">Run the project.</span></span> <span data-ttu-id="95b24-116">İlk denetime geçersiz (Bu örnekte sayısal olmayan) veriler yazın ve ardından ikinci sekmeye sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="95b24-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="95b24-117">Hata simgesi görüntülendiğinde, hata metnini görmek için fare işaretçisiyle üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="95b24-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b24-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95b24-118">See also</span></span>

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [<span data-ttu-id="95b24-119">ErrorProvider Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="95b24-119">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="95b24-120">Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="95b24-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](view-errors-within-a-dataset-with-wf-errorprovider-component.md)

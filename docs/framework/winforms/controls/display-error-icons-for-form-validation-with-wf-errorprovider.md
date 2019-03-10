---
title: 'Nasıl yapılır: Windows Forms ErrorProvider bileşeni ile Form doğrulama için hata simgeleri görüntüleme'
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
ms.openlocfilehash: f676454849c37da8c0a5f944be05c3f6c95887b4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707644"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="608e3-102">Nasıl yapılır: Windows Forms ErrorProvider bileşeni ile Form doğrulama için hata simgeleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="608e3-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="608e3-103">Bir Windows Forms kullanabileceğiniz <xref:System.Windows.Forms.ErrorProvider> kullanıcı geçersiz veri girdiğinde bir hata simgesi görüntülenecek bileşeni.</span><span class="sxs-lookup"><span data-stu-id="608e3-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="608e3-104">Bunlar arasında sekme ve böylece bir doğrulama kodu çağırmak için form üzerinde en az iki denetimleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="608e3-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="608e3-105">Bir denetimin değeri geçersiz bir hata simgesi görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="608e3-105">To display an error icon when a control's value is invalid</span></span>  
  
1.  <span data-ttu-id="608e3-106">İki denetimler ekleme — Örneğin, metin kutuları: bir Windows Form.</span><span class="sxs-lookup"><span data-stu-id="608e3-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2.  <span data-ttu-id="608e3-107">Ekleme bir <xref:System.Windows.Forms.ErrorProvider> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="608e3-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3.  <span data-ttu-id="608e3-108">Birinci denetimi seçin ve kod ekleyin, <xref:System.Windows.Forms.Control.Validating> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="608e3-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="608e3-109">Düzgün çalışması için bu kodu için sırada yordamı olaya bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="608e3-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="608e3-110">Daha fazla bilgi için [nasıl yapılır: Windows Forms için çalışma zamanında olay işleyicileri oluşturma](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="608e3-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="608e3-111">Aşağıdaki kod, kullanıcının girdiği verileri geçerliliğini sınar; Veri geçersizse <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="608e3-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="608e3-112">İlk bağımsız değişkeni <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemi yanındaki simge görüntülenecek denetleyen belirtir.</span><span class="sxs-lookup"><span data-stu-id="608e3-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="608e3-113">İkinci bağımsız değişkeni, görüntülenecek hata metindir.</span><span class="sxs-lookup"><span data-stu-id="608e3-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="608e3-114">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="608e3-114">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  <span data-ttu-id="608e3-115">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="608e3-115">Run the project.</span></span> <span data-ttu-id="608e3-116">İlk denetim ve ardından ikinci için sekmesinde (Bu örnekte, sayısal olmayan) geçersiz veri türü.</span><span class="sxs-lookup"><span data-stu-id="608e3-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="608e3-117">Hata simgesi görüntülendiğinde, hem hata metnini görmek için fare işaretçisi ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="608e3-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608e3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="608e3-118">See also</span></span>
- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [<span data-ttu-id="608e3-119">ErrorProvider Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="608e3-119">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="608e3-120">Nasıl yapılır: Windows Forms ErrorProvider bileşeni ile DataSet içindeki hataları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="608e3-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](view-errors-within-a-dataset-with-wf-errorprovider-component.md)

---
title: 'Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: b6fe0e615cc5bbd0f549505ed9e6add8d7a51433
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523996"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="c4864-102">Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4864-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>
<span data-ttu-id="c4864-103">Bir kullanıcı bir dize türleri, yer tutucu karakterleri görüntüler bir Windows Forms metin kutusuna bir parola kutusudur.</span><span class="sxs-lookup"><span data-stu-id="c4864-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>  
  
### <a name="to-create-a-password-text-box"></a><span data-ttu-id="c4864-104">Parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4864-104">To create a password text box</span></span>  
  
1.  <span data-ttu-id="c4864-105">Ayarlama <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özelliği <xref:System.Windows.Forms.TextBox> belirli bir karakterin denetime.</span><span class="sxs-lookup"><span data-stu-id="c4864-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>  
  
     <span data-ttu-id="c4864-106"><xref:System.Windows.Forms.TextBox.PasswordChar%2A> Özellik metin kutusunda görüntülenen karakter belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4864-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="c4864-107">Örneğin, yıldız işareti (parola) kutusunda görüntülenen istiyorsanız belirtin \* için <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Özellikler penceresindeki özellik.</span><span class="sxs-lookup"><span data-stu-id="c4864-107">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="c4864-108">Ardından, metin kutusuna bir kullanıcı türleri, hangi karakter bağımsız olarak bir yıldız işareti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4864-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>  
  
2.  <span data-ttu-id="c4864-109">(İsteğe bağlı) Ayarlama <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c4864-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="c4864-110">Özellik karakterlerinin kaçının tutulacağını metin kutusuna yazılabilir belirler.</span><span class="sxs-lookup"><span data-stu-id="c4864-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="c4864-111">En fazla uzunluk aşıldığında, sistem bir bip sesi yayar ve metin kutusunda daha fazla tüm karakterleri kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="c4864-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="c4864-112">Bu bir parola uzunluğu en fazla yapmak isteyebilirsiniz Not, parolanızı tahmin etmeye çalıştığınız saldırganlar için kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4864-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>  
  
     <span data-ttu-id="c4864-113">Aşağıdaki kod örneğinde nasıl başlatılacağını en fazla 14 karakter uzunluğunda bir dize kabul edin ve dize yerine bir yıldız görüntüler bir metin kutusu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4864-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="c4864-114">`InitializeMyControl` Yordamı değil yürütülecek otomatik olarak; çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4864-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c4864-115">Kullanarak <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özellik metin kutusundaki diğer kişilerin bunlar, girerek kullanıcı gözlemlerseniz, bir kullanıcının parolasını belirlemek mümkün olmayacaktır olun yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4864-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="c4864-116">Bu güvenlik önlemi depolama veya uygulama mantığınızın nedeniyle gerçekleşen parola iletim tamamını kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="c4864-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="c4864-117">Girilen metin herhangi bir yolla şifrelenmediğinden diğer gizli verileri gibi düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c4864-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="c4864-118">Bu nedenle görünmez olsa da, (bazı ek güvenlik önlemi uygulanmış sürece) parola yine de bir düz metin dizesi olarak kabul ediliyor.</span><span class="sxs-lookup"><span data-stu-id="c4864-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c4864-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4864-119">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="c4864-120">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c4864-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="c4864-121">Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını belirleme</span><span class="sxs-lookup"><span data-stu-id="c4864-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="c4864-122">Nasıl yapılır: Salt okunur metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4864-122">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="c4864-123">Nasıl yapılır: Dizeye tırnak işaretleri koyma</span><span class="sxs-lookup"><span data-stu-id="c4864-123">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="c4864-124">Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç</span><span class="sxs-lookup"><span data-stu-id="c4864-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="c4864-125">Nasıl yapılır: Windows Forms TextBox denetiminde birden çok satır görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c4864-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="c4864-126">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="c4864-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)

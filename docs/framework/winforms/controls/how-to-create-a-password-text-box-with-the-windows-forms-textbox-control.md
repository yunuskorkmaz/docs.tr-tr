---
title: "Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma"
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
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: caf5cef9e23134715101545902e32e72d63c0aac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="08fec-102">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08fec-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>
<span data-ttu-id="08fec-103">Parola kutusu yer tutucu karakterler bir kullanıcı bir dize türleri sırada görüntüleyen bir Windows Forms metin kutusu olur.</span><span class="sxs-lookup"><span data-stu-id="08fec-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>  
  
### <a name="to-create-a-password-text-box"></a><span data-ttu-id="08fec-104">Parola metin kutusu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="08fec-104">To create a password text box</span></span>  
  
1.  <span data-ttu-id="08fec-105">Ayarlama <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özelliği <xref:System.Windows.Forms.TextBox> denetlemek için bir özel karakter.</span><span class="sxs-lookup"><span data-stu-id="08fec-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>  
  
     <span data-ttu-id="08fec-106"><xref:System.Windows.Forms.TextBox.PasswordChar%2A> Özellik metin kutusunda görüntülenen karakter belirtir.</span><span class="sxs-lookup"><span data-stu-id="08fec-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="08fec-107">Örneğin, parola kutusunda görüntülenen yıldızlar istiyorsanız belirtin * için <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Özellikleri penceresinde özelliği.</span><span class="sxs-lookup"><span data-stu-id="08fec-107">For example, if you want asterisks displayed in the password box, specify * for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="08fec-108">Ardından, metin kutusuna bir kullanıcı türleri hangi karakter bağımsız olarak bir yıldız işareti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="08fec-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>  
  
2.  <span data-ttu-id="08fec-109">(İsteğe bağlı) Ayarlama <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="08fec-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="08fec-110">Özelliği kaç karakterin metin kutusunda girilebilen belirler.</span><span class="sxs-lookup"><span data-stu-id="08fec-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="08fec-111">En büyük uzunluğu aştı, sistem bip sesi yayar ve metin kutusuna daha fazla tüm karakterleri kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="08fec-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="08fec-112">Bu parola uzunluk üst sınırı yapmak isteyebilirsiniz Not kullanım için parolanızı tahmin etmeyi denemelerini saldırganlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="08fec-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>  
  
     <span data-ttu-id="08fec-113">Aşağıdaki kod örneği, en çok 14 karakter uzunluğunda bir dize kabul etmek ve dize yerine bir yıldız işareti görüntüleme bir metin kutusu başlatılmaya gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08fec-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="08fec-114">`InitializeMyControl` Yordamı değil yürütülecek otomatik olarak; çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08fec-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="08fec-115">Kullanarak <xref:System.Windows.Forms.TextBox.PasswordChar%2A> bir metin kutusu özellikte diğer kişilerin bunu giren kullanıcı gözlemlerseniz, bir kullanıcının parolasını belirlemek mümkün olmaz olun yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="08fec-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="08fec-116">Bu güvenlik önlemi her tür depolama ya da uygulama mantığınızın nedeniyle oluşabilir parola iletimini kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="08fec-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="08fec-117">Girilen metin herhangi bir şekilde şifrelenmediğinden diğer gizli veriler gibi düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="08fec-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="08fec-118">Bu nedenle görünmez olsa bile (bazı ek güvenlik önlemi uygulanan sürece) parola hala bir düz metin dizesi olarak kabul ediliyor.</span><span class="sxs-lookup"><span data-stu-id="08fec-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08fec-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08fec-119">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="08fec-120">TextBox denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="08fec-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="08fec-121">Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını denetleme</span><span class="sxs-lookup"><span data-stu-id="08fec-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="08fec-122">Nasıl yapılır: salt okunur metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="08fec-122">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="08fec-123">Nasıl yapılır: dizeye tırnak işaretleri koyma</span><span class="sxs-lookup"><span data-stu-id="08fec-123">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="08fec-124">Nasıl yapılır: metni seçme Windows Forms TextBox denetiminde</span><span class="sxs-lookup"><span data-stu-id="08fec-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="08fec-125">Nasıl yapılır: birden çok satır Windows Forms TextBox denetiminde görünümü</span><span class="sxs-lookup"><span data-stu-id="08fec-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="08fec-126">TextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="08fec-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)

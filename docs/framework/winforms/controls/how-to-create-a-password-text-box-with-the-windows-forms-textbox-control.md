---
title: TextBox denetimiyle parola metin kutusu oluşturma
description: Bir Kullanıcı bir dize yazdığında, yer tutucu karakterleri görüntüleyen Windows Forms bir metni nasıl oluşturabileceğinizi öğrenin.
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
ms.openlocfilehash: 6d7e61eefa44ce3152aa77e3922bde471a4aeaf3
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904318"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="4e69a-103">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e69a-103">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>

<span data-ttu-id="4e69a-104">Parola kutusu, bir Kullanıcı bir dize yazdığında yer tutucu karakterleri görüntüleyen bir Windows Forms metin kutusudur.</span><span class="sxs-lookup"><span data-stu-id="4e69a-104">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>

### <a name="to-create-a-password-text-box"></a><span data-ttu-id="4e69a-105">Parola metin kutusu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4e69a-105">To create a password text box</span></span>

1. <span data-ttu-id="4e69a-106"><xref:System.Windows.Forms.TextBox.PasswordChar%2A> <xref:System.Windows.Forms.TextBox> Denetimin özelliğini belirli bir karakter olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4e69a-106">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>

    <span data-ttu-id="4e69a-107"><xref:System.Windows.Forms.TextBox.PasswordChar%2A>Özelliği metin kutusunda gösterilecek karakteri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e69a-107">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="4e69a-108">Örneğin, parola kutusunda yıldız işaretlerini isterseniz, Özellikler penceresi özellik için \* belirtin <xref:System.Windows.Forms.TextBox.PasswordChar%2A> .</span><span class="sxs-lookup"><span data-stu-id="4e69a-108">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="4e69a-109">Ardından, kullanıcının metin kutusunda ne kadar karakterinde olduğuna bakılmaksızın bir yıldız işareti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4e69a-109">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>

2. <span data-ttu-id="4e69a-110">Seçim Özelliği ayarlayın <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> .</span><span class="sxs-lookup"><span data-stu-id="4e69a-110">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="4e69a-111">Özelliği, metin kutusuna kaç karakter girilebileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="4e69a-111">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="4e69a-112">Maksimum uzunluk aşılırsa sistem bir bip sesi yayar ve metin kutusu daha fazla karakter kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="4e69a-112">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="4e69a-113">Parolayı tahmin etmeye çalışan saldırganlar için bir parolanın en fazla uzunluğu kullanım dışı olabileceğinden bunu yapmak istemediğiniz unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e69a-113">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>

    <span data-ttu-id="4e69a-114">Aşağıdaki kod örneğinde, en fazla 14 karakter uzunluğunda bir dizeyi kabul edecek ve dize yerine yıldız işaretlerini gösteren bir metin kutusunun nasıl başlatıldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4e69a-114">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="4e69a-115">`InitializeMyControl`Yordam otomatik olarak yürütülmeyecektir; çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e69a-115">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="4e69a-116"><xref:System.Windows.Forms.TextBox.PasswordChar%2A>Özelliği metin kutusu üzerinde kullanmak, Kullanıcı tarafından giriş gözlemlerse, diğer kişilerin bir kullanıcının parolasını belirleyememesini sağlamaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e69a-116">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="4e69a-117">Bu güvenlik ölçüsü, Uygulama mantığınız nedeniyle gerçekleşebileceğini herhangi bir depolama veya parola aktarımını kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="4e69a-117">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="4e69a-118">Girilen metin herhangi bir şekilde şifrelenmediğinden, diğer gizli veriler gibi davranmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e69a-118">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="4e69a-119">Bu gibi görünmese de, parola hala düz metin dizesi olarak değerlendirildi (bazı ek güvenlik ölçüsü gerçekleştirmediğiniz sürece).</span><span class="sxs-lookup"><span data-stu-id="4e69a-119">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4e69a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e69a-120">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="4e69a-121">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e69a-121">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="4e69a-122">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="4e69a-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="4e69a-123">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e69a-123">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="4e69a-124">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="4e69a-124">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="4e69a-125">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="4e69a-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4e69a-126">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4e69a-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4e69a-127">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="4e69a-127">TextBox Control</span></span>](textbox-control-windows-forms.md)

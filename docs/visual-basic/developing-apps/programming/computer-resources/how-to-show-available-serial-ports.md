---
title: "Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme"
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cda98e8261669b2f20045e51b5ccef2e5db98a72
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="a93da-102">Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="a93da-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="a93da-103">Bu konuda nasıl kullanılacağını açıklar `My.Computer.Ports` Visual Basic'te bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için.</span><span class="sxs-lookup"><span data-stu-id="a93da-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="a93da-104">Kullanılacak bağlantı noktasını seçmek bir kullanıcı izin vermek için seri bağlantı noktalarının adlarını yerleştirilir bir <xref:System.Windows.Forms.ListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="a93da-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a93da-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a93da-105">Example</span></span>  
 <span data-ttu-id="a93da-106">Bu örnek döngü tüm dizeler, `My.Computer.Ports.SerialPortNames` özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="a93da-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="a93da-107">Bu bilgisayardaki kullanılabilir seri bağlantı noktalarına adlarını dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="a93da-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="a93da-108">Genellikle, bir kullanıcı uygulama kullanması gereken hangi seri bağlantı noktası kullanılabilir bağlantı noktaları listeden seçer.</span><span class="sxs-lookup"><span data-stu-id="a93da-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="a93da-109">Bu örnekte, seri bağlantı noktası adları depolanmış bir <xref:System.Windows.Forms.ListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="a93da-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="a93da-110">Daha fazla bilgi için bkz: [ListBox denetimi](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a93da-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 <span data-ttu-id="a93da-111">Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a93da-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a93da-112">Kod parçacığı Seçici bulunur **bağlantısı ve ağ**.</span><span class="sxs-lookup"><span data-stu-id="a93da-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="a93da-113">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a93da-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a93da-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a93da-114">Compiling the Code</span></span>  
 <span data-ttu-id="a93da-115">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a93da-115">This example requires:</span></span>  
  
-   <span data-ttu-id="a93da-116">System.Windows.Forms.dll proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="a93da-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="a93da-117">Üye erişimi <xref:System.Windows.Forms> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a93da-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="a93da-118">Ekleme bir `Imports` üye adlarının kodunuzda tam olarak niteleyemiyorsanız deyimi.</span><span class="sxs-lookup"><span data-stu-id="a93da-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="a93da-119">Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a93da-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="a93da-120">Formunuz sahip bir <xref:System.Windows.Forms.ListBox> adlı Denetim `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="a93da-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a93da-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a93da-121">Robust Programming</span></span>  
 <span data-ttu-id="a93da-122">Kullanmak zorunda değil <xref:System.Windows.Forms.ListBox> kullanılabilir seri bağlantı noktası adlarını görüntülemek için denetim.</span><span class="sxs-lookup"><span data-stu-id="a93da-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="a93da-123">Bunun yerine kullanabileceğiniz bir <xref:System.Windows.Forms.ComboBox> veya diğer denetim.</span><span class="sxs-lookup"><span data-stu-id="a93da-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="a93da-124">Uygulama kullanıcıdan bir yanıt gerekmez, kullanabileceğiniz bir <xref:System.Windows.Forms.TextBox> bilgileri görüntülemek için denetim.</span><span class="sxs-lookup"><span data-stu-id="a93da-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a93da-125">Tarafından döndürülen bağlantı noktası adları `My.Computer.Ports.SerialPortNames` Windows 98 çalıştırdığınızda hatalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a93da-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="a93da-126">Uygulama hataları önlemek için özel durum işleme gibi kullanmak `Try...Catch...Finally` deyimi veya `Using` bağlantı noktalarını açmak için bağlantı noktası adları kullanırken deyimi.</span><span class="sxs-lookup"><span data-stu-id="a93da-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a93da-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a93da-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [<span data-ttu-id="a93da-128">Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="a93da-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="a93da-129">Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="a93da-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="a93da-130">Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="a93da-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)

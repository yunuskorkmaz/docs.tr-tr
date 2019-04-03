---
title: "Nasıl yapılır: Visual Basic'te kullanılabilir seri bağlantı noktalarını gösterme"
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 57b3a33fecb6128a10ce903fd26724de98acb8c1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834653"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="176fc-102">Nasıl yapılır: Visual Basic'te kullanılabilir seri bağlantı noktalarını gösterme</span><span class="sxs-lookup"><span data-stu-id="176fc-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="176fc-103">Bu konu nasıl kullanılacağını açıklar `My.Computer.Ports` Visual Basic'te bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için.</span><span class="sxs-lookup"><span data-stu-id="176fc-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="176fc-104">Kullanılacak bağlantı noktasını seçmek bir kullanıcı izin vermek için seri bağlantı noktası adları yerleştirilir bir <xref:System.Windows.Forms.ListBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="176fc-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="176fc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="176fc-105">Example</span></span>  
 <span data-ttu-id="176fc-106">Bu örnek döngü tüm dizeler, `My.Computer.Ports.SerialPortNames` özelliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="176fc-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="176fc-107">Bu dizeler bilgisayardaki kullanılabilir seri bağlantı noktalarına adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="176fc-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="176fc-108">Genellikle, kullanıcı uygulamayı kullanması gereken hangi seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçer.</span><span class="sxs-lookup"><span data-stu-id="176fc-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="176fc-109">Bu örnekte, seri bağlantı noktası adları içinde depolanan bir <xref:System.Windows.Forms.ListBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="176fc-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="176fc-110">Daha fazla bilgi için [ListBox denetimi](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="176fc-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="176fc-111">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="176fc-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="176fc-112">Kod parçacığı Seçici'de bulunur **bağlantı ve ağ**.</span><span class="sxs-lookup"><span data-stu-id="176fc-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="176fc-113">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="176fc-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="176fc-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="176fc-114">Compiling the Code</span></span>  
 <span data-ttu-id="176fc-115">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="176fc-115">This example requires:</span></span>  
  
-   <span data-ttu-id="176fc-116">System.Windows.Forms.dll'e bir proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="176fc-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="176fc-117">Üye erişimi <xref:System.Windows.Forms> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="176fc-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="176fc-118">Ekleme bir `Imports` üye adları kodunuzda tamamen niteleyemiyorsanız deyimi.</span><span class="sxs-lookup"><span data-stu-id="176fc-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="176fc-119">Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="176fc-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="176fc-120">Formunuza sahip bir <xref:System.Windows.Forms.ListBox> adlı Denetim `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="176fc-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="176fc-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="176fc-121">Robust Programming</span></span>  
 <span data-ttu-id="176fc-122">Kullanmak zorunda değil <xref:System.Windows.Forms.ListBox> kullanılabilir seri bağlantı noktası adlarını görüntülemek için denetim.</span><span class="sxs-lookup"><span data-stu-id="176fc-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="176fc-123">Bunun yerine kullanabileceğiniz bir <xref:System.Windows.Forms.ComboBox> veya diğer denetim.</span><span class="sxs-lookup"><span data-stu-id="176fc-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="176fc-124">Kullanıcıdan bir yanıt uygulama gereksinimi yoksa, kullanabileceğiniz bir <xref:System.Windows.Forms.TextBox> bilgileri görüntülemek için denetim.</span><span class="sxs-lookup"><span data-stu-id="176fc-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="176fc-125">Tarafından döndürülen bağlantı noktası adları `My.Computer.Ports.SerialPortNames` Windows 98 çalıştırdığınızda yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="176fc-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="176fc-126">Uygulama hatalarını önlemek için özel durum işleme gibi kullanın `Try...Catch...Finally` deyimi veya `Using` bağlantı noktalarını açmak için bağlantı noktası adları kullanarak deyimi.</span><span class="sxs-lookup"><span data-stu-id="176fc-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176fc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="176fc-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="176fc-128">Nasıl yapılır: Seri bağlantı noktalarına ekli modemleri çevirme</span><span class="sxs-lookup"><span data-stu-id="176fc-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="176fc-129">Nasıl yapılır: Seri bağlantı noktalarına dizeler gönderme</span><span class="sxs-lookup"><span data-stu-id="176fc-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="176fc-130">Nasıl yapılır: Seri bağlantı noktalarından dize alma</span><span class="sxs-lookup"><span data-stu-id="176fc-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)

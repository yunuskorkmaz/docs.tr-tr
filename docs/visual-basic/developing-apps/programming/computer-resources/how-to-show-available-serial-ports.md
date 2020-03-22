---
title: 'Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c7e5f797c1d098a3b2d01745b949ed50375ea7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345569"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="b30da-102">Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="b30da-102">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="b30da-103">Bu konu, Visual `My.Computer.Ports` Basic'te bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b30da-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="b30da-104">Bir kullanıcının hangi bağlantı noktasını kullanacağını seçmesine izin vermek için, seri bağlantı noktalarının adları denetime <xref:System.Windows.Forms.ListBox> yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b30da-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b30da-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b30da-105">Example</span></span>  

 <span data-ttu-id="b30da-106">Bu örnek, özelliğin `My.Computer.Ports.SerialPortNames` döndürdüğü bütün dizeleri üzerinde döngüler.</span><span class="sxs-lookup"><span data-stu-id="b30da-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="b30da-107">Bu dizeleri bilgisayarda kullanılabilir seri bağlantı noktalarının adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="b30da-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="b30da-108">Genellikle, bir kullanıcı kullanılabilir bağlantı noktaları listesinden uygulamanın hangi seri bağlantı noktasını kullanması gerektiğini seçer.</span><span class="sxs-lookup"><span data-stu-id="b30da-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="b30da-109">Bu örnekte, seri bağlantı noktası adları <xref:System.Windows.Forms.ListBox> denetimde depolanır.</span><span class="sxs-lookup"><span data-stu-id="b30da-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="b30da-110">Daha fazla bilgi için [ListBox Denetimi'ne](../../../../framework/winforms/controls/listbox-control-windows-forms.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b30da-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="b30da-111">Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b30da-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b30da-112">Kod snippet toplayıcı, **bağlantı ve ağ**bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b30da-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="b30da-113">Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.</span><span class="sxs-lookup"><span data-stu-id="b30da-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b30da-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b30da-114">Compiling the Code</span></span>  

 <span data-ttu-id="b30da-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b30da-115">This example requires:</span></span>  
  
- <span data-ttu-id="b30da-116">System.Windows.Forms.dll için bir proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="b30da-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="b30da-117">Ad alanının üyelerine <xref:System.Windows.Forms> erişim.</span><span class="sxs-lookup"><span data-stu-id="b30da-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="b30da-118">Kodunuzda `Imports` üye adlarını tam olarak nitelemediğiniz bir ekstre ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b30da-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="b30da-119">Daha fazla bilgi [için, Bkz. İçerme Bildirimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="b30da-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="b30da-120">Formunuzun bir <xref:System.Windows.Forms.ListBox> denetimi `ListBox1`var.</span><span class="sxs-lookup"><span data-stu-id="b30da-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b30da-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b30da-121">Robust Programming</span></span>  

 <span data-ttu-id="b30da-122">Kullanılabilir seri bağlantı noktası <xref:System.Windows.Forms.ListBox> adlarını görüntülemek için denetimi kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b30da-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="b30da-123">Bunun yerine, bir <xref:System.Windows.Forms.ComboBox> veya başka bir denetim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b30da-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="b30da-124">Uygulamanın kullanıcıdan yanıt alabına ihtiyacı <xref:System.Windows.Forms.TextBox> yoksa, bilgileri görüntülemek için bir denetim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b30da-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b30da-125">Windows 98'de çalıştırıldığında döndürülen bağlantı noktası adları yanlış `My.Computer.Ports.SerialPortNames` olabilir.</span><span class="sxs-lookup"><span data-stu-id="b30da-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="b30da-126">Uygulama hatalarını önlemek için, bağlantı `Try...Catch...Finally` noktalarını `Using` açmak için bağlantı noktası adlarını kullanırken deyim veya deyim gibi özel durum işlemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b30da-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b30da-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b30da-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="b30da-128">Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="b30da-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="b30da-129">Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="b30da-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="b30da-130">Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="b30da-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)

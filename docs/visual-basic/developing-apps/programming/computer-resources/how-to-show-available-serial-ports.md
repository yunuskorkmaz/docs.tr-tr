---
title: "Nasıl yapılır: Visual Basic 'de kullanılabilir seri bağlantı noktalarını göster"
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: e8e0f6d63f7135c3bbe24ee6426cd714f2eb275f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956918"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="57d7a-102">Nasıl yapılır: Visual Basic 'de kullanılabilir seri bağlantı noktalarını göster</span><span class="sxs-lookup"><span data-stu-id="57d7a-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="57d7a-103">Bu konuda, Visual Basic ' de `My.Computer.Ports` bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57d7a-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="57d7a-104">Bir kullanıcının kullanılacak bağlantı noktasını seçmesine izin vermek için seri bağlantı noktalarının adları bir <xref:System.Windows.Forms.ListBox> denetime yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="57d7a-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57d7a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="57d7a-105">Example</span></span>  
 <span data-ttu-id="57d7a-106">Bu örnek, `My.Computer.Ports.SerialPortNames` özelliğin döndürdüğü tüm dizelerin üzerinde döngüye geçer.</span><span class="sxs-lookup"><span data-stu-id="57d7a-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="57d7a-107">Bu dizeler bilgisayardaki kullanılabilir seri bağlantı noktalarının adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="57d7a-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="57d7a-108">Genellikle, bir kullanıcı uygulamanın kullanılabilir bağlantı noktaları listesinden kullanması gereken seri bağlantı noktasını seçer.</span><span class="sxs-lookup"><span data-stu-id="57d7a-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="57d7a-109">Bu örnekte, seri bağlantı noktası adları bir <xref:System.Windows.Forms.ListBox> denetimde depolanır.</span><span class="sxs-lookup"><span data-stu-id="57d7a-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="57d7a-110">Daha fazla bilgi için bkz. [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="57d7a-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="57d7a-111">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57d7a-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="57d7a-112">Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="57d7a-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="57d7a-113">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="57d7a-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57d7a-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="57d7a-114">Compiling the Code</span></span>  
 <span data-ttu-id="57d7a-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="57d7a-115">This example requires:</span></span>  
  
- <span data-ttu-id="57d7a-116">System. Windows. Forms. dll ' ye bir proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="57d7a-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="57d7a-117"><xref:System.Windows.Forms> Ad alanının üyelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="57d7a-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="57d7a-118">Kodunuzda üye `Imports` adlarını tam olarak nitedıysanız bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="57d7a-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="57d7a-119">Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="57d7a-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="57d7a-120">Formunuzda adlı <xref:System.Windows.Forms.ListBox> `ListBox1`bir denetim vardır.</span><span class="sxs-lookup"><span data-stu-id="57d7a-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="57d7a-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="57d7a-121">Robust Programming</span></span>  
 <span data-ttu-id="57d7a-122">Kullanılabilir seri bağlantı noktası adlarını göstermek için <xref:System.Windows.Forms.ListBox> denetimi kullanmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="57d7a-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="57d7a-123">Bunun yerine, bir veya başka <xref:System.Windows.Forms.ComboBox> bir denetim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57d7a-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="57d7a-124">Uygulamanın kullanıcıdan bir yanıt ihtiyacı yoksa, bilgileri göstermek için bir <xref:System.Windows.Forms.TextBox> denetim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57d7a-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57d7a-125">Tarafından `My.Computer.Ports.SerialPortNames` döndürülen bağlantı noktası adları, Windows 98 üzerinde çalıştırıldığında yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="57d7a-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="57d7a-126">Uygulama hatalarını engellemek için, bağlantı noktalarını açmak üzere bağlantı noktası adlarını `Try...Catch...Finally` kullanırken, bildirim `Using` veya bildirim gibi özel durum işleme kullanın.</span><span class="sxs-lookup"><span data-stu-id="57d7a-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d7a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57d7a-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="57d7a-128">Nasıl yapılır: Seri bağlantı noktalarına bağlı modemleri ara</span><span class="sxs-lookup"><span data-stu-id="57d7a-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="57d7a-129">Nasıl yapılır: Dizeleri seri bağlantı noktalarına gönder</span><span class="sxs-lookup"><span data-stu-id="57d7a-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="57d7a-130">Nasıl yapılır: Seri bağlantı noktalarından dize alma</span><span class="sxs-lookup"><span data-stu-id="57d7a-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)

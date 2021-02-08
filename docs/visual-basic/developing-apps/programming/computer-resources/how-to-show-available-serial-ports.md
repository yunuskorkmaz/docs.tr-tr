---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic kullanılabilir seri bağlantı noktalarını gösterme'
title: 'Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 0f55e7ed7155940dd279a22ae9da5f21097f56a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775298"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="2ad81-103">Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="2ad81-103">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="2ad81-104">Bu konuda `My.Computer.Ports` , Visual Basic ' de bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ad81-104">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="2ad81-105">Bir kullanıcının kullanılacak bağlantı noktasını seçmesine izin vermek için seri bağlantı noktalarının adları bir <xref:System.Windows.Forms.ListBox> denetime yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2ad81-105">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ad81-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ad81-106">Example</span></span>  

 <span data-ttu-id="2ad81-107">Bu örnek, özelliğin döndürdüğü tüm dizelerin üzerinde döngüye geçer `My.Computer.Ports.SerialPortNames` .</span><span class="sxs-lookup"><span data-stu-id="2ad81-107">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="2ad81-108">Bu dizeler bilgisayardaki kullanılabilir seri bağlantı noktalarının adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="2ad81-108">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="2ad81-109">Genellikle, bir kullanıcı uygulamanın kullanılabilir bağlantı noktaları listesinden kullanması gereken seri bağlantı noktasını seçer.</span><span class="sxs-lookup"><span data-stu-id="2ad81-109">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="2ad81-110">Bu örnekte, seri bağlantı noktası adları bir <xref:System.Windows.Forms.ListBox> denetimde depolanır.</span><span class="sxs-lookup"><span data-stu-id="2ad81-110">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="2ad81-111">Daha fazla bilgi için bkz. [ListBox Control](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).</span><span class="sxs-lookup"><span data-stu-id="2ad81-111">For more information, see [ListBox Control](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="2ad81-112">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad81-112">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2ad81-113">Kod parçacığı seçicide, **bağlantı ve ağ** bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ad81-113">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="2ad81-114">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="2ad81-114">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ad81-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2ad81-115">Compiling the Code</span></span>  

 <span data-ttu-id="2ad81-116">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2ad81-116">This example requires:</span></span>  
  
- <span data-ttu-id="2ad81-117">System.Windows.Forms.dll bir proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="2ad81-117">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="2ad81-118"><xref:System.Windows.Forms>Ad alanının üyelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="2ad81-118">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="2ad81-119">`Imports`Kodunuzda üye adlarını tam olarak nitedıysanız bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2ad81-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="2ad81-120">Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="2ad81-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="2ad81-121">Formunuzda adlı bir denetim vardır <xref:System.Windows.Forms.ListBox> `ListBox1` .</span><span class="sxs-lookup"><span data-stu-id="2ad81-121">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2ad81-122">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2ad81-122">Robust Programming</span></span>  

 <span data-ttu-id="2ad81-123"><xref:System.Windows.Forms.ListBox>Kullanılabilir seri bağlantı noktası adlarını göstermek için denetimi kullanmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ad81-123">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="2ad81-124">Bunun yerine, bir <xref:System.Windows.Forms.ComboBox> veya başka bir denetim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ad81-124">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="2ad81-125">Uygulamanın kullanıcıdan bir yanıt ihtiyacı yoksa, <xref:System.Windows.Forms.TextBox> bilgileri göstermek için bir denetim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ad81-125">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ad81-126">Tarafından döndürülen bağlantı noktası adları, `My.Computer.Ports.SerialPortNames` Windows 98 üzerinde çalıştırıldığında yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad81-126">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="2ad81-127">Uygulama hatalarını engellemek için, bağlantı `Try...Catch...Finally` `Using` noktalarını açmak üzere bağlantı noktası adlarını kullanırken, bildirim veya bildirim gibi özel durum işleme kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ad81-127">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad81-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ad81-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="2ad81-129">Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="2ad81-129">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="2ad81-130">Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="2ad81-130">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="2ad81-131">Nasıl yapılır: Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="2ad81-131">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)

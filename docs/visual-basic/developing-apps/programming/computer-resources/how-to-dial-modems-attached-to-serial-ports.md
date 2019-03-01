---
title: "Nasıl yapılır: Visual Basic'te seri bağlantı noktalarına ekli modemleri çevirme"
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: f8eda72f72a1d152030aef620a4e3868573b7244
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971656"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="e4e37-102">Nasıl yapılır: Visual Basic'te seri bağlantı noktalarına ekli modemleri çevirme</span><span class="sxs-lookup"><span data-stu-id="e4e37-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="e4e37-103">Bu konu nasıl kullanılacağını açıklar `My.Computer.Ports` Visual Basic'te bir modem çevirmek için.</span><span class="sxs-lookup"><span data-stu-id="e4e37-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="e4e37-104">Genellikle, bilgisayardaki seri bağlantı noktalarından birine modem bağlı.</span><span class="sxs-lookup"><span data-stu-id="e4e37-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="e4e37-105">Modem ile iletişim kurmak, uygulamanız için uygun bir seri bağlantı noktasına komutları göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4e37-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="e4e37-106">Modem aramak için</span><span class="sxs-lookup"><span data-stu-id="e4e37-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="e4e37-107">Modem bağlı hangi seri bağlantı noktası belirleyin.</span><span class="sxs-lookup"><span data-stu-id="e4e37-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="e4e37-108">Bu örnekte, COM1 üzerinde modem olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="e4e37-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="e4e37-109">Kullanım `My.Computer.Ports.OpenSerialPort` bağlantı noktasına bir başvuru almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e4e37-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="e4e37-110">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4e37-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="e4e37-111">`Using` Blok bile bir özel durum oluşturur seri bağlantı noktası kapatmak uygulama izin verir.</span><span class="sxs-lookup"><span data-stu-id="e4e37-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="e4e37-112">Seri bağlantı noktası yöneten tüm kod gözükeceğini bu blok içinde veya içinde bir `Try...Catch...Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="e4e37-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3.  <span data-ttu-id="e4e37-113">Ayarlama `DtrEnable` bilgisayar modemden gelen bir iletim kabul etmeye hazır olduğunu belirtmek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4e37-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4.  <span data-ttu-id="e4e37-114">Modem ile seri bağlantı noktası aracılığıyla arama komut ve telefon numarası göndermek <xref:System.IO.Ports.SerialPort.Write%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e4e37-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="e4e37-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4e37-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="e4e37-116">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4e37-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="e4e37-117">Kod parçacığı Seçici'de bulunur **bağlantı ve ağ**.</span><span class="sxs-lookup"><span data-stu-id="e4e37-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="e4e37-118">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="e4e37-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4e37-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e4e37-119">Compiling the Code</span></span>  
 <span data-ttu-id="e4e37-120">Bu örnek, bir başvuru gerektirir <xref:System?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e4e37-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e4e37-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="e4e37-121">Robust Programming</span></span>  
 <span data-ttu-id="e4e37-122">Bu örnekte, modem COM1'e bağlı olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e4e37-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="e4e37-123">Kodunuzu istenen seri bağlantı noktası kullanılabilir bağlantı noktaları bir listesinden seçmek kullanıcı izin öneririz.</span><span class="sxs-lookup"><span data-stu-id="e4e37-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="e4e37-124">Daha fazla bilgi için [nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="e4e37-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="e4e37-125">Bu örnekte bir `Using` bir özel durum oluşturursa bile uygulama bağlantı noktasını kapatır emin olmak için blok.</span><span class="sxs-lookup"><span data-stu-id="e4e37-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="e4e37-126">Daha fazla bilgi için [Using deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e4e37-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="e4e37-127">Bu örnekte, uygulama modem çevirir sonra seri bağlantı noktası bağlantısını keser.</span><span class="sxs-lookup"><span data-stu-id="e4e37-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="e4e37-128">Gerçekçi olarak, modem gelen ve giden veri aktarımı isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e4e37-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="e4e37-129">Daha fazla bilgi için [nasıl yapılır: Seri bağlantı noktalarından dize alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="e4e37-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e37-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4e37-130">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="e4e37-131">Nasıl yapılır: Seri bağlantı noktalarına dizeler gönderme</span><span class="sxs-lookup"><span data-stu-id="e4e37-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="e4e37-132">Nasıl yapılır: Seri bağlantı noktalarından dize alma</span><span class="sxs-lookup"><span data-stu-id="e4e37-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="e4e37-133">Nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme</span><span class="sxs-lookup"><span data-stu-id="e4e37-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

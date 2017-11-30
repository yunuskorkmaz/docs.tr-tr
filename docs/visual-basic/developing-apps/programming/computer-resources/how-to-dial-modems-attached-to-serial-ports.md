---
title: "Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Ekli Modemleri Çevirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea1b2d6152af8919ac1aa272def4ba198b33867c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="f78b1-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="f78b1-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="f78b1-103">Bu konuda nasıl kullanılacağını açıklar `My.Computer.Ports` modem çevrilecek [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f78b1-103">This topic describes how to use `My.Computer.Ports` to dial a modem in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="f78b1-104">Genellikle, bilgisayardaki seri bağlantı noktalarından birine modem bağlı.</span><span class="sxs-lookup"><span data-stu-id="f78b1-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="f78b1-105">Modem ile iletişim kurmak, uygulamanız için uygun seri bağlantı noktasına komutları göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f78b1-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="f78b1-106">Modem aramak için</span><span class="sxs-lookup"><span data-stu-id="f78b1-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="f78b1-107">Modem bağlı hangi seri bağlantı noktası belirleyin.</span><span class="sxs-lookup"><span data-stu-id="f78b1-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="f78b1-108">Bu örnek, COM1 üzerindeki modem olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="f78b1-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="f78b1-109">Kullanım `My.Computer.Ports.OpenSerialPort` bir başvuru noktasına elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f78b1-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="f78b1-110">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="f78b1-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="f78b1-111">`Using` Bloğu bir özel durum oluşturursa bile seri bağlantı noktasını kapatmak uygulama izin verir.</span><span class="sxs-lookup"><span data-stu-id="f78b1-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="f78b1-112">Seri bağlantı noktası yöneten tüm kod bu bloğu içinde veya içinde görünmesi gereken bir `Try...Catch...Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="f78b1-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  <span data-ttu-id="f78b1-113">Ayarlama `DtrEnable` bilgisayarın modemden gelen bir aktarımını kabul etmeye hazır olduğunu belirtmek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="f78b1-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="f78b1-114">Arama komut ve telefon numarası yoluyla seri bağlantı noktası üzerinden modem göndermek <xref:System.IO.Ports.SerialPort.Write%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f78b1-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="f78b1-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f78b1-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 <span data-ttu-id="f78b1-116">Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f78b1-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="f78b1-117">Kod parçacığı Seçici bulunur **bağlantısı ve ağ**.</span><span class="sxs-lookup"><span data-stu-id="f78b1-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="f78b1-118">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="f78b1-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f78b1-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f78b1-119">Compiling the Code</span></span>  
 <span data-ttu-id="f78b1-120">Bu örnek, başvuru gerektirir <xref:System?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f78b1-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f78b1-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f78b1-121">Robust Programming</span></span>  
 <span data-ttu-id="f78b1-122">Bu örnekte, modem COM1'e bağlı olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="f78b1-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="f78b1-123">Kodunuzu kullanıcının istenen seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçmesine izin öneririz.</span><span class="sxs-lookup"><span data-stu-id="f78b1-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="f78b1-124">Daha fazla bilgi için bkz: [nasıl yapılır: kullanılabilir seri bağlantı noktalarını göster](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="f78b1-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="f78b1-125">Bu örnekte bir `Using` bloğu bir özel durum oluşturursa bile uygulama bağlantı noktasını kapatır emin olun.</span><span class="sxs-lookup"><span data-stu-id="f78b1-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="f78b1-126">Daha fazla bilgi için bkz: [kullanarak deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f78b1-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="f78b1-127">Bu örnekte, modem çevirir sonra uygulama seri bağlantı noktası bağlantısını keser.</span><span class="sxs-lookup"><span data-stu-id="f78b1-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="f78b1-128">Gerçekçi olarak, modem gelen ve giden veri aktarımı isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f78b1-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="f78b1-129">Daha fazla bilgi için bkz: [nasıl yapılır: alma dizeleri öğesinden seri bağlantı noktaları](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="f78b1-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f78b1-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f78b1-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="f78b1-131">Nasıl yapılır: seri bağlantı noktalarına dizeler gönderme</span><span class="sxs-lookup"><span data-stu-id="f78b1-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="f78b1-132">Nasıl yapılır: seri bağlantı noktalarından dize alma</span><span class="sxs-lookup"><span data-stu-id="f78b1-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 [<span data-ttu-id="f78b1-133">Nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme</span><span class="sxs-lookup"><span data-stu-id="f78b1-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

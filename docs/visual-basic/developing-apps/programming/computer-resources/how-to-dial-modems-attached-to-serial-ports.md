---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345635"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="8e024-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="8e024-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="8e024-103">Bu konu, Visual `My.Computer.Ports` Basic'te modem çevirmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e024-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="8e024-104">Genellikle modem, bilgisayardaki seri bağlantı noktalarından birine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="8e024-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="8e024-105">Uygulamanızın modemle iletişim kurabilmesi için komutları uygun seri bağlantı noktasına göndermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e024-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="8e024-106">Modemi çevirmek için</span><span class="sxs-lookup"><span data-stu-id="8e024-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="8e024-107">Modemin hangi seri bağlantı noktasına bağlı olduğunu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="8e024-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="8e024-108">Bu örnek, modem COM1 üzerinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="8e024-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="8e024-109">Bağlantı `My.Computer.Ports.OpenSerialPort` noktasına başvuruda bulunulmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e024-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="8e024-110">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e024-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="8e024-111">Blok, `Using` bir özel durum oluştursa bile uygulamanın seri bağlantı noktasını kapatmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8e024-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="8e024-112">Seri bağlantı noktasını işleyen tüm kodbu blok içinde `Try...Catch...Finally` veya bir blok içinde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="8e024-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="8e024-113">Bilgisayarın `DtrEnable` modemden gelen bir aktarımı kabul etmeye hazır olduğunu belirtmek için özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8e024-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="8e024-114"><xref:System.IO.Ports.SerialPort.Write%2A> Arama komutunu ve telefon numarasını yöntem le seri bağlantı noktası üzerinden modeme gönderin.</span><span class="sxs-lookup"><span data-stu-id="8e024-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="8e024-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e024-115">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="8e024-116">Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e024-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8e024-117">Kod snippet toplayıcı, **bağlantı ve ağ**bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e024-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="8e024-118">Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.</span><span class="sxs-lookup"><span data-stu-id="8e024-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e024-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8e024-119">Compiling the Code</span></span>  

 <span data-ttu-id="8e024-120">Bu örnek, <xref:System?displayProperty=nameWithType> ad alanına bir başvuru gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8e024-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8e024-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8e024-121">Robust Programming</span></span>  

 <span data-ttu-id="8e024-122">Bu örnek, modemcom1 bağlı olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="8e024-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="8e024-123">Kodunuzun, kullanıcının kullanılabilir bağlantı noktaları listesinden istenen seri bağlantı noktasını seçmesine izin vermesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="8e024-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="8e024-124">Daha fazla bilgi için [bkz: Kullanılabilir Seri Bağlantı Noktalarını Göster.](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)</span><span class="sxs-lookup"><span data-stu-id="8e024-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="8e024-125">Bu örnek, `Using` bir özel durum atsa bile uygulamanın bağlantı noktasını kapattıklarından emin olmak için bir blok kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e024-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="8e024-126">Daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/statements/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8e024-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="8e024-127">Bu örnekte, uygulama modemi çevirdikten sonra seri bağlantı noktasını keser.</span><span class="sxs-lookup"><span data-stu-id="8e024-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="8e024-128">Gerçekçi olmak gerekirse, modeme ve modemden veri aktarmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8e024-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="8e024-129">Daha fazla bilgi için [bkz: Seri Bağlantı Noktalarından Dizeleri Alma.](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)</span><span class="sxs-lookup"><span data-stu-id="8e024-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e024-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e024-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="8e024-131">Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="8e024-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="8e024-132">Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="8e024-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="8e024-133">Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="8e024-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

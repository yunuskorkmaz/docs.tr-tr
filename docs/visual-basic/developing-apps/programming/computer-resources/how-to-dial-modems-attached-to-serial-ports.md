---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345635"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="a8398-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="a8398-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="a8398-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a8398-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="a8398-104">Typically, the modem is connected to one of the serial ports on the computer.</span><span class="sxs-lookup"><span data-stu-id="a8398-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="a8398-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span><span class="sxs-lookup"><span data-stu-id="a8398-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="a8398-106">To dial a modem</span><span class="sxs-lookup"><span data-stu-id="a8398-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="a8398-107">Determine which serial port the modem is connected to.</span><span class="sxs-lookup"><span data-stu-id="a8398-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="a8398-108">This example assumes the modem is on COM1.</span><span class="sxs-lookup"><span data-stu-id="a8398-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="a8398-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span><span class="sxs-lookup"><span data-stu-id="a8398-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="a8398-110">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8398-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="a8398-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span><span class="sxs-lookup"><span data-stu-id="a8398-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="a8398-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span><span class="sxs-lookup"><span data-stu-id="a8398-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="a8398-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span><span class="sxs-lookup"><span data-stu-id="a8398-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="a8398-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span><span class="sxs-lookup"><span data-stu-id="a8398-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="a8398-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8398-115">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="a8398-116">This code example is also available as an IntelliSense code snippet.</span><span class="sxs-lookup"><span data-stu-id="a8398-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a8398-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span><span class="sxs-lookup"><span data-stu-id="a8398-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="a8398-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a8398-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a8398-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a8398-119">Compiling the Code</span></span>  

 <span data-ttu-id="a8398-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="a8398-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a8398-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a8398-121">Robust Programming</span></span>  

 <span data-ttu-id="a8398-122">This example assumes the modem is connected to COM1.</span><span class="sxs-lookup"><span data-stu-id="a8398-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="a8398-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span><span class="sxs-lookup"><span data-stu-id="a8398-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="a8398-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="a8398-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="a8398-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span><span class="sxs-lookup"><span data-stu-id="a8398-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="a8398-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a8398-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="a8398-127">In this example, the application disconnects the serial port after it dials the modem.</span><span class="sxs-lookup"><span data-stu-id="a8398-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="a8398-128">Realistically, you will want to transfer data to and from the modem.</span><span class="sxs-lookup"><span data-stu-id="a8398-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="a8398-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="a8398-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8398-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8398-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="a8398-131">Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="a8398-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="a8398-132">Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="a8398-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="a8398-133">Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="a8398-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

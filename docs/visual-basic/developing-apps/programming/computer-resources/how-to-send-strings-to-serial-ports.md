---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: b2051451142a7818a3b7d1bc564c5ae36b2579fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345581"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="c4095-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="c4095-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="c4095-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c4095-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4095-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4095-104">Example</span></span>  

 <span data-ttu-id="c4095-105">This example sends a string to the COM1 serial port.</span><span class="sxs-lookup"><span data-stu-id="c4095-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="c4095-106">You may need to use a different serial port on your computer.</span><span class="sxs-lookup"><span data-stu-id="c4095-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="c4095-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span><span class="sxs-lookup"><span data-stu-id="c4095-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="c4095-108">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4095-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="c4095-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span><span class="sxs-lookup"><span data-stu-id="c4095-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="c4095-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span><span class="sxs-lookup"><span data-stu-id="c4095-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="c4095-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span><span class="sxs-lookup"><span data-stu-id="c4095-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4095-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c4095-112">Compiling the Code</span></span>  
  
- <span data-ttu-id="c4095-113">This example assumes the computer is using `COM1`.</span><span class="sxs-lookup"><span data-stu-id="c4095-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c4095-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c4095-114">Robust Programming</span></span>  

 <span data-ttu-id="c4095-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span><span class="sxs-lookup"><span data-stu-id="c4095-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="c4095-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="c4095-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="c4095-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span><span class="sxs-lookup"><span data-stu-id="c4095-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="c4095-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c4095-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4095-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4095-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="c4095-120">Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="c4095-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="c4095-121">Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="c4095-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

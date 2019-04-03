---
title: "Nasıl yapılır: Visual Basic'te seri bağlantı noktalarına dizeler gönderme"
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: e1f0c9d5ba428f5379f8025c0e733cdbeb5204e0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822864"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="a70a5-102">Nasıl yapılır: Visual Basic'te seri bağlantı noktalarına dizeler gönderme</span><span class="sxs-lookup"><span data-stu-id="a70a5-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="a70a5-103">Bu konu nasıl kullanılacağını açıklar `My.Computer.Ports` bilgisayarın Visual Basic'te seri bağlantı noktalarına dizeler gönderme için.</span><span class="sxs-lookup"><span data-stu-id="a70a5-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a70a5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a70a5-104">Example</span></span>  
 <span data-ttu-id="a70a5-105">Bu örnek, bir dize COM1 seri bağlantı noktasına gönderir.</span><span class="sxs-lookup"><span data-stu-id="a70a5-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="a70a5-106">Bilgisayarınızda başka bir seri bağlantı noktası kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a70a5-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="a70a5-107">Kullanım `My.Computer.Ports.OpenSerialPort` bağlantı noktasına bir başvuru almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a70a5-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="a70a5-108">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="a70a5-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="a70a5-109">`Using` Blok bile bir özel durum oluşturur seri bağlantı noktası kapatmak uygulama izin verir.</span><span class="sxs-lookup"><span data-stu-id="a70a5-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="a70a5-110">Seri bağlantı noktası yöneten tüm kod gözükeceğini bu blok içinde veya içinde bir `Try...Catch...Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="a70a5-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="a70a5-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> Yöntemi verileri seri bağlantı noktasına gönderir.</span><span class="sxs-lookup"><span data-stu-id="a70a5-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a70a5-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a70a5-112">Compiling the Code</span></span>  
  
-   <span data-ttu-id="a70a5-113">Bu örnek kullandığınızı varsayar `COM1`.</span><span class="sxs-lookup"><span data-stu-id="a70a5-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a70a5-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a70a5-114">Robust Programming</span></span>  
 <span data-ttu-id="a70a5-115">Bu örnek kullandığınızı varsayar `COM1`; daha fazla esneklik için kodu kullanıcının istenen seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçmesini izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="a70a5-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="a70a5-116">Daha fazla bilgi için [nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="a70a5-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="a70a5-117">Bu örnekte bir `Using` bir özel durum oluşturursa bile uygulama bağlantı noktasını kapatır emin olmak için blok.</span><span class="sxs-lookup"><span data-stu-id="a70a5-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="a70a5-118">Daha fazla bilgi için [Using deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a70a5-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70a5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a70a5-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="a70a5-120">Nasıl yapılır: Seri bağlantı noktalarına ekli modemleri çevirme</span><span class="sxs-lookup"><span data-stu-id="a70a5-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="a70a5-121">Nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme</span><span class="sxs-lookup"><span data-stu-id="a70a5-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

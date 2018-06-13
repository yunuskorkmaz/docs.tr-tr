---
title: "Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme"
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: a00306407cfe880ebc915d74a753109cc9696f6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584033"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="859a8-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="859a8-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="859a8-103">Bu konuda nasıl kullanılacağını açıklar `My.Computer.Ports` bilgisayarın Visual Basic'te seri bağlantı noktalarına dizeler göndermek için.</span><span class="sxs-lookup"><span data-stu-id="859a8-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="859a8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="859a8-104">Example</span></span>  
 <span data-ttu-id="859a8-105">Bu örnek, bir dize COM1 seri bağlantı noktasına gönderir.</span><span class="sxs-lookup"><span data-stu-id="859a8-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="859a8-106">Bilgisayarınızda farklı bir seri bağlantı noktası kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="859a8-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="859a8-107">Kullanım `My.Computer.Ports.OpenSerialPort` bir başvuru noktasına elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="859a8-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="859a8-108">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="859a8-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="859a8-109">`Using` Bloğu bir özel durum oluşturursa bile seri bağlantı noktasını kapatmak uygulama izin verir.</span><span class="sxs-lookup"><span data-stu-id="859a8-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="859a8-110">Seri bağlantı noktası yöneten tüm kod bu bloğu içinde veya içinde görünmesi gereken bir `Try...Catch...Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="859a8-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="859a8-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> Yöntemi verileri seri bağlantı noktasına gönderir.</span><span class="sxs-lookup"><span data-stu-id="859a8-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="859a8-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="859a8-112">Compiling the Code</span></span>  
  
-   <span data-ttu-id="859a8-113">Bu örnek kullandığınızı varsayar `COM1`.</span><span class="sxs-lookup"><span data-stu-id="859a8-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="859a8-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="859a8-114">Robust Programming</span></span>  
 <span data-ttu-id="859a8-115">Bu örnek kullandığınızı varsayar `COM1`; daha fazla esneklik için kod istenilen seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçmek kullanıcı sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="859a8-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="859a8-116">Daha fazla bilgi için bkz: [nasıl yapılır: kullanılabilir seri bağlantı noktalarını göster](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="859a8-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="859a8-117">Bu örnekte bir `Using` bloğu bir özel durum oluşturursa bile uygulama bağlantı noktasını kapatır emin olun.</span><span class="sxs-lookup"><span data-stu-id="859a8-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="859a8-118">Daha fazla bilgi için bkz: [kullanarak deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="859a8-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859a8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="859a8-119">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="859a8-120">Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="859a8-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="859a8-121">Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="859a8-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

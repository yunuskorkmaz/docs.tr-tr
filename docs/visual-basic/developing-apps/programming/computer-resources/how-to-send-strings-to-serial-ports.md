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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345581"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="78737-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="78737-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="78737-103">Bu konu, Visual `My.Computer.Ports` Basic'te bilgisayarın seri bağlantı noktalarına dizeleri göndermek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="78737-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78737-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="78737-104">Example</span></span>  

 <span data-ttu-id="78737-105">Bu örnek, COM1 seri bağlantı noktasına bir dize gönderir.</span><span class="sxs-lookup"><span data-stu-id="78737-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="78737-106">Bilgisayarınızda farklı bir seri bağlantı noktası kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="78737-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="78737-107">Bağlantı `My.Computer.Ports.OpenSerialPort` noktasına başvuruda bulunulmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="78737-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="78737-108">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="78737-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="78737-109">Blok, `Using` bir özel durum oluştursa bile uygulamanın seri bağlantı noktasını kapatmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="78737-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="78737-110">Seri bağlantı noktasını işleyen tüm kodbu blok `Try...Catch...Finally` içinde veya bir blok içinde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="78737-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="78737-111">Yöntem <xref:System.IO.Ports.SerialPort.WriteLine%2A> verileri seri bağlantı noktasına gönderir.</span><span class="sxs-lookup"><span data-stu-id="78737-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="78737-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="78737-112">Compiling the Code</span></span>  
  
- <span data-ttu-id="78737-113">Bu örnek, bilgisayarın kullandığını `COM1`varsayar.</span><span class="sxs-lookup"><span data-stu-id="78737-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="78737-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="78737-114">Robust Programming</span></span>  

 <span data-ttu-id="78737-115">Bu örnek, bilgisayarın kullandığını `COM1`varsayar; daha fazla esneklik için, kod kullanıcıkullanılabilir bağlantı noktaları listesinden istenen seri bağlantı noktasını seçmek için izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="78737-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="78737-116">Daha fazla bilgi için [bkz: Kullanılabilir Seri Bağlantı Noktalarını Göster.](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)</span><span class="sxs-lookup"><span data-stu-id="78737-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="78737-117">Bu örnek, `Using` bir özel durum atsa bile uygulamanın bağlantı noktasını kapattıklarından emin olmak için bir blok kullanır.</span><span class="sxs-lookup"><span data-stu-id="78737-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="78737-118">Daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/statements/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="78737-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78737-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78737-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="78737-120">Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="78737-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="78737-121">Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="78737-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

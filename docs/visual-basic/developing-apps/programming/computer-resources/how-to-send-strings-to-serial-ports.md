---
description: 'Daha fazla bilgi edinin: nasıl yapılır: Visual Basic seri bağlantı noktalarına dizeler gönderme'
title: 'Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: 66dedaab05090af2659701e57b37b4813447b8ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666491"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="8895b-103">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="8895b-103">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="8895b-104">Bu konuda `My.Computer.Ports` , Visual Basic bilgisayarın seri bağlantı noktalarına dize göndermek için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8895b-104">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8895b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8895b-105">Example</span></span>  

 <span data-ttu-id="8895b-106">Bu örnekte, COM1 seri bağlantı noktasına bir dize gönderilir.</span><span class="sxs-lookup"><span data-stu-id="8895b-106">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="8895b-107">Bilgisayarınızda farklı bir seri bağlantı noktası kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8895b-107">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="8895b-108">`My.Computer.Ports.OpenSerialPort`Bağlantı noktasına bir başvuru almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8895b-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="8895b-109">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="8895b-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="8895b-110">`Using`Blok, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8895b-110">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="8895b-111">Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde veya bir blok içinde görünmelidir `Try...Catch...Finally` .</span><span class="sxs-lookup"><span data-stu-id="8895b-111">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="8895b-112"><xref:System.IO.Ports.SerialPort.WriteLine%2A>Yöntemi, verileri seri bağlantı noktasına gönderir.</span><span class="sxs-lookup"><span data-stu-id="8895b-112">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8895b-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8895b-113">Compiling the Code</span></span>  
  
- <span data-ttu-id="8895b-114">Bu örnekte, bilgisayarın kullandığı varsayılır `COM1` .</span><span class="sxs-lookup"><span data-stu-id="8895b-114">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8895b-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8895b-115">Robust Programming</span></span>  

 <span data-ttu-id="8895b-116">Bu örnekte, bilgisayarın kullandığı varsayılmaktadır `COM1` ; daha fazla esneklik için, kodun kullanılabilir bağlantı noktası listesinden istenen seri bağlantı noktasını seçmesine izin verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8895b-116">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="8895b-117">Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="8895b-117">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="8895b-118">Bu örnek, bir `Using` özel durum oluşturursa uygulamanın bağlantı noktasını kapatdığından emin olmak için bir bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="8895b-118">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="8895b-119">Daha fazla bilgi için bkz. [using deyimleri](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8895b-119">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8895b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8895b-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="8895b-121">Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="8895b-121">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="8895b-122">Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="8895b-122">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)

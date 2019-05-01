---
title: Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 33298fd9840630fbfd6f7f9d883cc2397a459843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921413"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="dd921-102">Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri</span><span class="sxs-lookup"><span data-stu-id="dd921-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="dd921-103">Bilgisayarınızın seri bağlantı noktaları üzerinden erişebildiğiniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıfları <xref:System.IO.Ports?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="dd921-103">You can access your computer's serial ports through the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="dd921-104">En önemli sınıfı <xref:System.IO.Ports.SerialPort>, zaman uyumlu ve olay odaklı g/ç, erişim için PIN ve kesme durumları ve seri sürücü özelliklere erişim için bir çerçeve sunar.</span><span class="sxs-lookup"><span data-stu-id="dd921-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="dd921-105">İçinde sarmalanabilir bir <xref:System.IO.Stream> nesnesi üzerinden erişilebilir <xref:System.IO.Ports.SerialPort.BaseStream> özelliği.</span><span class="sxs-lookup"><span data-stu-id="dd921-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="dd921-106">Sarmalama <xref:System.IO.Ports.SerialPort> içinde bir <xref:System.IO.Stream> nesne akışları kullanan sınıfları tarafından erişilecek seri bağlantı noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd921-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="dd921-107">Ad alanı, seri bağlantı denetimi basitleştiren sabit listeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dd921-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="dd921-108">En basit yolu oluşturmak için bir <xref:System.IO.Ports.SerialPort> nesnedir aracılığıyla <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd921-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd921-109">Kullanamazsınız [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bağlantı noktaları, paralel bağlantı noktaları, USB bağlantı noktası vb. gibi diğer tür doğrudan erişmek için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="dd921-109">You cannot use [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="dd921-110">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="dd921-110">Enumerations</span></span>  
 <span data-ttu-id="dd921-111">Bu tablo, listeler ve seri bağlantı noktası erişmek için kullanılan ana numaralandırmaları açıklar:</span><span class="sxs-lookup"><span data-stu-id="dd921-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="dd921-112">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="dd921-112">Enumeration</span></span>|<span data-ttu-id="dd921-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd921-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="dd921-114">Bir seri bağlantı noktası iletişimi için oluşturmada kullanılan Denetim Protokolü belirtir bir <xref:System.IO.Ports.SerialPort> nesne.</span><span class="sxs-lookup"><span data-stu-id="dd921-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="dd921-115">İçin eşlik biti belirtir bir <xref:System.IO.Ports.SerialPort> nesne.</span><span class="sxs-lookup"><span data-stu-id="dd921-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="dd921-116">Seri bağlantı noktasında alınan karakter türünü belirtir <xref:System.IO.Ports.SerialPort> nesne.</span><span class="sxs-lookup"><span data-stu-id="dd921-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="dd921-117">Gerçekleşen hataları belirtir <xref:System.IO.Ports.SerialPort> nesnesi</span><span class="sxs-lookup"><span data-stu-id="dd921-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="dd921-118">Üzerinde gerçekleşen değişiklik türünü belirtir <xref:System.IO.Ports.SerialPort> nesne.</span><span class="sxs-lookup"><span data-stu-id="dd921-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="dd921-119">Kullanılan Dur bitleri belirtir <xref:System.IO.Ports.SerialPort> nesne.</span><span class="sxs-lookup"><span data-stu-id="dd921-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd921-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd921-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="dd921-121">Bilgisayar Bağlantı Noktalarına Erişme</span><span class="sxs-lookup"><span data-stu-id="dd921-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

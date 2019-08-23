---
title: Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 936ff4c861444d3a971b38fd7b2a0af38b19494b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916599"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="f730a-102">Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri</span><span class="sxs-lookup"><span data-stu-id="f730a-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="f730a-103"><xref:System.IO.Ports?displayProperty=nameWithType> Ad alanındaki .NET Framework sınıfları aracılığıyla bilgisayarınızın seri bağlantı noktalarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f730a-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f730a-104">En önemli sınıf <xref:System.IO.Ports.SerialPort>, zaman uyumlu ve olay odaklı g/ç için bir çerçeve, PIN ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f730a-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="f730a-105">Özelliği aracılığıyla erişilebilen bir <xref:System.IO.Stream> nesneye kaydırılmış olabilir. <xref:System.IO.Ports.SerialPort.BaseStream></span><span class="sxs-lookup"><span data-stu-id="f730a-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="f730a-106"><xref:System.IO.Ports.SerialPort> Bir<xref:System.IO.Stream> nesne içine sarmalama, seri bağlantı noktasına akışlar kullanan sınıflar tarafından erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f730a-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="f730a-107">Ad alanı, seri bağlantı noktalarının denetimini kolaylaştıran numaralandırmalar içerir.</span><span class="sxs-lookup"><span data-stu-id="f730a-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="f730a-108">Bir <xref:System.IO.Ports.SerialPort> nesne<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> oluşturmanın en basit yolu yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="f730a-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f730a-109">Paralel bağlantı noktaları, USB bağlantı noktaları vb. gibi diğer bağlantı noktası türlerine doğrudan erişmek için .NET Framework sınıfları kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f730a-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="f730a-110">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="f730a-110">Enumerations</span></span>  
 <span data-ttu-id="f730a-111">Bu tablo, bir seri bağlantı noktasına erişmek için kullanılan ana numaralandırmaları listeler ve açıklar:</span><span class="sxs-lookup"><span data-stu-id="f730a-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="f730a-112">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f730a-112">Enumeration</span></span>|<span data-ttu-id="f730a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f730a-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="f730a-114">Bir <xref:System.IO.Ports.SerialPort> nesne için seri bağlantı noktası iletişimi kurarken kullanılan denetim protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f730a-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="f730a-115">Bir <xref:System.IO.Ports.SerialPort> nesne için eşlik bitini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f730a-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="f730a-116"><xref:System.IO.Ports.SerialPort> Nesnenin seri bağlantı noktasında alınan karakter türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f730a-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="f730a-117"><xref:System.IO.Ports.SerialPort> Nesnede oluşan hataları belirtir</span><span class="sxs-lookup"><span data-stu-id="f730a-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="f730a-118"><xref:System.IO.Ports.SerialPort> Nesnede gerçekleşen değişikliğin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f730a-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="f730a-119"><xref:System.IO.Ports.SerialPort> Nesnede kullanılan durdurma bitlerinin sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f730a-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f730a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f730a-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="f730a-121">Bilgisayar Bağlantı Noktalarına Erişme</span><span class="sxs-lookup"><span data-stu-id="f730a-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

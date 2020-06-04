---
title: .NET Framework'te Bağlantı Noktası İşlemleri
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 0ef0b8a7aec40603185d227d972cea655fd238c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360143"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="52c1c-102">Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri</span><span class="sxs-lookup"><span data-stu-id="52c1c-102">Port Operations in the .NET Framework with Visual Basic</span></span>

<span data-ttu-id="52c1c-103">Ad alanındaki .NET Framework sınıfları aracılığıyla bilgisayarınızın seri bağlantı noktalarına erişebilirsiniz <xref:System.IO.Ports?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="52c1c-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="52c1c-104">En önemli sınıf, <xref:System.IO.Ports.SerialPort> zaman uyumlu ve olay odaklı g/ç için bir çerçeve, PIN ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="52c1c-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="52c1c-105"><xref:System.IO.Stream>Özelliği aracılığıyla erişilebilen bir nesneye kaydırılmış olabilir <xref:System.IO.Ports.SerialPort.BaseStream> .</span><span class="sxs-lookup"><span data-stu-id="52c1c-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="52c1c-106"><xref:System.IO.Ports.SerialPort>Bir nesne içine sarmalama <xref:System.IO.Stream> , seri bağlantı noktasına akışlar kullanan sınıflar tarafından erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="52c1c-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="52c1c-107">Ad alanı, seri bağlantı noktalarının denetimini kolaylaştıran numaralandırmalar içerir.</span><span class="sxs-lookup"><span data-stu-id="52c1c-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>

<span data-ttu-id="52c1c-108">Bir nesne oluşturmanın en basit yolu <xref:System.IO.Ports.SerialPort> <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="52c1c-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="52c1c-109">Paralel bağlantı noktaları, USB bağlantı noktaları vb. gibi diğer bağlantı noktası türlerine doğrudan erişmek için .NET Framework sınıfları kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="52c1c-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>

## <a name="enumerations"></a><span data-ttu-id="52c1c-110">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="52c1c-110">Enumerations</span></span>

<span data-ttu-id="52c1c-111">Bu tablo, bir seri bağlantı noktasına erişmek için kullanılan ana numaralandırmaları listeler ve açıklar:</span><span class="sxs-lookup"><span data-stu-id="52c1c-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>

|<span data-ttu-id="52c1c-112">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="52c1c-112">Enumeration</span></span>|<span data-ttu-id="52c1c-113">Description</span><span class="sxs-lookup"><span data-stu-id="52c1c-113">Description</span></span>|
|---|---|
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="52c1c-114">Bir nesne için seri bağlantı noktası iletişimi kurarken kullanılan denetim protokolünü belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="52c1c-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="52c1c-115">Bir nesne için eşlik bitini belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="52c1c-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="52c1c-116">Nesnenin seri bağlantı noktasında alınan karakter türünü belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="52c1c-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="52c1c-117">Nesnede oluşan hataları belirtir <xref:System.IO.Ports.SerialPort></span><span class="sxs-lookup"><span data-stu-id="52c1c-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="52c1c-118">Nesnede gerçekleşen değişikliğin türünü belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="52c1c-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="52c1c-119">Nesnede kullanılan durdurma bitlerinin sayısını belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="52c1c-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|

## <a name="see-also"></a><span data-ttu-id="52c1c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52c1c-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="52c1c-121">Bilgisayar Bağlantı Noktalarına Erişme</span><span class="sxs-lookup"><span data-stu-id="52c1c-121">Accessing the Computer's Ports</span></span>](accessing-the-computer-s-ports.md)

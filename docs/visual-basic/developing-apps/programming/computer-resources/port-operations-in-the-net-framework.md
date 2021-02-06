---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic .NET Framework bağlantı noktası Işlemleri'
title: .NET Framework'te Bağlantı Noktası İşlemleri
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 072baac53589f8a5d6405eb786b4e692cbaf6181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641531"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="fe5f0-103">Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri</span><span class="sxs-lookup"><span data-stu-id="fe5f0-103">Port Operations in the .NET Framework with Visual Basic</span></span>

<span data-ttu-id="fe5f0-104">Ad alanındaki .NET Framework sınıfları aracılığıyla bilgisayarınızın seri bağlantı noktalarına erişebilirsiniz <xref:System.IO.Ports?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe5f0-104">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="fe5f0-105">En önemli sınıf, <xref:System.IO.Ports.SerialPort> zaman uyumlu ve olay odaklı g/ç için bir çerçeve, PIN ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe5f0-105">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="fe5f0-106"><xref:System.IO.Stream>Özelliği aracılığıyla erişilebilen bir nesneye kaydırılmış olabilir <xref:System.IO.Ports.SerialPort.BaseStream> .</span><span class="sxs-lookup"><span data-stu-id="fe5f0-106">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="fe5f0-107"><xref:System.IO.Ports.SerialPort>Bir nesne içine sarmalama <xref:System.IO.Stream> , seri bağlantı noktasına akışlar kullanan sınıflar tarafından erişilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="fe5f0-107">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="fe5f0-108">Ad alanı, seri bağlantı noktalarının denetimini kolaylaştıran numaralandırmalar içerir.</span><span class="sxs-lookup"><span data-stu-id="fe5f0-108">The namespace includes enumerations that simplify the control of serial ports.</span></span>

<span data-ttu-id="fe5f0-109">Bir nesne oluşturmanın en basit yolu <xref:System.IO.Ports.SerialPort> <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="fe5f0-109">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="fe5f0-110">Paralel bağlantı noktaları, USB bağlantı noktaları vb. gibi diğer bağlantı noktası türlerine doğrudan erişmek için .NET Framework sınıfları kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fe5f0-110">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>

## <a name="enumerations"></a><span data-ttu-id="fe5f0-111">Listelemeler</span><span class="sxs-lookup"><span data-stu-id="fe5f0-111">Enumerations</span></span>

<span data-ttu-id="fe5f0-112">Bu tablo, bir seri bağlantı noktasına erişmek için kullanılan ana numaralandırmaları listeler ve açıklar:</span><span class="sxs-lookup"><span data-stu-id="fe5f0-112">This table lists and describes the main enumerations used for accessing a serial port:</span></span>

|<span data-ttu-id="fe5f0-113">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="fe5f0-113">Enumeration</span></span>|<span data-ttu-id="fe5f0-114">Description</span><span class="sxs-lookup"><span data-stu-id="fe5f0-114">Description</span></span>|
|---|---|
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="fe5f0-115">Bir nesne için seri bağlantı noktası iletişimi kurarken kullanılan denetim protokolünü belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="fe5f0-115">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="fe5f0-116">Bir nesne için eşlik bitini belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="fe5f0-116">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="fe5f0-117">Nesnenin seri bağlantı noktasında alınan karakter türünü belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="fe5f0-117">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="fe5f0-118">Nesnede oluşan hataları belirtir <xref:System.IO.Ports.SerialPort></span><span class="sxs-lookup"><span data-stu-id="fe5f0-118">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="fe5f0-119">Nesnede gerçekleşen değişikliğin türünü belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="fe5f0-119">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="fe5f0-120">Nesnede kullanılan durdurma bitlerinin sayısını belirtir <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="fe5f0-120">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|

## <a name="see-also"></a><span data-ttu-id="fe5f0-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe5f0-121">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="fe5f0-122">Bilgisayar Bağlantı Noktalarına Erişme</span><span class="sxs-lookup"><span data-stu-id="fe5f0-122">Accessing the Computer's Ports</span></span>](accessing-the-computer-s-ports.md)

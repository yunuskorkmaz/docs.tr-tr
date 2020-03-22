---
title: .NET Framework'te Bağlantı Noktası İşlemleri
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 68f0c67b8135c6bb7ce8a134e2a324bc12c0aad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345513"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="32841-102">Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri</span><span class="sxs-lookup"><span data-stu-id="32841-102">Port Operations in the .NET Framework with Visual Basic</span></span>

<span data-ttu-id="32841-103">Bilgisayarınızın seri bağlantı noktalarına <xref:System.IO.Ports?displayProperty=nameWithType> ad alanındaki .NET Framework sınıfları aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32841-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="32841-104">En önemli sınıf, <xref:System.IO.Ports.SerialPort>senkron ve olay odaklı G/Ç, pin ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim için bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="32841-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="32841-105">Bir <xref:System.IO.Stream> nesneye sarılmış olabilir, <xref:System.IO.Ports.SerialPort.BaseStream> özellik üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="32841-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="32841-106">Bir <xref:System.IO.Ports.SerialPort> <xref:System.IO.Stream> nesneye kaydırma, seri bağlantı noktasına akışları kullanan sınıflar tarafından erişilmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="32841-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="32841-107">Ad alanı, seri bağlantı noktalarının denetimini basitleştiren sayısallaştırmalar içerir.</span><span class="sxs-lookup"><span data-stu-id="32841-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>

<span data-ttu-id="32841-108">Bir <xref:System.IO.Ports.SerialPort> nesne oluşturmanın en basit <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yolu yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="32841-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="32841-109">Paralel bağlantı noktaları, USB bağlantı noktaları gibi diğer bağlantı noktaları türlerine doğrudan erişmek için .NET Framework sınıflarını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="32841-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>

## <a name="enumerations"></a><span data-ttu-id="32841-110">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="32841-110">Enumerations</span></span>

<span data-ttu-id="32841-111">Bu tablo, seri bağlantı noktasına erişmek için kullanılan ana sayıları listeler ve açıklar:</span><span class="sxs-lookup"><span data-stu-id="32841-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>

|<span data-ttu-id="32841-112">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="32841-112">Enumeration</span></span>|<span data-ttu-id="32841-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32841-113">Description</span></span>|
|---|---|
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="32841-114">Bir nesne için seri bağlantı noktası iletişimi <xref:System.IO.Ports.SerialPort> oluştururken kullanılan denetim protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="32841-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="32841-115">Bir <xref:System.IO.Ports.SerialPort> nesne için eşlik bitini belirtir.</span><span class="sxs-lookup"><span data-stu-id="32841-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="32841-116"><xref:System.IO.Ports.SerialPort> Nesnenin seri bağlantı noktasında alınan karakter türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="32841-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="32841-117"><xref:System.IO.Ports.SerialPort> Nesneüzerinde oluşan hataları belirtir</span><span class="sxs-lookup"><span data-stu-id="32841-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="32841-118"><xref:System.IO.Ports.SerialPort> Nesne üzerinde oluşan değişiklik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="32841-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="32841-119"><xref:System.IO.Ports.SerialPort> Nesne üzerinde kullanılan durdurma bitlerinin sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="32841-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|

## <a name="see-also"></a><span data-ttu-id="32841-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32841-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="32841-121">Bilgisayar Bağlantı Noktalarına Erişme</span><span class="sxs-lookup"><span data-stu-id="32841-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

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
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri

Bilgisayarınızın seri bağlantı noktalarına <xref:System.IO.Ports?displayProperty=nameWithType> ad alanındaki .NET Framework sınıfları aracılığıyla erişebilirsiniz. En önemli sınıf, <xref:System.IO.Ports.SerialPort>senkron ve olay odaklı G/Ç, pin ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim için bir çerçeve sağlar. Bir <xref:System.IO.Stream> nesneye sarılmış olabilir, <xref:System.IO.Ports.SerialPort.BaseStream> özellik üzerinden erişilebilir. Bir <xref:System.IO.Ports.SerialPort> <xref:System.IO.Stream> nesneye kaydırma, seri bağlantı noktasına akışları kullanan sınıflar tarafından erişilmesine olanak tanır. Ad alanı, seri bağlantı noktalarının denetimini basitleştiren sayısallaştırmalar içerir.

Bir <xref:System.IO.Ports.SerialPort> nesne oluşturmanın en basit <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yolu yöntemdir.

> [!NOTE]
> Paralel bağlantı noktaları, USB bağlantı noktaları gibi diğer bağlantı noktaları türlerine doğrudan erişmek için .NET Framework sınıflarını kullanamazsınız.

## <a name="enumerations"></a>Numaralandırmalar

Bu tablo, seri bağlantı noktasına erişmek için kullanılan ana sayıları listeler ve açıklar:

|Sabit Listesi|Açıklama|
|---|---|
|<xref:System.IO.Ports.Handshake>|Bir nesne için seri bağlantı noktası iletişimi <xref:System.IO.Ports.SerialPort> oluştururken kullanılan denetim protokolünü belirtir.|
|<xref:System.IO.Ports.Parity>|Bir <xref:System.IO.Ports.SerialPort> nesne için eşlik bitini belirtir.|
|<xref:System.IO.Ports.SerialData>|<xref:System.IO.Ports.SerialPort> Nesnenin seri bağlantı noktasında alınan karakter türünü belirtir.|
|<xref:System.IO.Ports.SerialError>|<xref:System.IO.Ports.SerialPort> Nesneüzerinde oluşan hataları belirtir|
|<xref:System.IO.Ports.SerialPinChange>|<xref:System.IO.Ports.SerialPort> Nesne üzerinde oluşan değişiklik türünü belirtir.|
|<xref:System.IO.Ports.StopBits>|<xref:System.IO.Ports.SerialPort> Nesne üzerinde kullanılan durdurma bitlerinin sayısını belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Bilgisayar Bağlantı Noktalarına Erişme](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

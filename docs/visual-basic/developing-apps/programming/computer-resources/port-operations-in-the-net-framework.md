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
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri

Ad alanındaki .NET Framework sınıfları aracılığıyla bilgisayarınızın seri bağlantı noktalarına erişebilirsiniz <xref:System.IO.Ports?displayProperty=nameWithType> . En önemli sınıf, <xref:System.IO.Ports.SerialPort> zaman uyumlu ve olay odaklı g/ç için bir çerçeve, PIN ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim sağlar. <xref:System.IO.Stream>Özelliği aracılığıyla erişilebilen bir nesneye kaydırılmış olabilir <xref:System.IO.Ports.SerialPort.BaseStream> . <xref:System.IO.Ports.SerialPort>Bir nesne içine sarmalama <xref:System.IO.Stream> , seri bağlantı noktasına akışlar kullanan sınıflar tarafından erişilmesine izin verir. Ad alanı, seri bağlantı noktalarının denetimini kolaylaştıran numaralandırmalar içerir.

Bir nesne oluşturmanın en basit yolu <xref:System.IO.Ports.SerialPort> <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi kullanmaktır.

> [!NOTE]
> Paralel bağlantı noktaları, USB bağlantı noktaları vb. gibi diğer bağlantı noktası türlerine doğrudan erişmek için .NET Framework sınıfları kullanamazsınız.

## <a name="enumerations"></a>Numaralandırmalar

Bu tablo, bir seri bağlantı noktasına erişmek için kullanılan ana numaralandırmaları listeler ve açıklar:

|Sabit Listesi|Description|
|---|---|
|<xref:System.IO.Ports.Handshake>|Bir nesne için seri bağlantı noktası iletişimi kurarken kullanılan denetim protokolünü belirtir <xref:System.IO.Ports.SerialPort> .|
|<xref:System.IO.Ports.Parity>|Bir nesne için eşlik bitini belirtir <xref:System.IO.Ports.SerialPort> .|
|<xref:System.IO.Ports.SerialData>|Nesnenin seri bağlantı noktasında alınan karakter türünü belirtir <xref:System.IO.Ports.SerialPort> .|
|<xref:System.IO.Ports.SerialError>|Nesnede oluşan hataları belirtir <xref:System.IO.Ports.SerialPort>|
|<xref:System.IO.Ports.SerialPinChange>|Nesnede gerçekleşen değişikliğin türünü belirtir <xref:System.IO.Ports.SerialPort> .|
|<xref:System.IO.Ports.StopBits>|Nesnede kullanılan durdurma bitlerinin sayısını belirtir <xref:System.IO.Ports.SerialPort> .|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Bilgisayar Bağlantı Noktalarına Erişme](accessing-the-computer-s-ports.md)

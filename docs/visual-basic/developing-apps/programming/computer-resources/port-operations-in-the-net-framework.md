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

<xref:System.IO.Ports?displayProperty=nameWithType> Ad alanındaki .NET Framework sınıfları aracılığıyla bilgisayarınızın seri bağlantı noktalarına erişebilirsiniz. En önemli sınıf <xref:System.IO.Ports.SerialPort>, zaman uyumlu ve olay odaklı g/ç için bir çerçeve, PIN ve kesme durumlarına erişim ve seri sürücü özelliklerine erişim sağlar. <xref:System.IO.Ports.SerialPort.BaseStream> Özelliği aracılığıyla erişilebilen bir <xref:System.IO.Stream> nesneye kaydırılmış olabilir. Bir <xref:System.IO.Ports.SerialPort> <xref:System.IO.Stream> nesne içine sarmalama, seri bağlantı noktasına akışlar kullanan sınıflar tarafından erişilmesine izin verir. Ad alanı, seri bağlantı noktalarının denetimini kolaylaştıran numaralandırmalar içerir.

Bir <xref:System.IO.Ports.SerialPort> nesne oluşturmanın en basit yolu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi kullanmaktır.

> [!NOTE]
> Paralel bağlantı noktaları, USB bağlantı noktaları vb. gibi diğer bağlantı noktası türlerine doğrudan erişmek için .NET Framework sınıfları kullanamazsınız.

## <a name="enumerations"></a>Numaralandırmalar

Bu tablo, bir seri bağlantı noktasına erişmek için kullanılan ana numaralandırmaları listeler ve açıklar:

|Sabit Listesi|Açıklama|
|---|---|
|<xref:System.IO.Ports.Handshake>|Bir <xref:System.IO.Ports.SerialPort> nesne için seri bağlantı noktası iletişimi kurarken kullanılan denetim protokolünü belirtir.|
|<xref:System.IO.Ports.Parity>|Bir <xref:System.IO.Ports.SerialPort> nesne için eşlik bitini belirtir.|
|<xref:System.IO.Ports.SerialData>|<xref:System.IO.Ports.SerialPort> Nesnenin seri bağlantı noktasında alınan karakter türünü belirtir.|
|<xref:System.IO.Ports.SerialError>|<xref:System.IO.Ports.SerialPort> Nesnede oluşan hataları belirtir|
|<xref:System.IO.Ports.SerialPinChange>|<xref:System.IO.Ports.SerialPort> Nesnede gerçekleşen değişikliğin türünü belirtir.|
|<xref:System.IO.Ports.StopBits>|<xref:System.IO.Ports.SerialPort> Nesnede kullanılan durdurma bitlerinin sayısını belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Bilgisayar Bağlantı Noktalarına Erişme](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

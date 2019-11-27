---
title: .NET Framework'te Bağlantı Noktası İşlemleri
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 68f0c67b8135c6bb7ce8a134e2a324bc12c0aad9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345513"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri

<xref:System.IO.Ports?displayProperty=nameWithType> ad alanındaki .NET Framework sınıfları aracılığıyla bilgisayarınızın seri bağlantı noktalarına erişebilirsiniz. <xref:System.IO.Ports.SerialPort>en önemli sınıfı, zaman uyumlu ve olay odaklı g/ç için bir çerçeve sağlar, PIN ve kesme durumlarına erişebilir ve seri sürücü özelliklerine erişebilir. <xref:System.IO.Ports.SerialPort.BaseStream> özelliği aracılığıyla erişilebilen bir <xref:System.IO.Stream> nesnesine kaydırılmış olabilir. Bir <xref:System.IO.Stream> nesnesinde sarmalama <xref:System.IO.Ports.SerialPort>, akış kullanan sınıflar tarafından seri bağlantı noktasına erişilmesine izin verir. Ad alanı, seri bağlantı noktalarının denetimini kolaylaştıran numaralandırmalar içerir.

<xref:System.IO.Ports.SerialPort> nesne oluşturmanın en kolay yolu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi kullanmaktır.

> [!NOTE]
> Paralel bağlantı noktaları, USB bağlantı noktaları vb. gibi diğer bağlantı noktası türlerine doğrudan erişmek için .NET Framework sınıfları kullanamazsınız.

## <a name="enumerations"></a>Numaralandırmalar

Bu tablo, bir seri bağlantı noktasına erişmek için kullanılan ana numaralandırmaları listeler ve açıklar:

|Sabit Listesi|Açıklama|
|---|---|
|<xref:System.IO.Ports.Handshake>|<xref:System.IO.Ports.SerialPort> nesnesi için seri bağlantı noktası iletişimi kurarken kullanılan denetim protokolünü belirtir.|
|<xref:System.IO.Ports.Parity>|<xref:System.IO.Ports.SerialPort> nesne için eşlik bitini belirtir.|
|<xref:System.IO.Ports.SerialData>|<xref:System.IO.Ports.SerialPort> nesnesinin seri bağlantı noktasında alınan karakter türünü belirtir.|
|<xref:System.IO.Ports.SerialError>|<xref:System.IO.Ports.SerialPort> nesnesinde oluşan hataları belirtir|
|<xref:System.IO.Ports.SerialPinChange>|<xref:System.IO.Ports.SerialPort> nesnesinde gerçekleşen değişikliğin türünü belirtir.|
|<xref:System.IO.Ports.StopBits>|<xref:System.IO.Ports.SerialPort> nesnesinde kullanılan durdurma bitlerinin sayısını belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Bilgisayar Bağlantı Noktalarına Erişme](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

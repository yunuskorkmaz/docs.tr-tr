---
title: Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 10488f896ff7c6761e831d2a8af52249a19cf7d6
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524389"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri

@No__t_0 ad alanındaki .NET Framework sınıfları aracılığıyla bilgisayarınızın seri bağlantı noktalarına erişebilirsiniz. @No__t_0 en önemli sınıfı, zaman uyumlu ve olay odaklı g/ç için bir çerçeve sağlar, PIN ve kesme durumlarına erişebilir ve seri sürücü özelliklerine erişebilir. @No__t_1 özelliği aracılığıyla erişilebilen bir <xref:System.IO.Stream> nesnesine kaydırılmış olabilir. Bir <xref:System.IO.Stream> nesnesinde sarmalama <xref:System.IO.Ports.SerialPort>, akış kullanan sınıflar tarafından seri bağlantı noktasına erişilmesine izin verir. Ad alanı, seri bağlantı noktalarının denetimini kolaylaştıran numaralandırmalar içerir.

@No__t_0 nesne oluşturmanın en kolay yolu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi kullanmaktır.

> [!NOTE]
> Paralel bağlantı noktaları, USB bağlantı noktaları vb. gibi diğer bağlantı noktası türlerine doğrudan erişmek için .NET Framework sınıfları kullanamazsınız.

## <a name="enumerations"></a>Numaralandırmalar

Bu tablo, bir seri bağlantı noktasına erişmek için kullanılan ana numaralandırmaları listeler ve açıklar:

|Sabit Listesi|Açıklama|
|---|---|
|<xref:System.IO.Ports.Handshake>|@No__t_0 nesnesi için seri bağlantı noktası iletişimi kurarken kullanılan denetim protokolünü belirtir.|
|<xref:System.IO.Ports.Parity>|@No__t_0 nesne için eşlik bitini belirtir.|
|<xref:System.IO.Ports.SerialData>|@No__t_0 nesnesinin seri bağlantı noktasında alınan karakter türünü belirtir.|
|<xref:System.IO.Ports.SerialError>|@No__t_0 nesnesinde oluşan hataları belirtir|
|<xref:System.IO.Ports.SerialPinChange>|@No__t_0 nesnesinde gerçekleşen değişikliğin türünü belirtir.|
|<xref:System.IO.Ports.StopBits>|@No__t_0 nesnesinde kullanılan durdurma bitlerinin sayısını belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Bilgisayar Bağlantı Noktalarına Erişme](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

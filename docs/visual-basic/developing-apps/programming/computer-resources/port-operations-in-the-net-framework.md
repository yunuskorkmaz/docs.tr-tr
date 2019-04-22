---
title: Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 33298fd9840630fbfd6f7f9d883cc2397a459843
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826450"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri
Bilgisayarınızın seri bağlantı noktaları üzerinden erişebildiğiniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıfları <xref:System.IO.Ports?displayProperty=nameWithType> ad alanı. En önemli sınıfı <xref:System.IO.Ports.SerialPort>, zaman uyumlu ve olay odaklı g/ç, erişim için PIN ve kesme durumları ve seri sürücü özelliklere erişim için bir çerçeve sunar. İçinde sarmalanabilir bir <xref:System.IO.Stream> nesnesi üzerinden erişilebilir <xref:System.IO.Ports.SerialPort.BaseStream> özelliği. Sarmalama <xref:System.IO.Ports.SerialPort> içinde bir <xref:System.IO.Stream> nesne akışları kullanan sınıfları tarafından erişilecek seri bağlantı noktası sağlar. Ad alanı, seri bağlantı denetimi basitleştiren sabit listeleri içerir.  
  
 En basit yolu oluşturmak için bir <xref:System.IO.Ports.SerialPort> nesnedir aracılığıyla <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi.  
  
> [!NOTE]
>  Kullanamazsınız [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bağlantı noktaları, paralel bağlantı noktaları, USB bağlantı noktası vb. gibi diğer tür doğrudan erişmek için sınıflar.  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Bu tablo, listeler ve seri bağlantı noktası erişmek için kullanılan ana numaralandırmaları açıklar:  
  
|Sabit Listesi|Açıklama|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Bir seri bağlantı noktası iletişimi için oluşturmada kullanılan Denetim Protokolü belirtir bir <xref:System.IO.Ports.SerialPort> nesne.|  
|<xref:System.IO.Ports.Parity>|İçin eşlik biti belirtir bir <xref:System.IO.Ports.SerialPort> nesne.|  
|<xref:System.IO.Ports.SerialData>|Seri bağlantı noktasında alınan karakter türünü belirtir <xref:System.IO.Ports.SerialPort> nesne.|  
|<xref:System.IO.Ports.SerialError>|Gerçekleşen hataları belirtir <xref:System.IO.Ports.SerialPort> nesnesi|  
|<xref:System.IO.Ports.SerialPinChange>|Üzerinde gerçekleşen değişiklik türünü belirtir <xref:System.IO.Ports.SerialPort> nesne.|  
|<xref:System.IO.Ports.StopBits>|Kullanılan Dur bitleri belirtir <xref:System.IO.Ports.SerialPort> nesne.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Bilgisayar Bağlantı Noktalarına Erişme](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

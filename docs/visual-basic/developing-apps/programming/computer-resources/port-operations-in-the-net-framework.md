---
title: Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 66b3729081540e8dede42556c58e44cd55b62666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584725"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri
Bilgisayarınızın seri bağlantı noktaları üzerinden erişebilirsiniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıfları <xref:System.IO.Ports?displayProperty=nameWithType> ad alanı. En önemli sınıfı <xref:System.IO.Ports.SerialPort>, zaman uyumlu ve olay denetimli g/ç, PIN ve sonu durumları erişimi ve seri sürücü özelliklerine erişimi için bir çerçeve sağlar. İçinde kaydırılan bir <xref:System.IO.Stream> nesnesi üzerinden erişilebilir <xref:System.IO.Ports.SerialPort.BaseStream> özelliği. Kaydırma <xref:System.IO.Ports.SerialPort> içinde bir <xref:System.IO.Stream> nesne akışları kullanan sınıfları tarafından erişilecek seri bağlantı noktası sağlar. Ad alanı, seri bağlantı noktaları denetim basitleştirmek numaralandırmalar içerir.  
  
 En basit yolu oluşturmak için bir <xref:System.IO.Ports.SerialPort> nesnesidir aracılığıyla <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi.  
  
> [!NOTE]
>  Kullanamazsınız [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] doğrudan bağlantı noktaları, paralel bağlantı noktaları, USB bağlantı noktaları vb. gibi diğer türleri erişmek için sınıflar.  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Bu tabloda listelenmekte ve seri bağlantı noktasına erişmek için kullanılan ana numaralandırmalar açıklanmaktadır:  
  
|Sabit Listesi|Açıklama|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Bir seri bağlantı noktası iletişimi için oluşturmada kullanılan Denetim Protokolü belirten bir <xref:System.IO.Ports.SerialPort> nesnesi.|  
|<xref:System.IO.Ports.Parity>|İçin eşlik biti belirten bir <xref:System.IO.Ports.SerialPort> nesnesi.|  
|<xref:System.IO.Ports.SerialData>|Seri bağlantı noktasında alınan karakter türünü belirtir <xref:System.IO.Ports.SerialPort> nesnesi.|  
|<xref:System.IO.Ports.SerialError>|Üzerinde oluşan hataları belirtir <xref:System.IO.Ports.SerialPort> nesnesi|  
|<xref:System.IO.Ports.SerialPinChange>|Oluştu değişiklik türünü belirtir <xref:System.IO.Ports.SerialPort> nesnesi.|  
|<xref:System.IO.Ports.StopBits>|Dur bitleri kullanılan sayısını belirtir <xref:System.IO.Ports.SerialPort> nesnesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [Bilgisayar Bağlantı Noktalarına Erişme](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)

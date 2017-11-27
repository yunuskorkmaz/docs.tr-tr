---
title: "Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95c67b344572d21f418cbc14d350e6ff28611bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme
Bu konuda nasıl kullanılacağını açıklar `My.Computer.Ports` bilgisayarın seri bağlantı noktalarına dizeler gönderme için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dize COM1 seri bağlantı noktasına gönderir. Bilgisayarınızda farklı bir seri bağlantı noktası kullanmanız gerekebilir.  
  
 Kullanım `My.Computer.Ports.OpenSerialPort` bir başvuru noktasına elde etmek için yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using` Bloğu bir özel durum oluşturursa bile seri bağlantı noktasını kapatmak uygulama izin verir. Seri bağlantı noktası yöneten tüm kod bu bloğu içinde veya içinde görünmesi gereken bir `Try...Catch...Finally` bloğu.  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> Yöntemi verileri seri bağlantı noktasına gönderir.  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örnek kullandığınızı varsayar `COM1`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek kullandığınızı varsayar `COM1`; daha fazla esneklik için kod istenilen seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçmek kullanıcı sağlamalıdır. Daha fazla bilgi için bkz: [nasıl yapılır: kullanılabilir seri bağlantı noktalarını göster](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnekte bir `Using` bloğu bir özel durum oluşturursa bile uygulama bağlantı noktasını kapatır emin olun. Daha fazla bilgi için bkz: [kullanarak deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Nasıl yapılır: seri bağlantı noktalarına ekli modemleri çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

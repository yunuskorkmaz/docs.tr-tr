---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: b2051451142a7818a3b7d1bc564c5ae36b2579fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345581"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme

Bu konu, Visual `My.Computer.Ports` Basic'te bilgisayarın seri bağlantı noktalarına dizeleri göndermek için nasıl kullanılacağını açıklar.  
  
## <a name="example"></a>Örnek  

 Bu örnek, COM1 seri bağlantı noktasına bir dize gönderir. Bilgisayarınızda farklı bir seri bağlantı noktası kullanmanız gerekebilir.  
  
 Bağlantı `My.Computer.Ports.OpenSerialPort` noktasına başvuruda bulunulmak için yöntemi kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 Blok, `Using` bir özel durum oluştursa bile uygulamanın seri bağlantı noktasını kapatmasına olanak tanır. Seri bağlantı noktasını işleyen tüm kodbu blok `Try...Catch...Finally` içinde veya bir blok içinde görünmelidir.  
  
 Yöntem <xref:System.IO.Ports.SerialPort.WriteLine%2A> verileri seri bağlantı noktasına gönderir.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bu örnek, bilgisayarın kullandığını `COM1`varsayar.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnek, bilgisayarın kullandığını `COM1`varsayar; daha fazla esneklik için, kod kullanıcıkullanılabilir bağlantı noktaları listesinden istenen seri bağlantı noktasını seçmek için izin vermelidir. Daha fazla bilgi için [bkz: Kullanılabilir Seri Bağlantı Noktalarını Göster.](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)  
  
 Bu örnek, `Using` bir özel durum atsa bile uygulamanın bağlantı noktasını kapattıklarından emin olmak için bir blok kullanır. Daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/statements/using-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

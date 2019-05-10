---
title: "Nasıl yapılır: Visual Basic'te seri bağlantı noktalarına dizeler gönderme"
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: 66f7d0b51e51f6d550a42cca55b3194c2e273969
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662723"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te seri bağlantı noktalarına dizeler gönderme
Bu konu nasıl kullanılacağını açıklar `My.Computer.Ports` bilgisayarın Visual Basic'te seri bağlantı noktalarına dizeler gönderme için.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dize COM1 seri bağlantı noktasına gönderir. Bilgisayarınızda başka bir seri bağlantı noktası kullanmanız gerekebilir.  
  
 Kullanım `My.Computer.Ports.OpenSerialPort` bağlantı noktasına bir başvuru almak için yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using` Blok bile bir özel durum oluşturur seri bağlantı noktası kapatmak uygulama izin verir. Seri bağlantı noktası yöneten tüm kod gözükeceğini bu blok içinde veya içinde bir `Try...Catch...Finally` blok.  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> Yöntemi verileri seri bağlantı noktasına gönderir.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bu örnek kullandığınızı varsayar `COM1`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek kullandığınızı varsayar `COM1`; daha fazla esneklik için kodu kullanıcının istenen seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçmesini izin vermelidir. Daha fazla bilgi için [nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnekte bir `Using` bir özel durum oluşturursa bile uygulama bağlantı noktasını kapatır emin olmak için blok. Daha fazla bilgi için [Using deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl yapılır: Seri bağlantı noktalarına ekli modemleri çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

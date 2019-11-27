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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345581"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme

Bu konuda, Visual Basic bilgisayarın seri bağlantı noktalarına dizeler göndermek için `My.Computer.Ports` nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="example"></a>Örnek  

 Bu örnekte, COM1 seri bağlantı noktasına bir dize gönderilir. Bilgisayarınızda farklı bir seri bağlantı noktası kullanmanız gerekebilir.  
  
 Bağlantı noktasına bir başvuru almak için `My.Computer.Ports.OpenSerialPort` metodunu kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using` bloğu, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar. Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde veya `Try...Catch...Finally` bloğu içinde görünmelidir.  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> yöntemi, verileri seri bağlantı noktasına gönderir.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- Bu örnek, bilgisayarın `COM1`kullandığını varsayar.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnek, bilgisayarın `COM1`kullandığını varsayar; daha fazla esneklik için, kod kullanıcının kullanılabilir bağlantı noktası listesinden istenen seri bağlantı noktasını seçmesine izin verir. Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnek, bir özel durum oluşturursa bile uygulamanın bağlantı noktasını kapatdığından emin olmak için bir `Using` bloğu kullanır. Daha fazla bilgi için bkz. [using deyimleri](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

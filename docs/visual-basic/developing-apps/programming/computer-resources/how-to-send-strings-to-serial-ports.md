---
title: 'Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: f78df9cf1bd75432ea645c4dcc06498915ceee49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360299"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme

Bu konuda `My.Computer.Ports` , Visual Basic bilgisayarın seri bağlantı noktalarına dize göndermek için nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="example"></a>Örnek  

 Bu örnekte, COM1 seri bağlantı noktasına bir dize gönderilir. Bilgisayarınızda farklı bir seri bağlantı noktası kullanmanız gerekebilir.  
  
 `My.Computer.Ports.OpenSerialPort`Bağlantı noktasına bir başvuru almak için yöntemini kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using`Blok, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar. Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde veya bir blok içinde görünmelidir `Try...Catch...Finally` .  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A>Yöntemi, verileri seri bağlantı noktasına gönderir.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bu örnekte, bilgisayarın kullandığı varsayılır `COM1` .  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnekte, bilgisayarın kullandığı varsayılmaktadır `COM1` ; daha fazla esneklik için, kodun kullanılabilir bağlantı noktası listesinden istenen seri bağlantı noktasını seçmesine izin verilmelidir. Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](how-to-show-available-serial-ports.md).  
  
 Bu örnek, bir `Using` özel durum oluşturursa uygulamanın bağlantı noktasını kapatdığından emin olmak için bir bloğu kullanır. Daha fazla bilgi için bkz. [using deyimleri](../../../language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](how-to-show-available-serial-ports.md)

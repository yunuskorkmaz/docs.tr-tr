---
title: "Nasıl yapılır: Visual Basic'te seri bağlantı noktalarından dize alma"
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: f87ff7e621d241a94dae444bc156502ee86b36b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521614"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te seri bağlantı noktalarından dize alma
Bu konu nasıl kullanılacağını açıklar `My.Computer.Ports` bilgisayarın Visual Basic'te seri bağlantı noktalarından dize alma için.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Seri bağlantı noktasından dizelerini almak için  
  
1.  Dönüş dizesini başlatır.  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  Hangi seri bağlantı dizeleri sağlamalıdır belirleyin. Bu örnekte olduğu varsayılır `COM1`.  
  
3.  Kullanım `My.Computer.Ports.OpenSerialPort` bağlantı noktasına bir başvuru almak için yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` Blok bile bir özel durum oluşturur seri bağlantı noktası kapatmak uygulama izin verir. Seri bağlantı noktası yöneten tüm kod bu blok içinde görüntülenmesi gerekir.  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  Oluşturma bir `Do` satırlık metin okuma için daha fazla satır kullanılabilir olana kadar döngü.  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  Kullanım <xref:System.IO.Ports.SerialPort.ReadLine> metin kullanılabilen bir sonraki satıra seri bağlantı noktasından okumak için yöntem.  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  Kullanım bir `If` belirlemek için deyimi <xref:System.IO.Ports.SerialPort.ReadLine> yöntemi döndürür `Nothing` (yani daha fazla metin kullanılabilir). Dönüş yaparsa `Nothing`, çıkış `Do` döngü.  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  Ekleme bir `Else` bloğunu `If` dize gerçekten salt okunur ise, durumu işlemek için deyimi. Blok seri bağlantı dizesinden dönüş dizesine ekler.  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  Dizeyi döndürür.  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **bağlantı ve ağ**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek kullandığınızı varsayar `COM1`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek kullandığınızı varsayar `COM1`. Daha fazla esneklik için kodu, kullanıcının istenen seri bağlantı noktası kullanılabilir bağlantı noktaları bir listesinden seçmek izin vermelidir. Daha fazla bilgi için [nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnekte bir `Try...Catch...Finally` uygulama bağlantı noktasını kapatır emin olun ve herhangi bir zaman aşımı özel durumları yakalama bloğu. Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl yapılır: Seri bağlantı noktalarına ekli modemleri çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl yapılır: Seri bağlantı noktalarına dizeler gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

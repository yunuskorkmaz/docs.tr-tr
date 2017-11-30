---
title: "Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6939dee58051e9a97fa704f063f35ff0ac440036
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma
Bu konuda nasıl kullanılacağını açıklar `My.Computer.Ports` içinde bilgisayarın seri bağlantı noktalarından dize alma için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Seri bağlantı noktasından dizeleri almak için  
  
1.  Dönüş dizesini başlatır.  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  Hangi seri bağlantı dizeleri sağlamalıdır belirler. Bu örnekte olduğu varsayılır `COM1`.  
  
3.  Kullanım `My.Computer.Ports.OpenSerialPort` bir başvuru noktasına elde etmek için yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` Bloğu bir özel durum oluşturursa bile seri bağlantı noktasını kapatmak uygulama izin verir. Seri bağlantı noktası yöneten tüm kod bu blokta görüntülenmesi gerekir.  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  Oluşturma bir `Do` daha fazla satır kullanılabilir oluncaya kadar satırlık metin okumak için döngü.  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  Kullanım <xref:System.IO.Ports.SerialPort.ReadLine%2A> metnin kullanılabilen bir sonraki satıra seri bağlantı noktasından okumak için yöntem.  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  Kullanım bir `If` belirlemek için deyimi <xref:System.IO.Ports.SerialPort.ReadLine%2A> yöntemi döndürür `Nothing` (daha fazla metin başka bir deyişle, kullanılabilir). Bunu döndürürse `Nothing`, çıkış `Do` döngü.  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  Ekleme bir `Else` için engelleyin `If` dize gerçekte salt okunur ise durumu işlemek için deyimi. Blok seri bağlantı noktasından dizesi Dönüş dizesi olarak ekler.  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  Dize döndürür.  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **bağlantısı ve ağ**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek kullandığınızı varsayar `COM1`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek kullandığınızı varsayar `COM1`. Daha fazla esneklik için kod kullanıcının istenen seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçmesine izin vermelidir. Daha fazla bilgi için bkz: [nasıl yapılır: kullanılabilir seri bağlantı noktalarını göster](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnekte bir `Try...Catch...Finally` blok uygulama bağlantı noktasını kapatır emin olmak ve hiçbir zaman aşımı özel durumları yakalamak için. Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Nasıl yapılır: seri bağlantı noktalarına ekli modemleri çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Nasıl yapılır: seri bağlantı noktalarına dizeler gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [Nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

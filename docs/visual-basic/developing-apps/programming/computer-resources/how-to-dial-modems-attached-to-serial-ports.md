---
title: "Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Ekli Modemleri Çevirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea1b2d6152af8919ac1aa272def4ba198b33867c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Ekli Modemleri Çevirme
Bu konuda nasıl kullanılacağını açıklar `My.Computer.Ports` modem çevrilecek [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Genellikle, bilgisayardaki seri bağlantı noktalarından birine modem bağlı. Modem ile iletişim kurmak, uygulamanız için uygun seri bağlantı noktasına komutları göndermeniz gerekir.  
  
### <a name="to-dial-a-modem"></a>Modem aramak için  
  
1.  Modem bağlı hangi seri bağlantı noktası belirleyin. Bu örnek, COM1 üzerindeki modem olduğunu varsayar.  
  
2.  Kullanım `My.Computer.Ports.OpenSerialPort` bir başvuru noktasına elde etmek için yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using` Bloğu bir özel durum oluşturursa bile seri bağlantı noktasını kapatmak uygulama izin verir. Seri bağlantı noktası yöneten tüm kod bu bloğu içinde veya içinde görünmesi gereken bir `Try...Catch...Finally` bloğu.  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  Ayarlama `DtrEnable` bilgisayarın modemden gelen bir aktarımını kabul etmeye hazır olduğunu belirtmek için özelliği.  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  Arama komut ve telefon numarası yoluyla seri bağlantı noktası üzerinden modem göndermek <xref:System.IO.Ports.SerialPort.Write%2A> yöntemi.  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **bağlantısı ve ağ**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek, başvuru gerektirir <xref:System?displayProperty=nameWithType> ad alanı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnekte, modem COM1'e bağlı olduğu varsayılır. Kodunuzu kullanıcının istenen seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçmesine izin öneririz. Daha fazla bilgi için bkz: [nasıl yapılır: kullanılabilir seri bağlantı noktalarını göster](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnekte bir `Using` bloğu bir özel durum oluşturursa bile uygulama bağlantı noktasını kapatır emin olun. Daha fazla bilgi için bkz: [kullanarak deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 Bu örnekte, modem çevirir sonra uygulama seri bağlantı noktası bağlantısını keser. Gerçekçi olarak, modem gelen ve giden veri aktarımı isteyeceksiniz. Daha fazla bilgi için bkz: [nasıl yapılır: alma dizeleri öğesinden seri bağlantı noktaları](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Nasıl yapılır: seri bağlantı noktalarına dizeler gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [Nasıl yapılır: seri bağlantı noktalarından dize alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 [Nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

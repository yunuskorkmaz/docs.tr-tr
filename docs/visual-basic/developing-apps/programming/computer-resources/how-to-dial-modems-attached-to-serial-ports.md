---
title: "Nasıl yapılır: Visual Basic'te seri bağlantı noktalarına ekli modemleri çevirme"
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: db482af7750012d8805d4f834063a2c82224cf67
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014004"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te seri bağlantı noktalarına ekli modemleri çevirme
Bu konu nasıl kullanılacağını açıklar `My.Computer.Ports` Visual Basic'te bir modem çevirmek için.  
  
 Genellikle, bilgisayardaki seri bağlantı noktalarından birine modem bağlı. Modem ile iletişim kurmak, uygulamanız için uygun bir seri bağlantı noktasına komutları göndermeniz gerekir.  
  
### <a name="to-dial-a-modem"></a>Modem aramak için  
  
1. Modem bağlı hangi seri bağlantı noktası belirleyin. Bu örnekte, COM1 üzerinde modem olduğunu varsayar.  
  
2. Kullanım `My.Computer.Ports.OpenSerialPort` bağlantı noktasına bir başvuru almak için yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using` Blok bile bir özel durum oluşturur seri bağlantı noktası kapatmak uygulama izin verir. Seri bağlantı noktası yöneten tüm kod gözükeceğini bu blok içinde veya içinde bir `Try...Catch...Finally` blok.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Ayarlama `DtrEnable` bilgisayar modemden gelen bir iletim kabul etmeye hazır olduğunu belirtmek için özelliği.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Modem ile seri bağlantı noktası aracılığıyla arama komut ve telefon numarası göndermek <xref:System.IO.Ports.SerialPort.Write%2A> yöntemi.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **bağlantı ve ağ**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek, bir başvuru gerektirir <xref:System?displayProperty=nameWithType> ad alanı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnekte, modem COM1'e bağlı olduğu varsayılır. Kodunuzu istenen seri bağlantı noktası kullanılabilir bağlantı noktaları bir listesinden seçmek kullanıcı izin öneririz. Daha fazla bilgi için [nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnekte bir `Using` bir özel durum oluşturursa bile uygulama bağlantı noktasını kapatır emin olmak için blok. Daha fazla bilgi için [Using deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 Bu örnekte, uygulama modem çevirir sonra seri bağlantı noktası bağlantısını keser. Gerçekçi olarak, modem gelen ve giden veri aktarımı isteyeceksiniz. Daha fazla bilgi için [nasıl yapılır: Seri bağlantı noktalarından dize alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl yapılır: Seri bağlantı noktalarına dizeler gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl yapılır: Seri bağlantı noktalarından dize alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

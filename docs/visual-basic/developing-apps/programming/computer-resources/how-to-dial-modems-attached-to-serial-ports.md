---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345635"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Ekli Modemleri Çevirme

Bu konu, Visual `My.Computer.Ports` Basic'te modem çevirmek için nasıl kullanılacağını açıklar.  
  
 Genellikle modem, bilgisayardaki seri bağlantı noktalarından birine bağlanır. Uygulamanızın modemle iletişim kurabilmesi için komutları uygun seri bağlantı noktasına göndermesi gerekir.  
  
### <a name="to-dial-a-modem"></a>Modemi çevirmek için  
  
1. Modemin hangi seri bağlantı noktasına bağlı olduğunu belirleyin. Bu örnek, modem COM1 üzerinde olduğunu varsayar.  
  
2. Bağlantı `My.Computer.Ports.OpenSerialPort` noktasına başvuruda bulunulmak için yöntemi kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Blok, `Using` bir özel durum oluştursa bile uygulamanın seri bağlantı noktasını kapatmasına olanak tanır. Seri bağlantı noktasını işleyen tüm kodbu blok içinde `Try...Catch...Finally` veya bir blok içinde görünmelidir.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Bilgisayarın `DtrEnable` modemden gelen bir aktarımı kabul etmeye hazır olduğunu belirtmek için özelliği ayarlayın.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <xref:System.IO.Ports.SerialPort.Write%2A> Arama komutunu ve telefon numarasını yöntem le seri bağlantı noktası üzerinden modeme gönderin.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet toplayıcı, **bağlantı ve ağ**bulunmaktadır. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnek, <xref:System?displayProperty=nameWithType> ad alanına bir başvuru gerektirir.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnek, modemcom1 bağlı olduğunu varsayar. Kodunuzun, kullanıcının kullanılabilir bağlantı noktaları listesinden istenen seri bağlantı noktasını seçmesine izin vermesini öneririz. Daha fazla bilgi için [bkz: Kullanılabilir Seri Bağlantı Noktalarını Göster.](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)  
  
 Bu örnek, `Using` bir özel durum atsa bile uygulamanın bağlantı noktasını kapattıklarından emin olmak için bir blok kullanır. Daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/statements/using-statement.md)  
  
 Bu örnekte, uygulama modemi çevirdikten sonra seri bağlantı noktasını keser. Gerçekçi olmak gerekirse, modeme ve modemden veri aktarmak isteyeceksiniz. Daha fazla bilgi için [bkz: Seri Bağlantı Noktalarından Dizeleri Alma.](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

---
title: 'Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme'
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

Bu konu başlığı altında, Visual Basic `My.Computer.Ports` bir modem aramak için nasıl kullanılacağı açıklanmaktadır.  
  
 Genellikle, modem bilgisayardaki seri bağlantı noktalarından birine bağlanır. Uygulamanızın modemle iletişim kurması için uygun seri bağlantı noktasına komut göndermelidir.  
  
### <a name="to-dial-a-modem"></a>Modem aramak için  
  
1. Modemin bağlandığı seri bağlantı noktasını belirleme. Bu örnek, modemin COM1 üzerinde olduğunu varsayar.  
  
2. Bağlantı noktasına `My.Computer.Ports.OpenSerialPort` bir başvuru almak için yöntemini kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using` Blok, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar. Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde veya bir `Try...Catch...Finally` blok içinde görünmelidir.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. `DtrEnable` Özelliği, bilgisayarın modemden gelen bir iletimi kabul etmeye hazırlandığını belirtecek şekilde ayarlayın.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Arama komutunu ve telefon numarasını, <xref:System.IO.Ports.SerialPort.Write%2A> yöntemi aracılığıyla seri bağlantı noktası üzerinden modeme gönderin.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnek <xref:System?displayProperty=nameWithType> ad alanına bir başvuru gerektirir.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnek, modemin COM1 'ya bağlı olduğunu varsayar. Kodunuzun, kullanıcının kullanılabilir bağlantı noktaları listesinden istenen seri bağlantı noktasını seçmesine izin vermeyi öneririz. Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnek, bir `Using` özel durum oluşturursa uygulamanın bağlantı noktasını kapatdığından emin olmak için bir bloğu kullanır. Daha fazla bilgi için bkz. [using deyimleri](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 Bu örnekte, uygulama, modemi çevirdikten sonra seri bağlantı noktasının bağlantısını keser. Gerçekçi olarak, modemden veya modemden veri aktarmak isteyeceksiniz. Daha fazla bilgi için bkz. [nasıl yapılır: seri bağlantı noktalarından dize alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl yapılır: Seri Bağlantı Noktalarından Dize Alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

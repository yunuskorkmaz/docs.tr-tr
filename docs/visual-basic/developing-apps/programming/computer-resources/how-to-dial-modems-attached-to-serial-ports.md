---
title: 'Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: e55ce6399dae435fbd5b2f730d4d0848c98d8955
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363273"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Ekli Modemleri Çevirme

Bu konu başlığı `My.Computer.Ports` altında, Visual Basic bir modem aramak için nasıl kullanılacağı açıklanmaktadır.  
  
 Genellikle, modem bilgisayardaki seri bağlantı noktalarından birine bağlanır. Uygulamanızın modemle iletişim kurması için uygun seri bağlantı noktasına komut göndermelidir.  
  
### <a name="to-dial-a-modem"></a>Modem aramak için  
  
1. Modemin bağlandığı seri bağlantı noktasını belirleme. Bu örnek, modemin COM1 üzerinde olduğunu varsayar.  
  
2. `My.Computer.Ports.OpenSerialPort`Bağlantı noktasına bir başvuru almak için yöntemini kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using`Blok, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar. Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde veya bir blok içinde görünmelidir `Try...Catch...Finally` .  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Özelliği, `DtrEnable` bilgisayarın modemden gelen bir iletimi kabul etmeye hazırlandığını belirtecek şekilde ayarlayın.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Arama komutunu ve telefon numarasını, yöntemi aracılığıyla seri bağlantı noktası üzerinden modeme gönderin <xref:System.IO.Ports.SerialPort.Write%2A> .  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnek ad alanına bir başvuru gerektirir <xref:System?displayProperty=nameWithType> .  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnek, modemin COM1 'ya bağlı olduğunu varsayar. Kodunuzun, kullanıcının kullanılabilir bağlantı noktaları listesinden istenen seri bağlantı noktasını seçmesine izin vermeyi öneririz. Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](how-to-show-available-serial-ports.md).  
  
 Bu örnek, bir `Using` özel durum oluşturursa uygulamanın bağlantı noktasını kapatdığından emin olmak için bir bloğu kullanır. Daha fazla bilgi için bkz. [using deyimleri](../../../language-reference/statements/using-statement.md).  
  
 Bu örnekte, uygulama, modemi çevirdikten sonra seri bağlantı noktasının bağlantısını keser. Gerçekçi olarak, modemden veya modemden veri aktarmak isteyeceksiniz. Daha fazla bilgi için bkz. [nasıl yapılır: seri bağlantı noktalarından dize alma](how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](how-to-send-strings-to-serial-ports.md)
- [Nasıl yapılır: Seri Bağlantı Noktalarından Dize Alma](how-to-receive-strings-from-serial-ports.md)
- [Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](how-to-show-available-serial-ports.md)

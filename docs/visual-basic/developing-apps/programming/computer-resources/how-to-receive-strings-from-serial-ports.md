---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345592"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma

Bu konuda, Visual Basic bilgisayarın seri bağlantı noktalarından dizeler almak için `My.Computer.Ports` nasıl kullanılacağı açıklanmaktadır.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Seri bağlantı noktasından dizeler almak için  
  
1. Dönüş dizesini başlatın.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. Dizelerin hangi seri bağlantı noktası tarafından sağlanması gerektiğini saptayın. Bu örnek `COM1`olduğunu varsayar.  
  
3. Bağlantı noktasına bir başvuru almak için `My.Computer.Ports.OpenSerialPort` metodunu kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` bloğu, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar. Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde görünmelidir.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. Daha fazla satır kullanılamadığından metin satırlarını okumak için bir `Do` döngüsü oluşturun.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. Seri bağlantı noktasından sonraki kullanılabilir metin satırını okumak için <xref:System.IO.Ports.SerialPort.ReadLine> yöntemini kullanın.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <xref:System.IO.Ports.SerialPort.ReadLine> yönteminin `Nothing` döndürüp döndürmediğine (daha fazla metin kullanılamadığı anlamına gelir) `If` bir ifade kullanın. `Nothing`döndürmesi durumunda `Do` döngüsünden çıkın.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. Dize gerçekten okuneyse, durumu işlemek için `If` ifadesine `Else` bloğu ekleyin. Blok, dizeyi seri bağlantı noktasından dönüş dizesine ekler.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. Dizeyi döndürür.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleme  

 Bu örnek, bilgisayarın `COM1`kullandığını varsayar.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnek, bilgisayarın `COM1`kullandığını varsayar. Daha fazla esneklik için, kod kullanıcının kullanılabilir bağlantı noktası listesinden istenen seri bağlantı noktasını seçmesine izin verir. Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnek, uygulamanın bağlantı noktasını kapatıp zaman aşımı özel durumlarını yakalamada emin olmak için bir `Try...Catch...Finally` bloğu kullanır. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

---
title: 'Nasıl yapılır: Seri Bağlantı Noktalarından Dize Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345592"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma

Bu konu başlığı altında, bilgisayarın `My.Computer.Ports` seri bağlantı noktalarından Visual Basic dize almak için nasıl kullanılacağı açıklanmaktadır.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Seri bağlantı noktasından dizeler almak için  
  
1. Dönüş dizesini başlatın.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. Dizelerin hangi seri bağlantı noktası tarafından sağlanması gerektiğini saptayın. Bu örnek, `COM1`olduğunu varsayar.  
  
3. Bağlantı noktasına `My.Computer.Ports.OpenSerialPort` bir başvuru almak için yöntemini kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` Blok, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar. Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde görünmelidir.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. Daha fazla `Do` satır yoksa metin satırlarını okumak için bir döngü oluşturun.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. Seri bağlantı <xref:System.IO.Ports.SerialPort.ReadLine> noktasından sonraki kullanılabilir metin satırını okumak için yöntemini kullanın.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. Yöntemin döndürüp `If` döndürmediğine `Nothing` yönelik bir ifade kullanın (yani daha fazla metin kullanılamaz). <xref:System.IO.Ports.SerialPort.ReadLine> Geri dönemezse `Nothing` `Do` döngüden çıkın.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. Dize gerçekten `Else` okuneyse, `If` durumu işlemek için deyime bir blok ekleyin. Blok, dizeyi seri bağlantı noktasından dönüş dizesine ekler.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. Dizeyi döndürür.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnekte, bilgisayarın kullandığı `COM1`varsayılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnekte, bilgisayarın kullandığı `COM1`varsayılır. Daha fazla esneklik için, kod kullanıcının kullanılabilir bağlantı noktası listesinden istenen seri bağlantı noktasını seçmesine izin verir. Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Bu örnek, uygulamanın `Try...Catch...Finally` bağlantı noktasını kapatıp zaman aşımı özel durumlarını yakalamada emin olmak için bir bloğu kullanır. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

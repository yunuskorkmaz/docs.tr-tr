---
title: 'Nasıl yapılır: Seri Bağlantı Noktalarından Dize Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 93b6b47d89d05331c85a6459bba7d6fd5e2e3377
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401842"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma

Bu konu başlığı `My.Computer.Ports` altında, bilgisayarın seri bağlantı noktalarından Visual Basic dize almak için nasıl kullanılacağı açıklanmaktadır.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Seri bağlantı noktasından dizeler almak için  
  
1. Dönüş dizesini başlatın.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. Dizelerin hangi seri bağlantı noktası tarafından sağlanması gerektiğini saptayın. Bu örnek, olduğunu varsayar `COM1` .  
  
3. `My.Computer.Ports.OpenSerialPort`Bağlantı noktasına bir başvuru almak için yöntemini kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally`Blok, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar. Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde görünmelidir.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. `Do`Daha fazla satır yoksa metin satırlarını okumak için bir döngü oluşturun.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <xref:System.IO.Ports.SerialPort.ReadLine>Seri bağlantı noktasından sonraki kullanılabilir metin satırını okumak için yöntemini kullanın.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. `If` <xref:System.IO.Ports.SerialPort.ReadLine> Yöntemin döndürüp döndürmediğine yönelik bir ifade kullanın `Nothing` (yani daha fazla metin kullanılamaz). Geri dönemezse `Nothing` `Do` döngüden çıkın.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. `Else` `If` Dize gerçekten okuneyse, durumu işlemek için deyime bir blok ekleyin. Blok, dizeyi seri bağlantı noktasından dönüş dizesine ekler.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. Dizeyi döndürür.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnekte, bilgisayarın kullandığı varsayılır `COM1` .  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnekte, bilgisayarın kullandığı varsayılır `COM1` . Daha fazla esneklik için, kod kullanıcının kullanılabilir bağlantı noktası listesinden istenen seri bağlantı noktasını seçmesine izin verir. Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](how-to-show-available-serial-ports.md).  
  
 Bu örnek `Try...Catch...Finally` , uygulamanın bağlantı noktasını kapatıp zaman aşımı özel durumlarını yakalamada emin olmak için bir bloğu kullanır. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](how-to-send-strings-to-serial-ports.md)
- [Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](how-to-show-available-serial-ports.md)

---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma'
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

Bu konu, Visual `My.Computer.Ports` Basic'te bilgisayarın seri bağlantı noktalarından dizeleri almak için nasıl kullanılacağını açıklar.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Seri bağlantı noktasından dizeleri almak için  
  
1. İade dizesini başlangıç olarak ver.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. Dizeleri hangi seri bağlantı noktasısağlaması gerektiğini belirleyin. Bu örnek olduğunu `COM1`varsayar.  
  
3. Bağlantı `My.Computer.Ports.OpenSerialPort` noktasına başvuruda bulunulmak için yöntemi kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Blok, `Try...Catch...Finally` bir özel durum oluştursa bile uygulamanın seri bağlantı noktasını kapatmasına olanak tanır. Seri bağlantı noktasını işleyen tüm kodbu blok içinde görünmelidir.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. Başka `Do` satır bulunana kadar metin satırlarını okumak için bir döngü oluşturun.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. Seri <xref:System.IO.Ports.SerialPort.ReadLine> bağlantı noktasından bir sonraki kullanılabilir metin satırını okumak için yöntemi kullanın.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. Yöntemin `If` <xref:System.IO.Ports.SerialPort.ReadLine> geri döndüğünü `Nothing` belirlemek için bir deyim kullanın (bu da başka metin bulunmadığı anlamına gelir). Dönerse, `Nothing`döngüden `Do` çıkın.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. Dize `Else` `If` gerçekten okunuyorsa büyük/küçük harf işlemek için deyime bir blok ekleyin. Blok, dizeyi seri bağlantı noktasından return string'e ekler.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. Dizeyi geri ver.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet toplayıcı, **bağlantı ve ağ**bulunmaktadır. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnek, bilgisayarın kullandığını `COM1`varsayar.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu örnek, bilgisayarın kullandığını `COM1`varsayar. Daha fazla esneklik için, kod kullanıcının kullanılabilir bağlantı noktaları listesinden istenen seri bağlantı noktasını seçmesine izin vermelidir. Daha fazla bilgi için [bkz: Kullanılabilir Seri Bağlantı Noktalarını Göster.](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)  
  
 Bu örnek, `Try...Catch...Finally` uygulamanın bağlantı noktasını kapattıklarından emin olmak ve zaman aralarını yakalamak için bir blok kullanır. Daha fazla bilgi için [bkz. Yakalamak... Son Olarak İfade](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

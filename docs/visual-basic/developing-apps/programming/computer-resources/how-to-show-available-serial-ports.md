---
title: 'Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c7e5f797c1d098a3b2d01745b949ed50375ea7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345569"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme

Bu konu, Visual `My.Computer.Ports` Basic'te bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için nasıl kullanılacağını açıklar.  
  
 Bir kullanıcının hangi bağlantı noktasını kullanacağını seçmesine izin vermek için, seri bağlantı noktalarının adları denetime <xref:System.Windows.Forms.ListBox> yerleştirilir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, özelliğin `My.Computer.Ports.SerialPortNames` döndürdüğü bütün dizeleri üzerinde döngüler. Bu dizeleri bilgisayarda kullanılabilir seri bağlantı noktalarının adlarıdır.  
  
 Genellikle, bir kullanıcı kullanılabilir bağlantı noktaları listesinden uygulamanın hangi seri bağlantı noktasını kullanması gerektiğini seçer. Bu örnekte, seri bağlantı noktası adları <xref:System.Windows.Forms.ListBox> denetimde depolanır. Daha fazla bilgi için [ListBox Denetimi'ne](../../../../framework/winforms/controls/listbox-control-windows-forms.md)bakın.  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet toplayıcı, **bağlantı ve ağ**bulunmaktadır. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnek şunları gerektirir:  
  
- System.Windows.Forms.dll için bir proje başvurusu.  
  
- Ad alanının üyelerine <xref:System.Windows.Forms> erişim. Kodunuzda `Imports` üye adlarını tam olarak nitelemediğiniz bir ekstre ekleyin. Daha fazla bilgi [için, Bkz. İçerme Bildirimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Formunuzun bir <xref:System.Windows.Forms.ListBox> denetimi `ListBox1`var.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Kullanılabilir seri bağlantı noktası <xref:System.Windows.Forms.ListBox> adlarını görüntülemek için denetimi kullanmanız gerekmez. Bunun yerine, bir <xref:System.Windows.Forms.ComboBox> veya başka bir denetim kullanabilirsiniz. Uygulamanın kullanıcıdan yanıt alabına ihtiyacı <xref:System.Windows.Forms.TextBox> yoksa, bilgileri görüntülemek için bir denetim kullanabilirsiniz.  
  
> [!NOTE]
> Windows 98'de çalıştırıldığında döndürülen bağlantı noktası adları yanlış `My.Computer.Ports.SerialPortNames` olabilir. Uygulama hatalarını önlemek için, bağlantı `Try...Catch...Finally` noktalarını `Using` açmak için bağlantı noktası adlarını kullanırken deyim veya deyim gibi özel durum işlemeyi kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)

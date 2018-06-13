---
title: Verileri Panoda depolama ve (Visual Basic) panodan okuma
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: eb8ae25f260ed434c4aafcc064be8fb6bebaaac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591385"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Verileri Panoda depolama ve (Visual Basic) panodan okuma
Pano, metin ve resimler gibi verileri depolamak için kullanılabilir. Pano tüm etkin işlemler tarafından paylaşıldığından, bunlar arasında veri aktarmak için kullanılabilir. `My.Computer.Clipboard` Nesne kolayca panoya erişmek için okuma ve yazma olanak sağlar.  
  
## <a name="reading-from-the-clipboard"></a>Panodan okuma  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> yöntemi Panodaki metni okuyun. Aşağıdaki kod metni okur ve bir ileti kutusu görüntüler. Örneğin düzgün çalışması Panodaki depolanan metni olması gerekir.  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **Windows Forms uygulamaları > Pano**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> görüntüyü Pano'dan alma yöntemi. Bu örnek görüntüyü Pano'ya almadan ve atanarak önce olup olmadığını denetler `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **Windows Forms uygulamaları > Pano**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Uygulamayı kapatmak bile sonra Pano'ya yerleştirilen öğelerin korunur.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Pano'da depolanan dosya türünü belirleme  
 Panodaki veriler birkaç metin, ses dosyası veya bir görüntü gibi farklı form alabilir. Ne tür bir dosya Pano'ya olduğunu belirlemek için yöntemleri gibi kullanabilir <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, ve <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Yöntemi denetlemek istediğiniz özel bir biçim varsa kullanılabilir.  
  
 Kullanım `ContainsImage` Pano'ya bulunan verileri görüntüyü olup olmadığını belirlemek için işlev. Aşağıdaki kod, verileri bir görüntü ve buna göre raporlar olup olmadığını görmek için denetler.  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a>Pano temizleme  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Yöntemi Pano temizler. Pano başka işlemler tarafından paylaşıldığından, temizlemeden bu işlemleri üzerinde bir etkisi olabilir.  
  
 Aşağıdaki kodu nasıl kullanılacağını gösterir `Clear` yöntemi.  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a>Panoya yazma  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metni panoya yazmak için yöntem. Aşağıdaki kod, "Bu bir test panoya dizedir" dizesi yazar.  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 `SetText` Yöntemi türü içeren bir biçim parametresini kabul edebileceği <xref:System.Windows.Forms.TextDataFormat>. Aşağıdaki kod, "Bu bir test panoya RTF metin olarak dizedir" dizesi yazar.  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> panoya veri yazmak için yöntem. Bu örnek Yazar `DataObject``dataChunk` özel biçim Pano'ya `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> panoya ses veri yazmak için yöntem. Bu örnek, bayt dizisi oluşturur `musicReader`, dosyasını okur `cool.wav` , içine ve panoya yazar.  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  Pano diğer kullanıcılar tarafından erişilebilir olduğundan, parolalar veya gizli verileri gibi hassas bilgileri depolamak için kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>  
 [Nasıl Yapılır: Nesne Verilerini bir XML Dosyasından Okuma](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [Nasıl Yapılır: Nesne Verilerini bir XML Dosyasına Yazma](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

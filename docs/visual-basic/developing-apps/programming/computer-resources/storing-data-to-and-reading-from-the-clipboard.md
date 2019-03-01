---
title: Verileri Panoda depolama ve panodan (Visual Basic) okuma
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: cc39c501520f8d25d01917114553647621438750
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977714"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Verileri Panoda depolama ve panodan (Visual Basic) okuma
Pano, metin ve görüntü gibi verileri depolamak için kullanılabilir. Tüm etkin işlemler tarafından Pano paylaşıldığından, bunlar arasında veri aktarmak için kullanılabilir. `My.Computer.Clipboard` Nesne kolayca panoya erişebilir ve okuma ve yazma olanak tanır.  
  
## <a name="reading-from-the-clipboard"></a>Panodan okuma  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> Pano metni okumak için yöntem. Aşağıdaki kod okur ve bir ileti kutusunda görüntüler. Örneğin düzgün çalışması Panodaki depolanan metin olmalıdır.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Pano**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> panodan bir görüntü almak için yöntemi. Bu örnekte görüntüyü Pano'ya alınması ve giderek önce olup olmadığını denetler `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Pano**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Uygulama kapatma bile sonra Panoda yerleştirilen öğelerin açık kalır.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Panoya depolanan dosya türünü belirleme  
 Panodaki veriler, birkaç metin, ses dosyası ve görüntü gibi farklı form alabilir. Ne tür bir dosya olup Panodaki belirlemek için yöntemleri gibi kullanabileceğiniz <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, ve <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Yöntemi kontrol etmek istediğiniz özel bir biçim varsa kullanılabilir.  
  
 Kullanım `ContainsImage` verileri Panoya bir görüntü olup olmadığını belirlemek için işlevi. Veriler bir görüntü ve buna göre raporları görmek için aşağıdaki kodu denetler.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Pano temizleme  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Yöntemi Pano temizler. Pano başka işlemler tarafından paylaşıldığından, temizlemeden bu işlemlerin bir etkisi olabilir.  
  
 Aşağıdaki kod nasıl kullanılacağını gösterir `Clear` yöntemi.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Pano yazma  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> panoya metin yazmak için yöntemi. Aşağıdaki kod, "Bu bir test panoya dizedir" dizesi yazar.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 `SetText` Yöntemi, bir tür içeren bir biçim parametresini kabul edebilir <xref:System.Windows.Forms.TextDataFormat>. Aşağıdaki kod, "Bu bir test RTF metin olarak panoya dizedir" dizesi yazar.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> panoya veri yazmak için yöntemi. Bu örnek, Yazar `DataObject` `dataChunk` özel biçiminde panoya `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> panoya ses veri yazmak için yöntemi. Bu örnek, bir bayt dizisi oluşturur `musicReader`, dosyayı okur `cool.wav` içine ve panoya yazar.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
>  Pano, diğer kullanıcılar tarafından erişilebilir olduğundan, parolalar veya gizli verileri gibi hassas bilgileri depolamak için kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Nasıl yapılır: Nesne verilerini bir XML dosyasından okuma](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Nasıl yapılır: Nesne verilerini bir XML dosyasına yazma](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

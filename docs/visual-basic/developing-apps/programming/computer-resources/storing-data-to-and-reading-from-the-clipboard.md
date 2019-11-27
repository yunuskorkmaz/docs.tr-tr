---
title: Verileri Panoda Depolama ve Panodan Okuma
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 243fb237f3f9ba53f8b29079df08531c102c78dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349726"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Verileri Panoda Depolama ve Panodan Okuma (Visual Basic)

Pano, metin ve görüntü gibi verileri depolamak için kullanılabilir. Pano tüm etkin süreçler tarafından paylaşıldığından, bunlar arasında veri aktarmak için kullanılabilir. `My.Computer.Clipboard` nesnesi, panoya kolayca erişmenizi ve bu dosyayı okuyup yazmanızı sağlar.  
  
## <a name="reading-from-the-clipboard"></a>Panodan Okuma  

 Panodaki metni okumak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> yöntemini kullanın. Aşağıdaki kod, metni okur ve bir ileti kutusunda görüntüler. Örneğin doğru şekilde çalışması için Panoda depolanan metin olmalıdır.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Panodan bir görüntü almak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> yöntemini kullanın. Bu örnek, yüklemeden önce panoda bir görüntü olup olmadığını ve `PictureBox1`atamaya yönelik olup olmadığını denetler.  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Pano 'ya yerleştirilmiş öğeler, uygulama kapatıldıktan sonra bile kalır.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Panoda depolanan dosya türünü belirleme  

 Panodaki veriler metin, ses dosyası veya görüntü gibi çeşitli biçimlerde olabilir. Panodaki dosya sıralamasını belirlemek için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>ve <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>gibi yöntemleri kullanabilirsiniz. Denetlemek istediğiniz özel bir biçim varsa <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> yöntemi kullanılabilir.  
  
 Panoda içerilen verilerin bir görüntü olup olmadığını anlamak için `ContainsImage` işlevini kullanın. Aşağıdaki kod, verilerin bir görüntü ve raporların uygun olup olmadığını denetler.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Panoyu Temizleme  

 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> yöntemi panoyu temizler. Pano başka süreçler tarafından paylaşıldığından, temizleme işlemi bu işlemlere etkisi olabilir.  
  
 Aşağıdaki kod `Clear` yönteminin nasıl kullanılacağını gösterir.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Panoya yazma  

 Panoya metin yazmak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> yöntemini kullanın. Aşağıdaki kod, panoya "This bir test dizesidir" dizesini yazar.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 `SetText` yöntemi bir <xref:System.Windows.Forms.TextDataFormat>türü içeren bir biçim parametresi kabul edebilir. Aşağıdaki kod, "Bu bir test dizesi" dizesini RTF metni olarak panoya yazar.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 Panoya veri yazmak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> yöntemini kullanın. Bu örnek, `DataObject` `dataChunk` özel biçim `specialFormat`panoya yazar.  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Pano 'ya ses verileri yazmak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> yöntemini kullanın. Bu örnek, bayt dizisi `musicReader`oluşturur, dosyayı buna `cool.wav` okur ve sonra panoya yazar.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> Panoya diğer kullanıcılar tarafından erişilebildiğinden, parola veya gizli veriler gibi hassas bilgileri depolamak için bu uygulamayı kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Nasıl Yapılır: Nesne Verilerini bir XML Dosyasından Okuma](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Nasıl Yapılır: Nesne Verilerini bir XML Dosyasına Yazma](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

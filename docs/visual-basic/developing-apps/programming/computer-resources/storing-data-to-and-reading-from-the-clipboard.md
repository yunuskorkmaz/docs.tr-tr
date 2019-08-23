---
title: Verileri Panoda Depolama ve Panodan Okuma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: d7693f6b5dc74e17686cd7d2667f32adbde9df80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916512"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Verileri Panoda Depolama ve Panodan Okuma (Visual Basic)
Pano, metin ve görüntü gibi verileri depolamak için kullanılabilir. Pano tüm etkin süreçler tarafından paylaşıldığından, bunlar arasında veri aktarmak için kullanılabilir. `My.Computer.Clipboard` Nesnesi panoya kolayca erişmenizi ve bu panoyu okuyup yazmanızı sağlar.  
  
## <a name="reading-from-the-clipboard"></a>Panodan Okuma  
 Panodaki metni okumak için yönteminikullanın.<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> Aşağıdaki kod, metni okur ve bir ileti kutusunda görüntüler. Örneğin doğru şekilde çalışması için Panoda depolanan metin olmalıdır.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda**bulunur. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Panodan bir görüntü almak için yönteminikullanın.<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> Bu örnek, yüklemeden önce panoda bir resim olup olmadığını ve üzerine `PictureBox1`atamayı denetler.  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Pano 'ya yerleştirilmiş öğeler, uygulama kapatıldıktan sonra bile kalır.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Panoda depolanan dosya türünü belirleme  
 Panodaki veriler metin, ses dosyası veya görüntü gibi çeşitli biçimlerde olabilir. Panodaki dosya sıralamasını belirlemek için, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, ve <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>gibi yöntemleri <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A> <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>kullanabilirsiniz. Denetlemek istediğiniz özel bir biçim varsa yöntemikullanılabilir.<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A>  
  
 Panoda bulunan verilerin bir görüntü olup olmadığını anlamak için işlevinikullanın.`ContainsImage` Aşağıdaki kod, verilerin bir görüntü ve raporların uygun olup olmadığını denetler.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Panoyu Temizleme  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Yöntemi panoyu temizler. Pano başka süreçler tarafından paylaşıldığından, temizleme işlemi bu işlemlere etkisi olabilir.  
  
 Aşağıdaki kod `Clear` yönteminin nasıl kullanılacağını gösterir.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Panoya yazma  
 Panoya metin yazmak için yönteminikullanın.<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> Aşağıdaki kod, panoya "This bir test dizesidir" dizesini yazar.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 Yöntemi `SetText` ,<xref:System.Windows.Forms.TextDataFormat>türü içeren bir biçim parametresini kabul edebilir. Aşağıdaki kod, "Bu bir test dizesi" dizesini RTF metni olarak panoya yazar.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 Verileri panoya yazmak için yönteminikullanın.<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> Bu örnek, `DataObject` `dataChunk` öğesini panoya özel biçimde `specialFormat`yazar.  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Pano 'ya ses verileri yazmak için yönteminikullanın.<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> Bu örnek, Byte dizisini `musicReader`oluşturur, dosyayı `cool.wav` onunla okur ve panoya yazar.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> Panoya diğer kullanıcılar tarafından erişilebildiğinden, parola veya gizli veriler gibi hassas bilgileri depolamak için bu uygulamayı kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Nasıl yapılır: XML dosyasından nesne verilerini okuma](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Nasıl yapılır: Nesne verilerini bir XML dosyasına yaz](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

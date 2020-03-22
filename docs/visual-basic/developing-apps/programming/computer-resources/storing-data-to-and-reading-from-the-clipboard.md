---
title: Panoya veri depolama ve Panodan okuma
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349726"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Panoya veri depolama ve Panodan okuma (Visual Basic)

Pano, metin ve resim gibi verileri depolamak için kullanılabilir. Pano tüm etkin işlemler tarafından paylaşıldığından, aralarındaveri aktarmak için kullanılabilir. Nesne, `My.Computer.Clipboard` Pano'ya kolayca erişmenizi ve panodan okumanızı ve ona yazmanızı sağlar.  
  
## <a name="reading-from-the-clipboard"></a>Panodan Okuma  

 Panodaki <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metni okumak için yöntemi kullanın. Aşağıdaki kod metni okur ve bir ileti kutusunda görüntüler. Örneğin düzgün çalışması için Pano'da kayıtlı metin olması gerekir.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet picker, Windows Forms **Uygulamaları > Pano**bulunur. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
 Pano'dan <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> görüntü almak için yöntemi kullanın. Bu örnek, Pano'yu almadan ve `PictureBox1`atamadan önce Pano'da bir görüntü olup olmadığını denetler.  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet picker, Windows Forms **Uygulamaları > Pano**bulunur. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
 Panoya yerleştirilen öğeler, uygulama kapatıldıktan sonra bile devam edecektir.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Panoda depolanan dosya türünü belirleme  

 Panodaki veriler metin, ses dosyası veya görüntü gibi çeşitli formlar alabilir. Panoda ne tür bir dosya olduğunu belirlemek <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>için , , <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>ve <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. Denetlemek <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> istediğiniz özel bir biçiminiz varsa yöntem kullanılabilir.  
  
 Panoda `ContainsImage` bulunan verilerin bir görüntü olup olmadığını belirlemek için işlevi kullanın. Aşağıdaki kod, verilerin bir görüntü olup olmadığını denetler ve buna göre raporlar.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Panoyu Temizleme  

 Yöntem <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Pano'yu temizler. Pano diğer işlemler tarafından paylaşıldığından, temizlemenin bu işlemler üzerinde bir etkisi olabilir.  
  
 Aşağıdaki kod yöntemin nasıl `Clear` kullanılacağını gösterir.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Panoya Yazma  

 Panoya <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metin yazmak için yöntemi kullanın. Aşağıdaki kod Panoya "Bu bir test dizesidir" dizesini yazar.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 Yöntem, `SetText` <xref:System.Windows.Forms.TextDataFormat>bir tür . Aşağıdaki kod, PANOYA RTF metni olarak "Bu bir test dizesidir" dizesini yazar.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 Panoya <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> veri yazmak için yöntemi kullanın. Bu örnek, `DataObject` `dataChunk` panoya özel biçimde `specialFormat`yazar.  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Panoya <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> ses verileri yazmak için yöntemi kullanın. Bu örnek bayt dizisini `musicReader`oluşturur, `cool.wav` dosyayı içine okur ve panoya yazar.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> Panoya diğer kullanıcılar erişebildiği için, parolalar veya gizli veriler gibi hassas bilgileri depolamak için kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Nasıl kullanılır: XML Dosyasından Nesne Verilerini Okuma](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Nasıl kullanılır: Nesne Verilerini XML Dosyasına Yazma](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

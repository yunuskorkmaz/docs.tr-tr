---
title: "Nasıl yapılır: Windows Forms'da Baskı Önizlemeyi Kullanarak Yazdırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 07137d03dd9a20d8eab564757618e48e25b45353
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931763"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Nasıl yapılır: Windows Forms'da Baskı Önizlemeyi Kullanarak Yazdırma
Yazdırma hizmetlerinin yanı sıra baskı önizleme sunmak için Windows Forms programlamada çok yaygındır. Uygulamanıza baskı önizleme hizmetleri eklemenin kolay bir yolu, bir dosyayı yazdırmak için <xref:System.Windows.Forms.PrintPreviewDialog> <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleme mantığı ile birlikte bir denetim kullanmaktır.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Bir metin belgesini PrintPreview Iletişim kutusu denetimiyle önizlemek için  
  
1. Formunuza bir <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>ve iki dize ekleyin.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. Yazdırmak istediğiniz belgeye özelliği ayarlayın ve belgenin içeriğini açın ve daha önce eklediğiniz dizeye okuyun. <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Belgeyi yazdırırken yaptığınız gibi, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde, sayfa başına satırları hesaplamak ve belgenin içeriğini işlemek için, <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğini ve dosya içeriğini kullanın. Her sayfa çizildikten sonra, son sayfa olup olmadığını denetleyin ve <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliğini <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde ayarlayın. Olay, olana kadar <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A>tetiklenir. `false` <xref:System.Drawing.Printing.PrintDocument.PrintPage> Belgenin işlenmesi bittiğinde, işlenecek dizeyi sıfırlayın. Ayrıca, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayın olay işleme yöntemiyle ilişkili olduğundan emin olun.  
  
    > [!NOTE]
    > Uygulamanızda yazdırma uyguladıysanız adım 2 ve 3 ' ü zaten tamamlamış olabilirsiniz.  
  
     Aşağıdaki kod örneğinde, olay işleyicisi, formda kullanılan yazı tipinde "testPage. txt" dosyasını yazdırmak için kullanılır.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> Denetimin<xref:System.Drawing.Printing.PrintDocument> özelliğini formdaki bileşeneayarlayın<xref:System.Windows.Forms.PrintPreviewDialog> .  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <xref:System.Windows.Forms.PrintPreviewDialog> Denetimindeki <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi çağırın. Genellikle bir düğmenin <xref:System.Windows.Forms.Control.Click> olay <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> işleme yönteminden çağrı yapılır. Çağırma <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> olayı<xref:System.Drawing.Printing.PrintDocument.PrintPage> başlatır ve çıktıyı <xref:System.Windows.Forms.PrintPreviewDialog> denetime işler. Kullanıcı iletişim kutusundaki yazdır simgesine tıkladığında, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay yeniden oluşturulur ve Önizleme iletişim kutusu yerine çıktıyı yazıcıya gönderir. Bu nedenle, 3. adımdaki işleme sürecinin sonunda dize sıfırlanır.  
  
     Aşağıdaki kod örneğinde, form üzerindeki <xref:System.Windows.Forms.Control.Click> bir düğme için olay işleme yöntemi gösterilmektedir. Bu olay işleme yöntemi, belgeyi okumak ve Baskı Önizleme iletişim kutusunu göstermek için yöntemleri çağırır.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Windows. Forms, System. Drawing derlemelerine başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms bir çok sayfalı metin dosyası yazdırma](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)
- [Windows Forms'ta Daha Güvenli Yazdırma](../more-secure-printing-in-windows-forms.md)

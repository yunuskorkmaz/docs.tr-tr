---
title: Baskı önizlemeyi kullanarak yazdırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 1975c902fdb56326c763f2e2fc11e381ffc7fbd3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740610"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Nasıl yapılır: Windows Forms'ta Baskı Önizlemeyi Kullanarak Yazdırma
Yazdırma hizmetlerinin yanı sıra baskı önizleme sunmak için Windows Forms programlamada çok yaygındır. Uygulamanıza baskı önizleme hizmetleri eklemenin kolay bir yolu, bir dosyayı yazdırmak için <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleme mantığı ile birlikte <xref:System.Windows.Forms.PrintPreviewDialog> bir denetim kullanmaktır.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Bir metin belgesini PrintPreview Iletişim kutusu denetimiyle önizlemek için  
  
1. Formunuza bir <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>ve iki dize ekleyin.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliğini yazdırmak istediğiniz belge olarak ayarlayın ve belgenin içeriğini açın ve daha önce eklediğiniz dizeye okuyun.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Belgeyi yazdırırken yaptığınız gibi, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde, sayfa başına satırları hesaplamak ve belgenin içeriğini işlemek için <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğini ve dosya içeriğini kullanın. Her sayfa çizildikten sonra, son sayfa olup olmadığını denetleyin ve <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliğini uygun şekilde ayarlayın. <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı, <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false`kadar tetiklenir. Belgenin işlenmesi bittiğinde, işlenecek dizeyi sıfırlayın. Ayrıca, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayının olay işleme yöntemiyle ilişkili olduğundan emin olun.  
  
    > [!NOTE]
    > Uygulamanızda yazdırma uyguladıysanız adım 2 ve 3 ' ü zaten tamamlamış olabilirsiniz.  
  
     Aşağıdaki kod örneğinde, olay işleyicisi, formda kullanılan yazı tipinde "testPage. txt" dosyasını yazdırmak için kullanılır.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <xref:System.Windows.Forms.PrintPreviewDialog> denetiminin <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> özelliğini formdaki <xref:System.Drawing.Printing.PrintDocument> bileşeni olarak ayarlayın.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <xref:System.Windows.Forms.PrintPreviewDialog> denetiminde <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini çağırın. Genellikle bir düğmenin <xref:System.Windows.Forms.Control.Click> olay işleme yönteminden <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çağırabilirsiniz. <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çağırmak <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayını oluşturur ve çıktıyı <xref:System.Windows.Forms.PrintPreviewDialog> denetimine işler. Kullanıcı iletişim kutusundaki yazdır simgesine tıkladığında, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı yeniden oluşturulur ve Önizleme iletişim kutusu yerine çıktıyı yazıcıya gönderir. Bu nedenle, 3. adımdaki işleme sürecinin sonunda dize sıfırlanır.  
  
     Aşağıdaki kod örneği, form üzerindeki bir düğme için <xref:System.Windows.Forms.Control.Click> olay işleme yöntemini gösterir. Bu olay işleme yöntemi, belgeyi okumak ve Baskı Önizleme iletişim kutusunu göstermek için yöntemleri çağırır.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- System, System. Windows. Forms, System. Drawing derlemelerine başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)
- [Windows Forms'ta Daha Güvenli Yazdırma](../more-secure-printing-in-windows-forms.md)

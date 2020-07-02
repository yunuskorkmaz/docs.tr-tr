---
title: Baskı önizlemeyi kullanarak yazdırma
description: Windows Forms PrintPreview Iletişim kutusunu kullanarak uygulamanıza baskı önizleme hizmetleri eklemeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: abcf77db40f648df1a0cd49922bb49e5c9407811
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621619"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Nasıl yapılır: Windows Forms'ta Baskı Önizlemeyi Kullanarak Yazdırma
Yazdırma hizmetlerinin yanı sıra baskı önizleme sunmak için Windows Forms programlamada çok yaygındır. Uygulamanıza baskı önizleme hizmetleri eklemenin kolay bir yolu, <xref:System.Windows.Forms.PrintPreviewDialog> <xref:System.Drawing.Printing.PrintDocument.PrintPage> bir dosyayı yazdırmak için olay işleme mantığı ile birlikte bir denetim kullanmaktır.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Bir metin belgesini PrintPreview Iletişim kutusu denetimiyle önizlemek için  
  
1. Formunuza bir <xref:System.Windows.Forms.PrintPreviewDialog> , <xref:System.Drawing.Printing.PrintDocument> ve iki dize ekleyin.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>Yazdırmak istediğiniz belgeye özelliği ayarlayın ve belgenin içeriğini açın ve daha önce eklediğiniz dizeye okuyun.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Belgeyi yazdırırken yaptığınız gibi, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde, <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> <xref:System.Drawing.Printing.PrintPageEventArgs> sayfa başına satırları hesaplamak ve belgenin içeriğini işlemek için, sınıfının özelliğini ve dosya içeriğini kullanın. Her sayfa çizildikten sonra, son sayfa olup olmadığını denetleyin ve <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliğini <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde ayarlayın. <xref:System.Drawing.Printing.PrintDocument.PrintPage>Olay, olana kadar tetiklenir <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false` . Belgenin işlenmesi bittiğinde, işlenecek dizeyi sıfırlayın. Ayrıca, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayın olay işleme yöntemiyle ilişkili olduğundan emin olun.  
  
    > [!NOTE]
    > Uygulamanızda yazdırma uyguladıysanız adım 2 ve 3 ' ü zaten tamamlamış olabilirsiniz.  
  
     Aşağıdaki kod örneğinde, olay işleyicisi, formda kullanılan yazı tipinde "testPage.txt" dosyasını yazdırmak için kullanılır.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> <xref:System.Windows.Forms.PrintPreviewDialog> Denetimin özelliğini <xref:System.Drawing.Printing.PrintDocument> formdaki bileşene ayarlayın.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>Denetimindeki yöntemi çağırın <xref:System.Windows.Forms.PrintPreviewDialog> . Genellikle <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> <xref:System.Windows.Forms.Control.Click> bir düğmenin olay işleme yönteminden çağrı yapılır. Çağırma <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> olayı başlatır <xref:System.Drawing.Printing.PrintDocument.PrintPage> ve çıktıyı <xref:System.Windows.Forms.PrintPreviewDialog> denetime işler. Kullanıcı iletişim kutusundaki yazdır simgesine tıkladığında, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay yeniden oluşturulur ve Önizleme iletişim kutusu yerine çıktıyı yazıcıya gönderir. Bu nedenle, 3. adımdaki işleme sürecinin sonunda dize sıfırlanır.  
  
     Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.Control.Click> form üzerindeki bir düğme için olay işleme yöntemi gösterilmektedir. Bu olay işleme yöntemi, belgeyi okumak ve Baskı Önizleme iletişim kutusunu göstermek için yöntemleri çağırır.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Windows. Forms, System. Drawing derlemelerine başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)
- [Windows Forms'ta Daha Güvenli Yazdırma](../more-secure-printing-in-windows-forms.md)

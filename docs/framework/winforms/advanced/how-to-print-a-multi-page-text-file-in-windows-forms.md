---
title: 'Nasıl yapılır: çok sayfalı metin dosyası yazdırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 51e30706bb7693988d611701d013792c82dccd0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740652"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma
Windows tabanlı uygulamaların metin yazdırması çok yaygındır. <xref:System.Drawing.Graphics> sınıfı, ekran veya yazıcı gibi bir cihaza nesneleri (grafik veya metin) çizmek için yöntemler sağlar.  
  
> [!NOTE]
> <xref:System.Windows.Forms.TextRenderer> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemleri yazdırma için desteklenmez. Yazdırma amaçlarıyla metin çizmek için, aşağıdaki kod örneğinde gösterildiği gibi <xref:System.Drawing.Graphics><xref:System.Drawing.Graphics.DrawString%2A> yöntemlerini her zaman kullanmanız gerekir.  
  
### <a name="to-print-text"></a>Metin yazdırmak için  
  
1. Formunuza bir <xref:System.Drawing.Printing.PrintDocument> bileşeni ve dize ekleyin.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. Belge yazdırıyorsanız, <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliğini yazdırmak istediğiniz belge olarak ayarlayın ve belgeler içeriğini açın ve daha önce eklediğiniz dizeye belge içeriğini okuyun.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde, satır uzunluğunu ve sayfa başına satırları hesaplamak için <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğini ve belge içeriğini kullanın. Her sayfa çizildikten sonra, son sayfa olup olmadığını denetleyin ve <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliğini uygun şekilde ayarlayın. <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı, <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false`kadar tetiklenir. Ayrıca, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayının olay işleme yöntemiyle ilişkili olduğundan emin olun.  
  
     Aşağıdaki kod örneğinde, olay işleyicisi "testPage. txt" dosyasının içeriğini formda kullanılan yazı tipiyle yazdırmak için kullanılır.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayını yükseltmek için <xref:System.Drawing.Printing.PrintDocument.Print%2A> yöntemi çağırın.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- C:\\sürücüsünün kökünde bulunan, yazdırılacak metni içeren testPage. txt adlı bir metin dosyası. Farklı bir dosyayı yazdırmak için kodu düzenleyin.  
  
- System, System. Windows. Forms, System. Drawing derlemelerine başvuru.  
  
- Bu örneği Visual Basic veya görsel C#için komut satırından oluşturma hakkında daha fazla bilgi için, bkz. [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [CSC. exe ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Ayrıca, kodu yeni bir projeye yapıştırarak bu örneği Visual Studio 'da da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)

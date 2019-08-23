---
title: "Nasıl yapılır: Windows Forms'da Çok Sayfalı Metin Dosyası Yazdırma"
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
ms.openlocfilehash: bd858279a4d8a3509a91bcd1c62fb1f61d6d2bb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931784"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Nasıl yapılır: Windows Forms'da Çok Sayfalı Metin Dosyası Yazdırma
Windows tabanlı uygulamaların metin yazdırması çok yaygındır. <xref:System.Drawing.Graphics> Sınıfı, ekran veya yazıcı gibi bir cihaza nesneleri (grafik veya metin) çizmek için yöntemler sağlar.  
  
> [!NOTE]
> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yöntemleri<xref:System.Windows.Forms.TextRenderer> yazdırma için desteklenmez. Yazdırma amaçlarıyla metin çizmek için <xref:System.Drawing.Graphics.DrawString%2A> , aşağıdaki <xref:System.Drawing.Graphics>kod örneğinde gösterildiği gibi her zaman yöntemini kullanmanız gerekir.  
  
### <a name="to-print-text"></a>Metin yazdırmak için  
  
1. Formunuza bir <xref:System.Drawing.Printing.PrintDocument> bileşen ve dize ekleyin.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. Bir belge yazdırıyorsanız, <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliği yazdırmak istediğiniz belgeye ayarlayın ve belge içeriğini açın ve daha önce eklediğiniz dizeye belge içeriğini okuyun.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. Olay işleyicisinde, satır uzunluğunu ve sayfa <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> başına satırları hesaplamak <xref:System.Drawing.Printing.PrintPageEventArgs> için sınıfının özelliğini ve belge içeriğini kullanın. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Her sayfa çizildikten sonra, son sayfa olup olmadığını denetleyin ve <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliğini <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde ayarlayın. Olay, olana kadar <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A>tetiklenir. `false` <xref:System.Drawing.Printing.PrintDocument.PrintPage> Ayrıca, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayın olay işleme yöntemiyle ilişkili olduğundan emin olun.  
  
     Aşağıdaki kod örneğinde, olay işleyicisi "testPage. txt" dosyasının içeriğini formda kullanılan yazı tipiyle yazdırmak için kullanılır.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. Olayı yükseltmek için <xref:System.Drawing.Printing.PrintDocument.Print%2A>yönteminiçağırın <xref:System.Drawing.Printing.PrintDocument.PrintPage> .  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- C:\\sürücüsünün kökünde bulunan, yazdırılacak metni içeren TestPage. txt adlı bir metin dosyası. Farklı bir dosyayı yazdırmak için kodu düzenleyin.  
  
- System, System. Windows. Forms, System. Drawing derlemelerine başvuru.  
  
- Bu örneği Visual Basic veya görsel C#için komut satırından oluşturma hakkında daha fazla bilgi için, bkz. [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [CSC. exe ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Ayrıca, kodu yeni bir projeye yapıştırarak bu örneği Visual Studio 'da da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)

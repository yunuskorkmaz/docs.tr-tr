---
title: "Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma"
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
ms.openlocfilehash: b8cfba338bb318139bedf5595df8bad666c201bd
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773543"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma
Metin yazdırma Windows tabanlı uygulamalar için çok yaygındır. <xref:System.Drawing.Graphics> Sınıfı bir aygıta bir ekran veya yazıcı gibi çizim nesneleri (grafik veya metin) için yöntemler sağlar.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yöntemlerinin <xref:System.Windows.Forms.TextRenderer> yazdırma için desteklenmez. Her zaman kullanmalısınız <xref:System.Drawing.Graphics.DrawString%2A> yöntemlerinin <xref:System.Drawing.Graphics>metin yazdırma amacıyla çizmek için aşağıdaki kod örneğinde gösterildiği gibi.  
  
### <a name="to-print-text"></a>Metin yazdırma  
  
1.  Ekleme bir <xref:System.Drawing.Printing.PrintDocument> bileşeni ve formunuza bir dize.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  Belge yazdırma verilirse <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> belge özelliğini istediğiniz yazdırma, açın ve daha önce eklediğiniz dizeye belge içeriklerini okuma.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  İçinde <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi, kullanım <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfı ve belge içeriğini hesaplamak için satır uzunluğu ve sayfa başına satır. Her sayfanın çekildikten sonra son sayfa olup olmadığını denetleyin ve ayarlama <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Kadar olayı yükseltildiğinde <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> olduğu `false`. Ayrıca, emin <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay, olay işleme yöntemi ile ilişkili.  
  
     Aşağıdaki kod örneğinde, olay işleyicisi, form üzerinde kullanılan aynı yazı tipi "testPage.txt" dosyasının içeriği yazdırmak için kullanılır.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  Çağrı <xref:System.Drawing.Printing.PrintDocument.Print%2A> yükseltmek için yöntemi <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Yazdırmak için metni içeren testPage.txt adlı bir metin dosyası C: sürücüsünün kök dizininde bulunan\\. Farklı bir dosya yazdırma için kodu düzenleyin.  
  
-   Sistem, System.Windows.Forms, System.Drawing derlemelere başvurular.  
  
-   Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [Windows Forms Yazdırma Desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)

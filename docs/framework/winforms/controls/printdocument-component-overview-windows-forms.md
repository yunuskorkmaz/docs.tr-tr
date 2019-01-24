---
title: PrintDocument Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 2facbf0a567f81aa6debe2ca60f7f8eabc794bb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532360"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument Bileşenine Genel Bakış (Windows Forms)
Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) bileşen ne tanımlayan özellikleri ve Windows tabanlı uygulamalar içinde belge yazdırma özelliğini ayarlamak için kullanılır. İle birlikte kullanılabilir [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) belge yazdırma tüm yönlerini denetiminde olmasını bileşeni.  
  
## <a name="working-with-the-printdocument-component"></a>PrintDocument bileşeni ile çalışma  
 İki içeren ana senaryoları <xref:System.Drawing.Printing.PrintDocument> bileşeni şunlardır:  
  
-   Bireysel metin dosyası yazdırma gibi basit yazdırma işler. Böyle bir durumda, eklediğiniz <xref:System.Drawing.Printing.PrintDocument> Windows Form, bileşene, ardından bir dosyaya yazdırır programlama mantığı eklemek <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi. Programlama mantığı ile sizin <xref:System.Drawing.Printing.PrintDocument.Print%2A> belge yazdırma için yöntemi. Bu yöntem gönderir bir <xref:System.Drawing.Graphics> bulunan nesne <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfına yazıcı. Bir metin belgesini kullanarak yazdırma gösteren bir örnek <xref:System.Drawing.Printing.PrintDocument> bileşeni Bkz [nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).  
  
-   Daha karmaşık yazdırma işlerini yazdırma mantıksal yazdığınız yeniden istediğiniz bir durum gibi. Böyle bir durumda yeni bir bileşenden türetin <xref:System.Drawing.Printing.PrintDocument> bileşeni ve geçersiz kılma (bkz [geçersiz kılmalar](~/docs/visual-basic/language-reference/modifiers/overrides.md) Visual Basic veya [geçersiz kılma](~/docs/csharp/language-reference/keywords/override.md) için C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.  
  
 Bir forma eklendiğinde <xref:System.Drawing.Printing.PrintDocument> bileşeni Tepsi Windows Form Tasarımcısı'nın altındaki görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms Yazdırma Desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
- [PrintDocument Bileşeni](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)

---
title: PrintDocument Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728548"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument Bileşenine Genel Bakış (Windows Forms)

Windows Forms [PrintDocument](printdocument-component-windows-forms.md) bileşeni, nelerin yazdırılacağını betimleyen özellikleri ve Windows tabanlı uygulamalar içinde belge yazdırma özelliğini ayarlamak için kullanılır. Belge yazdırmanın tüm yönlerinin denetiminde olması için [PrintDialog](printdialog-component-windows-forms.md) bileşeniyle birlikte kullanılabilir.

## <a name="working-with-the-printdocument-component"></a>PrintDocument bileşeniyle çalışma

<xref:System.Drawing.Printing.PrintDocument> bileşeni içeren temel senaryolardan ikisi şunlardır:

- Tek bir metin dosyası yazdırma gibi basit yazdırma işleri. Böyle bir durumda, <xref:System.Drawing.Printing.PrintDocument> bileşenini bir Windows formuna eklemeniz ve sonra <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisine bir dosya yazdıran programlama mantığını eklemeniz gerekir. Programlama mantığı, belgeyi yazdırmak için <xref:System.Drawing.Printing.PrintDocument.Print%2A> yöntemiyle birlikte olmalıdır. Bu yöntem, <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğinde bulunan <xref:System.Drawing.Graphics> nesnesini yazıcıya gönderir. <xref:System.Drawing.Printing.PrintDocument> bileşenini kullanarak bir metin belgesinin nasıl yazdırılacağını gösteren bir örnek için, bkz. [nasıl yapılır: Windows Forms Içinde çok sayfalı metin dosyası yazdırma](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).

- Yazdığınız yazdırma mantığını yeniden kullanmak istediğiniz durumlar gibi daha karmaşık yazdırma işleri. Böyle bir durumda, <xref:System.Drawing.Printing.PrintDocument> bileşeninden yeni bir bileşen türetirsiniz ve <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı geçersiz kılmalısınız (bkz. Visual Basic veya [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) Için C# [geçersiz kılmalar](../../../visual-basic/language-reference/modifiers/overrides.md) ).

Bir forma eklendiğinde <xref:System.Drawing.Printing.PrintDocument> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms Yazdırma Desteği](../advanced/windows-forms-print-support.md)
- [PrintDocument Bileşeni](printdocument-component-windows-forms.md)

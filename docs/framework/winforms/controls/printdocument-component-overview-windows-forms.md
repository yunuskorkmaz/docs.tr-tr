---
title: PrintDocument Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928985"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument Bileşenine Genel Bakış (Windows Forms)

Windows Forms [PrintDocument](printdocument-component-windows-forms.md) bileşeni, nelerin yazdırılacağını betimleyen özellikleri ve Windows tabanlı uygulamalar içinde belge yazdırma özelliğini ayarlamak için kullanılır. Belge yazdırmanın tüm yönlerinin denetiminde olması için [PrintDialog](printdialog-component-windows-forms.md) bileşeniyle birlikte kullanılabilir.

## <a name="working-with-the-printdocument-component"></a>PrintDocument bileşeniyle çalışma

<xref:System.Drawing.Printing.PrintDocument> Bileşeni içeren temel senaryolardan ikisi şunlardır:

- Tek bir metin dosyası yazdırma gibi basit yazdırma işleri. Böyle bir durumda, <xref:System.Drawing.Printing.PrintDocument> bileşeni bir Windows formuna eklemeli ve ardından <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisine bir dosya yazdıran programlama mantığını eklersiniz. Programlama mantığı, belgeyi yazdırma <xref:System.Drawing.Printing.PrintDocument.Print%2A> yöntemiyle birlikte olmalıdır. Bu yöntem, <xref:System.Drawing.Graphics> <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğinde yer alan bir nesneyi yazıcıya gönderir. <xref:System.Drawing.Printing.PrintDocument> Bileşeni kullanarak nasıl metin belgesi yazdırılacağını gösteren bir örnek için bkz [. nasıl yapılır: Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)bir çok sayfalı metin dosyası yazdırın.

- Yazdığınız yazdırma mantığını yeniden kullanmak istediğiniz durumlar gibi daha karmaşık yazdırma işleri. Böyle bir durumda <xref:System.Drawing.Printing.PrintDocument> , bileşenden yeni bir bileşen türetirsiniz ve <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı geçersiz kılarsınız (için C#bkz. Visual Basic veya [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) için [geçersiz kılmalar](../../../visual-basic/language-reference/modifiers/overrides.md) ).

Bir forma <xref:System.Drawing.Printing.PrintDocument> eklendiğinde bileşen, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms Yazdırma Desteği](../advanced/windows-forms-print-support.md)
- [PrintDocument Bileşeni](printdocument-component-windows-forms.md)

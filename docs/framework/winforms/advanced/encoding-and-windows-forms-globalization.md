---
title: Kodlama ve Windows Forms Genelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
ms.openlocfilehash: 60ca9f7ba2f716b5dab1b0276bc3cd07ddd8f65c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736880"
---
# <a name="encoding-and-windows-forms-globalization"></a>Kodlama ve Windows Forms Genelleştirme

Windows Forms uygulamalar tamamen Unicode özellikli olduğundan, her karakterin platform, program veya dile bakılmaksızın benzersiz bir sayıyla temsil edildiği anlamına gelir. Unicode hakkında daha fazla bilgi için bkz. [Unicode konsorsiyum Web sitesi](https://www.unicode.org).

## <a name="benefits-of-unicode"></a>Unicode avantajları

Unicode özellikli formların avantajları, Hintçe gibi yalnızca Unicode olan betiklerle çalışma olanağını içerir. Ayrıca, tek bir biçimde birden çok dil kullanabilirsiniz. Unicode 'da, tüm karakterler iki bayt uzunluğundadır, bu nedenle çift baytlık karakterleri temsil etmek için özel bir çaba gerekmez. Ayrıca, tüm platformlarda çalışacak tek bir kod kümesi de yazabilirsiniz. Bu, önceki Visual Basic sürümlerinden bir değişiklik olduğundan, Windows NT ve Windows 98 gibi farklı platformlar için farklı kodlar yazmanız gerekiyordu.

Ancak, bazı denetimler Windows 98 ve Windows Millennium Edition 'da Unicode 'U desteklemez. Bu denetimler, tüm ortak denetimden devraldığı, ANSI olarak Windows kod sayfalarıyla verileri işleyecek. Bu denetimler şunlardır: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar> ve <xref:System.Windows.Forms.StatusBar>. Sonuç olarak, listelenen platformlarda Unicode verilerini bu denetimlerde görüntüleyemezsiniz. Örneğin, Ingilizce bir Windows 98 işletim sisteminde Japonca karakterler görüntüleyemezsiniz.

@No__t-0 ve <xref:System.Windows.Forms.StatusBar> denetimlerinin Unicode kullanan alternatifleri için, bu eski denetimleri değiştirecek <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.StatusStrip> denetimlerini kullanın. Uygulamanızdaki görsel öğeler arasında benzer bir görünüm sağlamak için, <xref:System.Windows.Forms.MainMenu> yerine işleme menüleri için <xref:System.Windows.Forms.MenuStrip> denetimi kullanın. @No__t-0 ve <xref:System.Windows.Forms.StatusStrip> gibi <xref:System.Windows.Forms.MenuStrip> de Unicode karakterleri işleyebilir ve görüntüleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms uygulamaları Genelleştirme](globalizing-windows-forms.md)

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
ms.openlocfilehash: 1b1ac50bde87b22c3ce9ff7524edbf8750976788
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183119"
---
# <a name="encoding-and-windows-forms-globalization"></a>Kodlama ve Windows Forms Genelleştirme
Windows Forms uygulamaları tamamen Unicode-her karakter, hangi platformu, program veya dili ne olursa olsun, benzersiz bir numara tarafından temsil edilen anlamı etkindir. Unicode hakkında daha fazla bilgi için bkz. [Unicode consortium Web sitesi](https://www.unicode.org).  
  
## <a name="benefits-of-unicode"></a>Unicode avantajları  
 Unicode etkin formlar avantajları dahil olan komut dosyaları ile çalışma olanağını salt Unicode, Hintçe gibi. Ayrıca, tek bir form üzerinde birden çok dil kullanabilirsiniz. Unicode tüm karakterleri iki bayt uzunluğunda olduğundan özel çaba çift baytlık karakterler temsil etmek için gereklidir. Ayrıca, tek bir kümesi tüm platformlarda çalışacak bir kod yazabilirsiniz. Bu, tablonuz Windows NT gibi farklı platformlar için farklı kod yazmak Visual Basic'in önceki sürümlerden farklıdır ve [!INCLUDE[win98](../../../../includes/win98-md.md)].  
  
 Ancak, belirli denetimler Unicode desteği olmayan [!INCLUDE[win98](../../../../includes/win98-md.md)] ve Windows Millennium Edition. Tüm ortak denetim devralır, bu denetimler, Windows kod sayfaları ile veri olarak işleyecek [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)]. Bu denetimler: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, ve <xref:System.Windows.Forms.StatusBar>. Sonuç olarak, listelenen platformları üzerinde bu denetimlerde Unicode veriler görüntülenemiyor. Örneğin, Japonca karakterler bir İngilizce görüntüleyemiyor [!INCLUDE[win98](../../../../includes/win98-md.md)] işletim sistemi.  
  
 Unicode uyumlu alternatifleri için <xref:System.Windows.Forms.ToolBar> ve <xref:System.Windows.Forms.StatusBar> denetimlerini kullanmaya <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.StatusStrip> eski bu denetimleri değiştirin kontrol eder. Uygulamanızı görsel öğe arasındaki benzer bir görünümü ve deneyimini korumak için kullanın <xref:System.Windows.Forms.MenuStrip> yerine işleme menü denetimi <xref:System.Windows.Forms.MainMenu>. Gibi <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> ayrıca işleyebilir ve Unicode karakteri görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

[Windows Forms uygulamaları Genelleştirme](globalizing-windows-forms.md)

---
title: Kodlama ve Windows Forms Genelleştirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 16e54e1915370549124c202bce6ad09c4aca1a40
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="encoding-and-windows-forms-globalization"></a>Kodlama ve Windows Forms Genelleştirme
Windows Forms uygulamaları tamamen Unicode her karakter hangi platformu, program veya dil olsun benzersiz bir numara tarafından temsil edilen anlamına gelir, etkinleştirilmiştir. Unicode hakkında daha fazla bilgi için bkz: [Unicode Web sitesine](http://www.unicode.org).  
  
## <a name="benefits-of-unicode"></a>Unicode yararları  
 Unicode etkin formlar avantajları olan komut dosyaları ile çalışma olanağını şunlardır yalnızca Unicode, Hintçe gibi. Ayrıca, tek bir form üzerinde birden çok dil kullanabilirsiniz. Unicode olarak tüm karakterleri iki bayt uzun olduğundan hiçbir özel çaba çift baytlık karakterler temsil etmek için gereklidir. Ayrıca, tüm platformlarda çalışır kod tek bir dizi yazabilirsiniz. Bu, sahip olduğunuz Windows NT gibi farklı platformları için farklı bir kod yazmak Visual Basic önceki sürümlerden farklıdır ve [!INCLUDE[win98](../../../../includes/win98-md.md)].  
  
 Ancak, bazı denetimler Unicode desteklemeyen [!INCLUDE[win98](../../../../includes/win98-md.md)] ve Windows Millennium Edition. Her biri ortak denetiminden devral, bu denetimleri olarak Windows kod sayfaları ile veri işleyecek [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)]. Bu denetimler: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, ve <xref:System.Windows.Forms.StatusBar>. Sonuç olarak, bu denetimlerindeki listelenen platformlar Unicode verilerini görüntüleyemezsiniz. Örneğin, Japonca karakterler İngilizce görüntüleyemiyor [!INCLUDE[win98](../../../../includes/win98-md.md)] işletim sistemi.  
  
 Unicode uyumlu alternatifleri için <xref:System.Windows.Forms.ToolBar> ve <xref:System.Windows.Forms.StatusBar> denetimleri kullanın <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.StatusStrip> bu eski denetimleri Değiştir kontrol eder. Benzer bir görünüm ve kullanımında uygulamanızda görsel öğeleri arasında korumak için kullanmak <xref:System.Windows.Forms.MenuStrip> denetim işleme menüleri yerine için <xref:System.Windows.Forms.MainMenu>. Gibi <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> ayrıca işlemek ve Unicode karakterler görüntüleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms’u Genelleştirme](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)

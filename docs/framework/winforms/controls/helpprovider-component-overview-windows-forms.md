---
title: "HelpProvider Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23a9db5f7c5286eaab50f2499845f7294af878ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider Bileşenine Genel Bakış (Windows Forms)
Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) bileşen bir HTML Yardımı 1.x Yardım dosyası (HTML Yardım Atölyesi ile üretilen bir .chm dosyasını veya bir .htm dosyasının), Windows uygulama ile ilişkilendirmek için kullanılır. Çeşitli şekillerde Yardım sağlayabilirsiniz:  
  
-   Windows Forms denetimleri için bağlama duyarlı Yardım sağlar.  
  
-   Belirli iletişim kutusu veya belirli bir iletişim kutusu denetimlere bağlama duyarlı Yardım sağlar.  
  
-   Ana sayfanın içindekiler tablosu, dizin veya arama işlevi gibi belirli alanlar için bir Yardım dosyasını açın.  
  
## <a name="using-the-help-provider"></a>Yardım sağlayıcısını kullanma  
 Ekleme bir <xref:System.Windows.Forms.HelpProvider> Windows formunuza bileşeni Yardım özelliklerini göstermek için formdaki diğer denetimleri sağlar <xref:System.Windows.Forms.HelpProvider> bileşeni. Bu, Windows formundaki denetimler için Yardım vermenizi sağlar. Yardım dosyası ile ilişkilendirebilirsiniz <xref:System.Windows.Forms.HelpProvider> bileşenini kullanarak <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği. Çağıran sağlanan Yardım türünü belirtin <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> arasında bir değer sağlayarak ve <xref:System.Windows.Forms.HelpNavigator> belirtilen denetim numaralandırması. Anahtar sözcük ya da konu yardımını çağırarak sağladığınız <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> yöntemi.  
  
 İsteğe bağlı olarak, belirli bir Yardım dizeyi başka bir denetimi ile ilişkilendirmek için kullanın <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> yöntemi. Kullanıcı denetimi odağa sahipken F1 tuşuna bastığında bu yöntemi kullanarak bir denetimle ilişkilendirme dize açılır pencerede görüntülenir.  
  
 Varsa <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> , kullanmalısınız ayarlanmadı değil <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> Yardım metni sağlamak için. Her ikisi de ayarladıysanız <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ve Yardım dayalı Yardım dizesi <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> öncelikli olur.  
  
> [!NOTE]
>  Göreli yolu kullanarak sorunlarla karşılaşabilirsiniz zaman belirtmeyi Yardım dosyasının yolu içinde <xref:System.Windows.Forms.Help.ShowHelp%2A> yöntemi veya <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği <xref:System.Windows.Forms.HelpProvider> denetim. Bu nedenle, Yardım dosyasını belirtmek için mutlak dosya yolunu kullandığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Uygulamalarındaki Yardım Sistemleri](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)

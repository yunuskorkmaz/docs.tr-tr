---
title: Yardım sistemleri
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
ms.openlocfilehash: c97a22dbdbdcc0eb282b52e16c4ef40914b1d9e7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742241"
---
# <a name="help-systems-in-windows-forms-applications"></a>Windows Forms Uygulamalarındaki Yardım Sistemleri
Bir uygulamalar geliştiricisi olarak sizin için en önemli kurs, kullanıcılarınız bir yardım sistemi olan bir geliştirici olarak sizin için önemli olan bir yardım sistemidir. Bu, ne zaman karıştırılır, yoksa yönlendirilirler. Windows tabanlı bir uygulamada yardım sistemi sağlamak, [HelpProvider bileşeni](../controls/helpprovider-component-windows-forms.md)kullanılarak kolayca yapılır.  
  
## <a name="different-types-of-help"></a>Farklı yardım türleri  
 Windows Forms <xref:System.Windows.Forms.HelpProvider> bileşeni, bir HTML Yardım 1. x yardım dosyasını (HTML yardım Atölyiyle oluşturulan bir. chm dosyası ya da bir. htm dosyası) Windows tabanlı uygulamanızla ilişkilendirmek için kullanılır. <xref:System.Windows.Forms.HelpProvider> bileşeni, Windows Forms veya belirli denetimlerde denetimler için bağlama duyarlı yardım sağlamak üzere kullanılabilir. Ayrıca <xref:System.Windows.Forms.HelpProvider> bileşeni, bir içindekiler tablosunun ana sayfası, dizin veya arama işlevi gibi belirli alanlara bir yardım dosyası açabilir. <xref:System.Windows.Forms.HelpProvider> bileşeni hakkında genel bilgi için bkz. [HelpProvider Bileşenine Genel Bakış](../controls/helpprovider-component-overview-windows-forms.md). Windows Forms açılan menü yardımını göstermek için <xref:System.Windows.Forms.HelpProvider> bileşenini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: açılan pencere yardımını görüntüleme](how-to-display-pop-up-help.md). Denetime özgü Yardımı göstermek için <xref:System.Windows.Forms.ToolTip> bileşenini kullanma hakkında daha fazla bilgi için bkz. [araç Ipuçlarını kullanarak denetim yardımı](control-help-using-tooltips.md).  
  
 HTML Yardım Atölyesi ile HTML Yardımı 1. x dosyaları oluşturabilirsiniz. HTML Yardımı hakkında daha fazla bilgi için MSDN 'deki "HTML Yardım Atölyesi" veya diğer "HTML Yardımı" konularına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Kullanıcı Yardımını Tümleştirme](integrating-user-help-in-windows-forms.md)
- [HelpProvider Bileşeni](../controls/helpprovider-component-windows-forms.md)
- [ToolTip Bileşeni](../controls/tooltip-component-windows-forms.md)
- [Windows Forms'a Genel Bakış](../windows-forms-overview.md)
- [Windows Forms](../index.md)

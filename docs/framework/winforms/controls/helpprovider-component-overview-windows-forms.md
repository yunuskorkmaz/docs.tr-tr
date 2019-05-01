---
title: HelpProvider Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: 177b61cab99d21a844298632020244fa424d8d2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971229"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider Bileşenine Genel Bakış (Windows Forms)
Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) bileşeni, bir HTML Yardım 1.x Yardım dosyası (HTML Help Workshop ile üretilen bir .chm dosyası veya bir .htm dosyasının), Windows uygulama ile ilişkilendirmek için kullanılır. Çeşitli şekillerde Yardım sağlayabilirsiniz:  
  
- Windows Forms'da denetimleri için bağlama duyarlı Yardım sağlar.  
  
- Bağlama duyarlı Yardım belirli iletişim kutusu ya da belirli bir iletişim kutusu denetimleri sağlar.  
  
- Ana sayfasında içindekiler tablosu, dizin veya bir arama işlevi gibi belirli alanları için bir Yardım dosyasını açın.  
  
## <a name="using-the-help-provider"></a>Yardım sağlayıcısını kullanma  
 Ekleme bir <xref:System.Windows.Forms.HelpProvider> Windows formunuza bileşen Yardım özelliklerini göstermek için form üzerindeki diğer denetimler sağlar <xref:System.Windows.Forms.HelpProvider> bileşeni. Bu, Windows formundaki denetimler için Yardım vermenizi sağlar. Yardım dosyası ile ilişkilendirebilirsiniz <xref:System.Windows.Forms.HelpProvider> bileşenini kullanarak <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği. Yardım çağırarak sağlanan türünü belirtin <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> ve değeri elde <xref:System.Windows.Forms.HelpNavigator> belirtilen denetimi için sabit listesi. Anahtar sözcük veya konuda Yardım almak için çağırarak sağladığınız <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> yöntemi.  
  
 İsteğe bağlı olarak belirli bir Yardım dizeyi başka bir denetimle ilişkilendirilecek kullanın <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> yöntemi. Kullanıcı F1 tuşuna bastığında denetim odağa sahip ancak bu yöntemi kullanarak bir denetimle ilişkilendirme dize açılan bir pencerede görüntülenir.  
  
 Varsa <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> , kullanmanız gerekir, ayarlanmış durumda <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> Yardım metnini sağlamak için. Her ikisi de ayarladıysanız <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ve Yardım temel Yardım dizesi <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> öncelikli olur.  
  
> [!NOTE]
>  Yardım dosyasında da yolunu belirtirken göreli yolu kullanarak sorunlarla karşılaşabilirsiniz <xref:System.Windows.Forms.Help.ShowHelp%2A> yöntemi veya <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği <xref:System.Windows.Forms.HelpProvider> denetimi. Bu nedenle, Yardım dosyasını belirtmek için mutlak dosya yolunu kullandığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Uygulamalarındaki Yardım Sistemleri](../advanced/help-systems-in-windows-forms-applications.md)

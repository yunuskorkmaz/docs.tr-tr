---
title: HelpProvider Bileşenine Genel Bakış
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
ms.openlocfilehash: 74d35dfa39a605cb1e1e85cc3aeda834e1c60669
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738718"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider Bileşenine Genel Bakış (Windows Forms)
Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) bileşeni, bir HTML Yardım 1. x yardım dosyasını (HTML yardım atölyiyle oluşturulan bir. chm dosyası ya da bir. htm dosyası) Windows uygulamanızla ilişkilendirmek için kullanılır. Çeşitli yollarla yardım sağlayabilirsiniz:  
  
- Windows Forms denetimleri için bağlama duyarlı yardım sağlar.  
  
- Belirli bir iletişim kutusu veya iletişim kutusunda belirli denetimler üzerinde bağlama duyarlı yardım sağlar.  
  
- Bir Içindekiler tablosunun ana sayfası, dizin veya arama işlevi gibi belirli alanlara bir yardım dosyası açın.  
  
## <a name="using-the-help-provider"></a>Yardım sağlayıcısını kullanma  
 Windows formunuza bir <xref:System.Windows.Forms.HelpProvider> bileşeni eklemek, formdaki diğer denetimlerin <xref:System.Windows.Forms.HelpProvider> bileşenin yardım özelliklerini kullanıma almasına izin verir. Bu, Windows formunuzdaki denetimler için yardım sağlamanıza olanak sağlar. <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliğini kullanarak bir yardım dosyasını <xref:System.Windows.Forms.HelpProvider> bileşeniyle ilişkilendirebilirsiniz. <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> çağırarak ve belirtilen denetim için <xref:System.Windows.Forms.HelpNavigator> numaralandırmasından bir değer sağlayarak sağlanan yardım türünü belirtirsiniz. <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> yöntemini çağırarak yardım için anahtar sözcüğünü veya konuyu sağlarsınız.  
  
 İsteğe bağlı olarak, belirli bir Yardım dizesini başka bir denetimle ilişkilendirmek için <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> yöntemini kullanın. Bu yöntemi kullanarak bir denetimle ilişkilendirdiğiniz dize, denetim odağa sahipken kullanıcı F1 tuşuna bastığında bir açılır pencerede görüntülenir.  
  
 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ayarlanmamışsa, yardım metnini sağlamak için <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> kullanmanız gerekir. Hem <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> hem de yardım dizesini ayarladıysanız, <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> temel alan yardım, öncelikli olur.  
  
> [!NOTE]
> <xref:System.Windows.Forms.Help.ShowHelp%2A> yönteminde veya <xref:System.Windows.Forms.HelpProvider> denetiminin <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliğindeki yardım dosyasının yolunu belirtirken göreli yolu kullanarak sorunlarla karşılaşabilirsiniz. Bu nedenle, yardım dosyasını belirtmek için mutlak dosya yolunu kullandığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Uygulamalarındaki Yardım Sistemleri](../advanced/help-systems-in-windows-forms-applications.md)

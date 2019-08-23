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
ms.openlocfilehash: cefc590bb3011b282392504a78ac5c393c58493e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965691"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider Bileşenine Genel Bakış (Windows Forms)
Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) bileşeni, bir HTML Yardım 1. x yardım dosyasını (HTML yardım atölyiyle oluşturulan bir. chm dosyası ya da bir. htm dosyası) Windows uygulamanızla ilişkilendirmek için kullanılır. Çeşitli yollarla yardım sağlayabilirsiniz:  
  
- Windows Forms denetimleri için bağlama duyarlı yardım sağlar.  
  
- Belirli bir iletişim kutusu veya iletişim kutusunda belirli denetimler üzerinde bağlama duyarlı yardım sağlar.  
  
- Bir Içindekiler tablosunun ana sayfası, dizin veya arama işlevi gibi belirli alanlara bir yardım dosyası açın.  
  
## <a name="using-the-help-provider"></a>Yardım sağlayıcısını kullanma  
 Windows formunuza <xref:System.Windows.Forms.HelpProvider> bir bileşen eklemek, formdaki diğer denetimlerin, <xref:System.Windows.Forms.HelpProvider> bileşenin yardım özelliklerini kullanıma sunmasına olanak tanır. Bu, Windows formunuzdaki denetimler için yardım sağlamanıza olanak sağlar. Özelliğini kullanarak bir yardım dosyasını <xref:System.Windows.Forms.HelpProvider> bileşeniyle ilişkilendirebilirsiniz. <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ' İ çağırarak <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> ve belirtilen denetim için <xref:System.Windows.Forms.HelpNavigator> Numaralandırmadaki bir değer sağlayarak sağlanan yardım türünü belirtirsiniz. <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> Yöntemini çağırarak yardım için anahtar sözcüğünü veya konuyu sağlarsınız.  
  
 İsteğe bağlı olarak, belirli bir Yardım dizesini başka bir denetimle ilişkilendirmek için <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> yöntemini kullanın. Bu yöntemi kullanarak bir denetimle ilişkilendirdiğiniz dize, denetim odağa sahipken kullanıcı F1 tuşuna bastığında bir açılır pencerede görüntülenir.  
  
 Ayarlanmamışsa, yardım metnini sağlamak için kullanmanız <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> gerekir. <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> Hem hem de <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> Yardım dizesini ayarladıysanız, Yardımı <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> temel alır.  
  
> [!NOTE]
> <xref:System.Windows.Forms.Help.ShowHelp%2A> <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> Denetimin yönteminde veya özelliğindeki yardım dosyasının yolunu belirtirken göreli yolu kullanarak sorunlarla karşılaşabilirsiniz. <xref:System.Windows.Forms.HelpProvider> Bu nedenle, yardım dosyasını belirtmek için mutlak dosya yolunu kullandığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Uygulamalarındaki Yardım Sistemleri](../advanced/help-systems-in-windows-forms-applications.md)

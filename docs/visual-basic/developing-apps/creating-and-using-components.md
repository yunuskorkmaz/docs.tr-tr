---
title: Visual Basic'te Bileşenler Oluşturma ve Kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: b48fb59f0927056c8dba75211b4fffa6f25c5c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-and-using-components-in-visual-basic"></a>Visual Basic'te Bileşenler Oluşturma ve Kullanma
A *bileşen* uygulayan bir sınıf <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> arabirimi ya da uygulayan bir sınıftan türeyen doğrudan veya dolaylı olarak <xref:System.ComponentModel.IComponent>. A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] yeniden kullanılabilir, diğer nesnelerle etkileşim kurabilir ve dış kaynaklara ve tasarım zamanı destek üzerinde denetim sağlar. bir nesne bir bileşendir.  
  
 Bir bileşen olan bir sınıf Visual Studio tümleşik geliştirme ortamında kullanılabilir başka bir deyişle, designable, olmalarını bileşenlerin önemli özelliklerinden biridir. Bir bileşenin Araç Kutusu'na eklenebilir, sürüklenen ve formunuza bırakılan ve bir tasarım yüzeyine yönetilebilir. Tasarım zamanı desteği bileşenleri için temel bildirimi içinde oluşturulan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; bir bileşen Geliştirici temel tasarım zamanı işlevselliği yararlanmak için başka çalışma yapmasına gerek yoktur.  
  
 A *denetim* her ikisi de designable gibi bir bileşen için benzer. Ancak, bir bileşenin çalışmazken bir denetim bir kullanıcı arabirimi sağlar. Bir denetim temel denetim sınıfları birinden türetilmesi gerekir: <xref:System.Windows.Forms.Control> veya <xref:System.Web.UI.Control>.  
  
## <a name="when-to-create-a-component"></a>Bir bileşeni oluşturma zamanı  
 Sınıfınız (örneğin, Web Forms Tasarımcısı ve Windows Forms) yüzey ancak hiçbir kullanıcı arabirimine sahiptir bir tasarım üzerinde kullanılacaksa, bir bileşen olması ve uygulamak <xref:System.ComponentModel.IComponent>, veya doğrudan veya dolaylı olarak uygulayan öğesinden bir sınıf türetin <xref:System.ComponentModel.IComponent>.  
  
 <xref:System.ComponentModel.Component> Ve <xref:System.ComponentModel.MarshalByValueComponent> sınıflardır temel uygulamaları <xref:System.ComponentModel.IComponent> arabirimi. Bu sınıflar arasındaki temel fark olan <xref:System.ComponentModel.Component> sınıfı başvuruya göre sıralanmış sırada <xref:System.ComponentModel.IComponent> değerine göre sıralanmış. Aşağıdaki listede uygulayıcılar için geniş açıklamalar sağlar.  
  
-   Bileşeniniz başvuruya göre sıralanmış gerekiyorsa, türetilen <xref:System.ComponentModel.Component>.  
  
-   Bileşeniniz değerine göre sıralanmış gerekiyorsa, türetilen <xref:System.ComponentModel.MarshalByValueComponent>.  
  
-   Tek devralma nedeniyle temel uygulamaları birinden bileşeniniz türetilemez, uygulama <xref:System.ComponentModel.IComponent>.  
  
## <a name="component-classes"></a>Bileşen Sınıfları  
 <xref:System.ComponentModel> Ad alanı, bileşenleri ve denetimleri çalıştırma ve tasarım zamanı davranışını uygulamak için kullanılan sınıfları sağlar. Bu ad alanı taban sınıfları ve öznitelikleri ve tür dönüştürücüleri uygulama, veri kaynakları bağlama ve bileşenleri lisans arabirimleri içerir.  
  
 Çekirdek Bileşen sınıfları şunlardır:  
  
-   <xref:System.ComponentModel.Component>. İçin temel bir uygulama <xref:System.ComponentModel.IComponent> arabirimi. Bu sınıf, uygulamalar arasında paylaşma nesnesi sağlar.  
  
-   <xref:System.ComponentModel.MarshalByValueComponent>. İçin temel bir uygulama <xref:System.ComponentModel.IComponent> arabirimi.  
  
-   <xref:System.ComponentModel.Container>. Temel uygulamasını <xref:System.ComponentModel.IContainer> arabirimi. Bu sınıf, sıfır veya daha fazla bileşen yalıtır.  
  
 Bileşen lisans için kullanılan sınıflar bazıları şunlardır:  
  
-   <xref:System.ComponentModel.License>. Tüm lisanslar için Özet temel sınıf. Bir bileşenin belirli bir örneği için bir lisans verilir.  
  
-   <xref:System.ComponentModel.LicenseManager>. Özellikleri ve yöntemleri bir lisans için bir bileşen ekleyin ve yönetmenize olanak sağlayan bir <xref:System.ComponentModel.LicenseProvider>.  
  
-   <xref:System.ComponentModel.LicenseProvider>. Bir lisans sağlayıcısı uygulamak için Özet temel sınıf.  
  
-   <xref:System.ComponentModel.LicenseProviderAttribute>. Belirtir <xref:System.ComponentModel.LicenseProvider> sınıf ile kullanmak için sınıf.  
  
 Açıklayan ve bileşenleri sürdürmek için yaygın olarak kullanılan sınıflar.  
  
-   <xref:System.ComponentModel.TypeDescriptor>. Öznitelikler, özellikleri ve olayları gibi bir bileşen için özellikleri hakkında bilgi sağlar.  
  
-   <xref:System.ComponentModel.EventDescriptor>. Bir olay hakkında bilgi sağlar.  
  
-   <xref:System.ComponentModel.PropertyDescriptor>. Bir özellik hakkında bilgi sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Denetim ve Bileşen Yazmada Sorun Giderme](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Sık karşılaşılan sorunları düzeltmek açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms'ta tasarım zamanı desteği erişim](../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 

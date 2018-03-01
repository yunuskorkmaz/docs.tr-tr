---
title: "Visual Basic'te Bileşenler Oluşturma ve Kullanma"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 17c9b7440d60c38ba30d230f8412c3ca1a21830a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="creating-and-using-components-in-visual-basic"></a>Visual Basic'te Bileşenler Oluşturma ve Kullanma
A *bileşen* uygulayan bir sınıf <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> arabirimi ya da uygulayan bir sınıftan türeyen doğrudan veya dolaylı olarak <xref:System.ComponentModel.IComponent>. A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] yeniden kullanılabilir, diğer nesnelerle etkileşim kurabilir ve dış kaynaklara ve tasarım zamanı destek üzerinde denetim sağlar. bir nesne bir bileşendir.  
  
 Hangi bir bileşen olan bir sınıf olarak kullanılabileceği anlamına gelir designable, olmalarını bileşenlerin önemli özelliklerinden biridir [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] tümleşik geliştirme ortamı. Bir bileşenin Araç Kutusu'na eklenebilir, sürüklenen ve formunuza bırakılan ve bir tasarım yüzeyine yönetilebilir. Tasarım zamanı desteği bileşenleri için temel bildirimi içinde oluşturulan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; bir bileşen Geliştirici temel tasarım zamanı işlevselliği yararlanmak için başka çalışma yapmasına gerek yoktur.  
  
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
 

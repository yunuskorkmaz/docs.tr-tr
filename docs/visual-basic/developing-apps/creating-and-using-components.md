---
title: "Visual Basic'te Bileşenler Oluşturma ve Kullanma"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 453d341961207dd851136aa47a52759b0841424d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 Tasarım zamanı desteği hakkında daha fazla bilgi için bkz: [bileşenleri için tasarım zamanı öznitelikleri](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) ve [tasarım zamanı destekleyen genişletme](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
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
 [Sınıf vs. Bileşen vs. Denetimi](http://msdn.microsoft.com/library/db8b842e-44d9-40cc-a0f8-70fd189632c3)  
 Tanımlar *bileşen* ve *denetim*, sınıfları ve bunları arasındaki farklar açıklanmaktadır.  
  
 [Bileşen yazma](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 Bileşenleri ile çalışmaya başlama için yol haritası.  
  
 [Bileşen geliştirme izlenecek yollar](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 Bileşen programlama için adım adım yönerge sağlamanız konulara bağlantılar.  
  
 [Bileşen sınıfları](http://msdn.microsoft.com/library/ce2e5647-e673-4c2b-8125-ffebbd9d71bc)  
 Bir bileşen yolu bileşenlerine erişimi denetleme ve bileşen örnekleri nasıl oluşturulduğunu denetleme bileşen işlevselliği kullanıma sunmak için bir sınıf kılan açıklar.  
  
 [Denetim ve bileşen yazmada sorun giderme](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Sık karşılaşılan sorunları düzeltmek açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms'ta tasarım zamanı desteği erişim](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)  
 [Nasıl yapılır: görünümü ve davranışı denetimlerinin Tasarım modunda genişletme](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b)  
 [Nasıl yapılır: Tasarım modunda denetimler için özel başlatma gerçekleştirir](http://msdn.microsoft.com/library/914eaa03-092f-4556-9160-b8a2a40641d9)

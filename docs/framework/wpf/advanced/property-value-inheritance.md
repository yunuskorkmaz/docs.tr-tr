---
title: Özellik Değeri Kalıtımı
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: 6af356d1c6325714fbc98cd5fe8c3ebc1825fcb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547400"
---
# <a name="property-value-inheritance"></a>Özellik Değeri Kalıtımı
Özellik değeri devralma özelliğidir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sistemi. Özellik değeri devralma ağacında belirli bir özellik değerini en yakın üst öğede herhangi bir yere ayarlanmış olarak bu değer devralma öğeler, üst öğeden elde öğelerinin alt öğeleri sağlar. Sistem büyük olasılıkla bu süreç boyunca tüm sayfa kök recurses şekilde üst öğenin de değerini özellik değeri devralma aracılığıyla elde. Özellik değeri devralma varsayılan özellik sistemi davranış değildir; bir özellik, özellik değeri devralma, alt öğelerde başlatmak bu özelliği neden için belirli meta veri ayarı ile oluşturulmuş olmalıdır.  
  

  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>Özellik değeri devralma kapsama devralma olduğu  
 Burada bir terim olarak "devralma" devralma türleri ve genel nesne odaklı programlama, burada türetilen sınıflar kendi temel sınıflarından üye tanımlarını devral bağlamında oldukça aynı kavram değil. Devralma anlamını ayrıca etkin olduğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: çeşitli temel sınıflarda tanımlanan özellikler türetilmiş için öznitelik olarak açığa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sınıfları öğeleri olarak kullanılan ve kod üyeleri olarak sunulur. Özellik değeri devralma özellikle nasıl özellik değerlerini bir öğeyi başka bir üst-alt ilişkisi öğelerinin bir ağaç içindeki temel alarak devrettiği hakkındadır. Bu öğeleri ağacı içinde tanımladığınız uygulamalar gibi öğeler diğer öğelerin içinde iç içe en doğrudan görülebilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme. Nesnelerin ağaçları de programlı olarak diğer nesnelerin atanmış koleksiyonlarına nesneler ekleyerek oluşturulabilir ve özellik değeri devralma aynı şekilde tamamlanmış ağaçtaki çalışma zamanında çalışır.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Özellik değeri devralma pratik uygulamalar  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Özellik devralma etkin olan çeşitli özellikler içerir. Genellikle bu senaryoda, özellik sayfa başına yalnızca bir kez ayarlanabilir, ancak bu özellik ayrıca temel öğe sınıfları birinin üyesi olduğu ve bu nedenle de alt öğelerinin en sık var uygun olduğu bir özelliği içerirler olur. Örneğin, <xref:System.Windows.FrameworkElement.FlowDirection%2A> hangi yöne aktarılan içeriği özellik denetimleri sunulan ve gerekir sayfada düzenlenmiş. Genellikle, tüm alt öğelerini tutarlı bir şekilde ele alınması için metin akışı kavramının istiyor. Akış yönü kullanıcı veya ortam eylemi tarafından belirli bir düzeyde öğe ağacı sıfırlama herhangi bir nedenle olsaydı, boyunca genellikle sıfırlanması. Zaman <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği devralır yapıldığında, değer yalnızca ayarlanamaz veya uygulamadaki her sayfanın sunum gereksinimlerini kapsayan öğe ağacındaki düzeyinde sıfırlanmalıdır. Hatta ilk varsayılan değer, bu şekilde devralır. Özellik değeri devralma modeli hala akış yönleri karışımına sahip bilerek olduğu nadir durumlarda değerini sıfırlamak ayrı ayrı öğeler sağlar.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Devredilebilir özel özellik yapma  
 Özel özelliğin meta verilerini değiştirerek de kendi özel özellikler devralınabilir yapabilirsiniz. Ancak, bir özelliği olarak devralınabilir bazı performans değerlendirmeleri sahip olup olmadığını unutmayın. Burada bu özelliği yerleşik yerel değerin veya stiller, şablonları veya veri bağlama alınan bir değer yok durumlarda, mantıksal ağaç içindeki tüm alt öğeleri olarak atanan özellik değerlerini devralınabilir bir özelliği sağlar.  
  
 Bir özelliğin değeri devralma katılmak, özel bir oluşturma özelliği, açıklandığı gibi eklenmiş [iliştirilmiş özellik](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md). Özellik meta verileri ile Kaydet (<xref:System.Windows.FrameworkPropertyMetadata>) ve bu meta veri içindeki Seçenekleri ayarları "Inherits" seçeneğini belirtin. Ayrıca bu değer şimdi devralacaktır çünkü özelliği oluşturulmuş varsayılan bir değere sahip olduğundan emin olun. Bir "iliştirilmemiş" bağımlılık özelliği için yaptığınız gibi özelliği bağlı olarak kaydedilen rağmen sahibi türüne özellik get/set erişim "sarmalayıcı" oluşturmak isteyebilirsiniz. Bunu yaptıktan sonra devralınabilir özellik ya da sahip türü veya türetilmiş türlerde doğrudan özellik sarmalayıcısı kullanılarak ayarlanabilir veya üzerlerinde ekli özellik sözdizimi kullanılarak ayarlanabilir <xref:System.Windows.DependencyObject>.  
  
 Ekli özellikler kavramsal genel özelliklerine benzer; herhangi bir değer için denetleyebilirsiniz <xref:System.Windows.DependencyObject> ve geçerli bir sonuç alın. Ekli özellikler için tipik senaryo alt öğeler üzerinde özellik değerlerini ayarlamaktır ve bu senaryo söz konusu özellik her zaman her öğe üzerinde eklenen bir özellik olarak örtük olarak mevcut olan iliştirilmiş bir özellik olması durumunda daha etkilidir (<xref:System.Windows.DependencyObject>) ağacında.  
  
> [!NOTE]
>  Devralma davranışı çalışma zamanı ağacındaki belirli öğe sınırları üzerinden iliştirilmemiş bir özellik için özellik değeri devralma iliştirilmemiş bağımlılık özellikleri için iş gibi görünse de tanımlanmamıştır. Her zaman kullanmak <xref:System.Windows.DependencyProperty.RegisterAttached%2A> belirttiğiniz özellikleri kaydetmek için <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> meta veriler.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Özellik değerlerini ağaç sınırları boyunca devralma  
 Özellik devralma öğeleri ağacının çapraz geçiş yapan çalışır. Bu genellikle mantıksal ağacının paralel ağacıdır. Bununla birlikte, her dahil WPF çekirdek düzeyinde bir nesne gibi bir öğe ağacı tanımlayan biçimlendirmedeki bir <xref:System.Windows.Media.Brush>, kesintili bir mantıksal ağaç oluşturdunuz. True mantıksal ağacının yoluyla kavramsal olarak genişlemez <xref:System.Windows.Media.Brush>, çünkü mantıksal ağacının bir WPF çerçeve düzeyi kavramıdır. Bu yöntemleri kullanarak sonuçları yansıtılmış görebilirsiniz <xref:System.Windows.LogicalTreeHelper>. Ancak, özellik değeri devralma bu mantıksal ağacında boşluğunu ve devralınabilir özellik iliştirilmiş bir özellik ve kasıtlı devralmayı engelleme sınır kayıtlı olduğu sürece, devralınan değerleri hala geçirebilirsiniz (bir gibi<xref:System.Windows.Controls.Frame>) ile karşılaşıldı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımlılık Özelliği Meta Verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Ekli Özelliklere Genel Bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [Bağımlılık Özelliği Değer Önceliği](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)

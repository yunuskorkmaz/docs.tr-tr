---
title: Özellik Değeri Kalıtımı
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: e6b16bc3fc482e0f640f8b2d083392e6f94de618
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520593"
---
# <a name="property-value-inheritance"></a>Özellik Değeri Kalıtımı
Özellik değeri kalıtımı özelliğidir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sistemi. Özellik değeri kalıtımı alt öğelerini üstten öğeleri, bu değer en yakın üst öğede herhangi bir yerde ayarlanmış olarak devralınması belirli bir özellik değeri kalıtımı ağacındaki sağlar. Sistem büyük olasılıkla tüm sayfa kök recurses için üst öğe Ayrıca özellik değeri devralma yoluyla değeri elde. Özellik değeri devralma varsayılan özellik sistemi davranış değildir; bir özellik alt öğeleri üzerinde özellik değeri kalıtımı başlatmak bu özelliği neden için özel meta verileri ayarıyla oluşturulmalıdır.  
  

  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>Özellik değeri kalıtımı olan kapsama inheritance'tır  
 Burada bir terim olarak "devralma" tam olarak aynı kavram olarak devralma türleri ve genel nesne yönelimli programlama, burada türetilmiş sınıflar temel sınıflarının işaretçilerine üye tanımları devral bağlamında değil. Devralmanın anlamı da etkin olduğu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: çeşitli temel sınıflarında tanımlanan özellikler, öznitelik olarak sunulur, türetilmiş için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sınıflar öğeleri olarak kullanılan ve kod üyeleri olarak sunulur. Özellik değeri kalıtımı özellikle nasıl özellik değerlerini bir öğeden diğerine öğe ağacındaki içinde üst-alt ilişkileri göndermemeniz devrettiği hakkındadır. Öğe ağacı içinde tanımladığınız uygulamalar gibi diğer öğeleri içinde öğeleri iç içe doğrudan görülebilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme. Nesnelerin ağaçlarını de program aracılığıyla nesneleri diğer nesnelerin atanan koleksiyonlarına ekleyerek oluşturulabilir ve özellik değeri kalıtımı aynı şekilde tamamlanmış ağaçtaki çalışma zamanında çalışır.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Özellik değeri devralma pratik uygulamalar  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Özelliği devralım etkin olan çeşitli özellikler içerir. Genellikle bu senaryoda, özellik sayfa başına yalnızca bir kez ayarlanabilir, ancak bu özellik ayrıca temel öğe sınıflarından birinin üyesidir ve bu nedenle de alt öğeleri çoğunda var uygun olduğu bir özelliği içerirler oluşur. Örneğin, <xref:System.Windows.FrameworkElement.FlowDirection%2A> özellik denetimleri hangi yönde, içerik akışı yapılan işlemler sunulan verilecek ve sayfasında. Genellikle, tüm alt öğeleri tutarlı bir şekilde işlenecek metin akış kavramı istersiniz. Akış yönü, belli bir düzeyde öğe ağacı kullanıcı ya da ortam işlem tarafından sıfırlama herhangi bir nedenle olsaydı, boyunca genellikle sıfırlanması. Zaman <xref:System.Windows.FrameworkElement.FlowDirection%2A> devralmak için özelliği yapıldığında, değeri yalnızca ayarlanabilir veya uygulamada her sayfanın sunum gereksinimlerini kapsayan öğe ağacı düzeyinde sıfırlanmalıdır. Bu şekilde bile ilk varsayılan değeri devralır. Özellik değeri devralma modeli burada akış yönleri bir karışımını sahip kasıtlıdır nadiren değeri sıfırlamak ayrı ayrı öğeler yine de sağlar.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Özel bir özellik alınabilir hale getirme  
 Özel özelliğin meta verilerini değiştirerek, ayrıca kendi özel özellikler devralınabilir yapabilirsiniz. Ancak, bir özelliği olarak devralınabilir bazı performans değerlendirmeleri olduğunu unutmayın. Burada bu özellik bir belirlenen yerel değer veya stiller, şablonlar veya veri bağlama elde ettiği değerle yok durumlarda, mantıksal ağaç içindeki tüm alt öğeleri olarak atanan özellik değerlerini devralınabilir bir özelliği sağlar.  
  
 Bir özelliğin değeri Devralmada rol oynayan, bir özel oluştur, açıklandığı ekli özellik [iliştirilmiş özellik](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md). Özelliği meta verilerle kaydetme (<xref:System.Windows.FrameworkPropertyMetadata>) ve bu meta veri içindeki Seçenekleri ayarları "Inherits" seçeneğini belirtin. Ayrıca çünkü bu değeri artık devralır özelliği oluşturulmuş varsayılan bir değere sahip olduğundan emin olun. Bir "iliştirilmemiş" bağımlılık özelliği için yaptığınız gibi özelliği olarak bağlanmış kayıtlı olsa da, bir özellik "sarmalayıcı" get/set erişim için sahip türü üzerinde oluşturmak isteyebilirsiniz. Bunu yaptıktan sonra devralınabilir özellik ya da sahibi veya türetilmiş türleri üzerinde doğrudan özellik sarmalayıcısını kullanarak ayarlanabilir veya herhangi bir ekli özellik sözdizimini kullanarak ayarlanabilir <xref:System.Windows.DependencyObject>.  
  
 Ekli özelliklere genel özelliklerine kavramsal olarak benzer; herhangi bir değer denetleyebilirsiniz <xref:System.Windows.DependencyObject> ve geçerli bir sonuç alın. Tipik bir senaryo iliştirilmiş özellikler için alt öğeler üzerinde özellik değerlerini ayarlamak için ve bu senaryo söz konusu özellik her zaman örtük olarak ekli özelliği her öğe üzerinde olarak mevcut olan ekli özelliği ise daha etkili (<xref:System.Windows.DependencyObject>) ağacında.  
  
> [!NOTE]
>  Özellik değeri kalıtımı iliştirilmemiş bağımlılık özellikleri için çalışma gibi görünse de, belirli çalışma zamanı ağacındaki öğe sınırları üzerinden iliştirilmemiş bir özellik için devralma davranışı tanımsızdır. Her zaman <xref:System.Windows.DependencyProperty.RegisterAttached%2A> belirttiğiniz özellikleri kaydetmek için <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> meta verilerinde.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Özellik değerlerini ağaç sınırlarında devralıyor  
 Özellik devralma öğelerin bir ağacının çapraz geçişi ile çalışır. Bu genellikle için mantıksal ağaç paralel ağacıdır. Ancak, her dahil WPF çekirdek düzeyinde bir nesne gibi bir öğe ağacı tanımlar biçimlendirme içinde bir <xref:System.Windows.Media.Brush>, kesintili bir mantıksal ağaç oluşturdunuz. True mantıksal ağacı yoluyla kavramsal olarak genişlemez <xref:System.Windows.Media.Brush>, mantıksal ağacı bir WPF çerçeve düzeyi kavramıdır. Bu yöntemleri kullanırken sonuçları yansıtılmış gördüğünüz <xref:System.Windows.LogicalTreeHelper>. Ancak, özellik değeri kalıtımı bu boşluğu mantıksal ağaçta arasında köprü olabilir ve devralınabilir özelliği ekli özelliği ve bilinçli devralmayı engelleme sınır kayıtlı olduğu sürece, devralınan değerleri yine de geçirebilirsiniz (bir gibi<xref:System.Windows.Controls.Frame>) karşılaşıldı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağımlılık Özelliği Meta Verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
- [Ekli Özelliklere Genel Bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
- [Bağımlılık Özelliği Değer Önceliği](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)

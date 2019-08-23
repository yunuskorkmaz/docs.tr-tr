---
title: Özellik Değeri Kalıtımı
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: eb757d039437d9954a2b648c5f758dffa3fee3d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958355"
---
# <a name="property-value-inheritance"></a>Özellik Değeri Kalıtımı
Özellik değeri devralma [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özelliği, özellik sisteminin bir özelliğidir. Özellik değeri kalıtımı, bir öğe ağacındaki alt öğelerin üst öğeden belirli bir özelliğin değerini elde etmesini sağlar ve bu değeri en yakın üst öğede herhangi bir yerde ayarlandığı şekilde devralarak. Üst öğe, özellik değeri devralma yoluyla değerini elde edebilir, bu sayede sistem, sayfa köküne kadar olan her şekilde yinelenen olabilecek. Özellik değeri kalıtımı varsayılan özellik sistem davranışı değildir; özelliğin alt öğelerde Özellik değeri devralmayı başlatmasını sağlamak için belirli bir meta veri ayarıyla bir özellik oluşturulmalıdır.  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>Özellik değeri devralımı kapsama devralma  
 Burada bir terim olarak "devralma", türetilmiş sınıfların kendi temel sınıflarından üye tanımlarını devraldığı türler ve genel nesne odaklı programlama bağlamında devralmayla aynı kavram değildir. Devralmanın bu anlamı ' de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]de etkindir: çeşitli temel sınıflarda tanımlı özellikler, öğeler olarak kullanıldığında türetilmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sınıflar için öznitelikler olarak sunulur ve kod için üye olarak sunulur. Özellik değeri kalıtımı özellikle özellik değerlerinin bir öğe ağacı içindeki üst-alt ilişkileri temel alınarak bir öğeden diğerine nasıl devralınabileceği hakkında bir özelliktir. Bu öğe ağacı, biçimlendirme içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulama tanımladığınız sırada öğeleri diğer öğelerin içine yuvalandığınızda doğrudan görünür. Nesne ağaçları Ayrıca, diğer nesnelerin belirlenen koleksiyonlarına nesne eklenerek programlı bir şekilde oluşturulabilir ve özellik değeri devralma, çalışma zamanında tamamlanmış ağaçta aynı şekilde çalışır.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Özellik değeri devralmanın pratik uygulamaları  
 API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 'ler, özellik devralımı etkin olan çeşitli özellikler içerir. Genellikle, bu senaryo, özelliğin sayfa başına yalnızca bir kez ayarlandığı, ancak bu özelliğin temel öğe sınıflarından birinin bir üyesi olduğu ve bu nedenle alt öğelerin çoğunda da bulunduğu bir özelliği içerirler. Örneğin, <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği sayfada hangi yöne akan içeriğin sunulduğunu ve düzenlendiğini denetler. Genellikle, metin akışı kavramının tüm alt öğeler boyunca tutarlı bir şekilde işlenmesini istersiniz. Akış yönü, bazı bir nedenle Kullanıcı veya ortam eylemi tarafından bir öğe ağacı düzeyinde sıfırlanırsa, genellikle üzerinde sıfırlanması gerekir. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Özelliği devralma için yapıldığında, değer yalnızca uygulamadaki her bir sayfanın sunum ihtiyaçlarını kapsayan öğe ağacındaki düzeyde ayarlanmalıdır veya sıfırlanır. İlk varsayılan değer bile bu şekilde devralınır. Özellik değeri devralma modeli yine de tek tek öğelerin, bir akış yönü karışımı olan nadir durumlar için değeri sıfırlamasına olanak sağlar.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Özel bir özelliğin devralınabilir hale getirilmesi  
 Özel bir özelliğin meta verilerini değiştirerek, kendi özel özelliklerinizi de devralınabilir hale getirebilirsiniz. Ancak, bir özelliği devralınabilir olarak belirlemek için bazı performans hususları olduğunu unutmayın. Bu özelliğin bir yerel değeri veya stiller, şablonlar ya da veri bağlama yoluyla elde edilen bir değeri olmadığı durumlarda devralınabilir bir özellik, atanan özellik değerlerini mantıksal ağaçtaki tüm alt öğelere sağlar.  
  
 Bir özelliğin değer devralıma katılmasını sağlamak için, [ekli özelliği kaydetme](how-to-register-an-attached-property.md)bölümünde açıklandığı gibi özel bir iliştirilmiş özellik oluşturun. Özelliği meta veriler (<xref:System.Windows.FrameworkPropertyMetadata>) ile kaydedin ve bu meta veriler içindeki seçenekler ayarlarındaki "devralma" seçeneğini belirtin. Ayrıca, özelliğin bir varsayılan değere sahip olduğundan emin olun, çünkü bu değerin şimdi devralması gerekir. Özelliği iliştirilmiş olarak kaydettirdiğiniz halde, "iliştirilmemiş" bağımlılık özelliğinde olduğu gibi, sahip türü üzerinde get/set erişimi için "sarmalayıcı" özelliği oluşturmak isteyebilirsiniz. Bunu yaptıktan sonra, devralınabilir özellik sahip türü veya türetilmiş türler üzerinde doğrudan özellik sarmalayıcısı kullanılarak ayarlanabilir veya herhangi bir <xref:System.Windows.DependencyObject>üzerinde iliştirilmiş özellik sözdizimi kullanılarak ayarlanabilir.  
  
 Eklenmiş Özellikler kavramsal olarak genel özelliklere benzer; her türlü <xref:System.Windows.DependencyObject> değeri denetleyebilir ve geçerli bir sonuç elde edebilirsiniz. Ekli Özellikler için tipik senaryo alt öğelerinde özellik değerlerini ayarlamak ve söz konusu özellik her zaman her bir öğede iliştirilmiş bir özellik olarak örtülü olarak bulunan iliştirilmiş bir özellik ise, bu senaryo daha etkilidir. (<xref:System.Windows.DependencyObject>).  
  
> [!NOTE]
> Özellik değeri devralımı eklenmemiş bağımlılık özellikleri için çalışıyor gibi görünse de, çalışma zamanı ağacındaki belirli öğe sınırları aracılığıyla eklenmemiş olmayan bir özelliğin devralma davranışı tanımsızdır. Meta verilerde <xref:System.Windows.DependencyProperty.RegisterAttached%2A> belirttiğiniz <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> özellikleri kaydetmek için her zaman kullanın.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Ağaç sınırları genelinde özellik değerlerini devralma  
 Özellik devralma bir öğe ağacında geçiş yaparak işe yarar. Bu ağaç genellikle mantıksal ağaca paraleldir. Ancak, bir <xref:System.Windows.Media.Brush>, gibi bir öğe ağacını tanımlayan İşaretlemede bir WPF Core düzeyi nesnesi eklediğinizde, ardışık bir mantıksal ağaç oluşturmuş olursunuz. Mantıksal ağaç bir WPF çerçeve düzeyi kavramı olduğundan, gerçek <xref:System.Windows.Media.Brush>bir mantıksal ağaç kavramsal olarak ' ı genişletir. Yöntemlerini kullanırken Bunun sonuçlara yansıtıldığını görebilirsiniz <xref:System.Windows.LogicalTreeHelper>. Ancak, özellik değeri kalıtımı mantıksal ağaçta bu boşluğu köprülemez ve devralınabilir özellik iliştirilmiş bir özellik olarak kaydedildiği ve bilinçli Devralma-engelleme sınırı <xref:System.Windows.Controls.Frame>olmadığısürecedevralınandeğerleriaracılığıylageçirebilir.) ile karşılaşıldı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Ekli Özelliklere Genel Bakış](attached-properties-overview.md)
- [Bağımlılık Özelliği Değer Önceliği](dependency-property-value-precedence.md)

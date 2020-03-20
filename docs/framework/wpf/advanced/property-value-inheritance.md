---
title: Özellik Değeri Kalıtımı
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: b63f307d9edffd14315d383d8e06419fa141aee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187189"
---
# <a name="property-value-inheritance"></a>Özellik Değeri Kalıtımı
Özellik değeri devralma [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sisteminin bir özelliğidir. Özellik değeri devralma, öğeler in bir ağacındaki alt öğelerin, belirli bir özelliğin değerini üst öğelerden elde etmesini sağlayarak, bu değeri en yakın üst öğenin herhangi bir yerinde ayarlanan değeri devralır. Üst öğe de özellik değeri devralma yoluyla değerini elde etmiş olabilir, bu nedenle sistem potansiyel olarak sayfa köküne kadar tüm lanetler. Özellik değeri devralma varsayılan özellik sistemi davranışı değildir; bu özelliğin alt öğeler üzerinde özellik değeri devralma başlatmasına neden olmak için belirli bir meta veri ayarı ile bir özellik oluşturulmalıdır.  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>
## <a name="property-value-inheritance-is-containment-inheritance"></a>Özellik Değeri Devralma Koruma Kalıtım mı  
 Burada bir terim olarak "kalıtım" türleri ve türemiş sınıfların temel sınıflarından üye tanımları devraldığı genel nesne yönelimli programlama bağlamında devralma kavramıyla tamamen aynı kavram değildir. Kalıtımın anlamı da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]etkindir: çeşitli temel sınıflarda tanımlanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özellikler, öğe olarak kullanıldığında türemiş sınıflar için öznitelikler olarak ortaya çıkarır ve kod için üye olarak ortaya çıkarır. Özellik değeri devralma, özellikle özellik değerlerinin bir öğe ağacındaki üst-alt ilişkileri temelinde bir öğeden diğerine nasıl devralınabileceğiyle ilgilidir. Biçimlendirmedeki uygulamaları tanımlarken, bu öğeler ağacı en doğrudan diğer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğelerin içine giren öğelerde görünür. Nesnelerin ağaçları da diğer nesnelerin atanmış koleksiyonlarına nesneleri ekleyerek programlı olarak oluşturulabilir ve özellik değeri kalıtım çalışma zamanında bitmiş ağaç aynı şekilde çalışır.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>
## <a name="practical-applications-of-property-value-inheritance"></a>Gayrimenkul Değeri Devralma Pratik Uygulamaları  
 API'ler, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik devralma özelliği etkin olan birkaç özellik içerir. Genellikle, bunlar için senaryo, özelliğin sayfa başına yalnızca bir kez ayarlanmasıuygun, ancak bu özelliğin aynı zamanda temel öğe sınıflarından birinin üyesi olduğu ve böylece alt öğelerin çoğunda da bulunacağı bir özellik içermeleridir. Örneğin, <xref:System.Windows.FrameworkElement.FlowDirection%2A> özellik hangi yönde akan içeriğin sayfada sunulması ve düzenlenmesi gerektiğini denetler. Genellikle, metin akışı kavramının tüm alt öğeler de tutarlı bir şekilde ele alınmasını istersiniz. Akış yönü bir nedenle kullanıcı veya ortam eylemi tarafından öğe ağacının bazı düzeylerinde sıfırlandı, genellikle boyunca sıfırlanmalıdır. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Özellik devralınması için yapıldığında, değeryalnızca bir kez ayarlanması veya uygulamadaki her sayfanın sunu gereksinimlerini kapsayan öğe ağacındaki düzeyde sıfırlanması gerekir. Hatta ilk varsayılan değer bu şekilde devralınacaktır. Özellik değeri devralma modeli, akış yönergelerinin bir karışımının kasıtlı olduğu nadir durumlar için değeri sıfırlamaya devam eder.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>
## <a name="making-a-custom-property-inheritable"></a>Özel Bir Özellik Devredilebilir Yapma  
 Özel bir özelliğin meta verilerini değiştirerek, kendi özel özelliklerinizi de devralınabilir hale getirebilirsiniz. Ancak, bir özelliği devralabilir olarak atamanın bazı performans konuları olduğunu unutmayın. Bu özelliğin yerleşik bir yerel değeri veya stiller, şablonlar veya veri bağlama yoluyla elde edilen bir değere sahip olmadığı durumlarda, devralınabilir özellik, atanan özellik değerlerini mantıksal ağaçtaki tüm alt öğelere sağlar.  
  
 Bir özelliğin değer devralmasına katılmasını sağlamak için, [Ekli Mülkü Kayded'de](how-to-register-an-attached-property.md)açıklandığı gibi özel bir özellik oluşturun. Özelliği meta verilerle<xref:System.Windows.FrameworkPropertyMetadata>kaydedin ( ) ve bu meta verilerdeki seçenekler ayarlarında "Devralmalar" seçeneğini belirtin. Ayrıca, bu değer artık devralınacağı için özelliğin yerleşik bir varsayılan değere sahip olduğundan emin olun. Özelliği ekli olarak kaydetmiş olsanız da, tıpkı "bağlı olmayan" bir bağımlılık özelliğinde olduğu gibi, sahibi türüne erişim sağlamak/ayarlamak için bir özellik "sarıcı" oluşturmak da isteyebilirsiniz. Bunu yaptıktan sonra, devralınabilir özellik ya sahibi türü veya türetilmiş türleri üzerinde doğrudan özellik sarıcı kullanılarak ayarlanabilir, ya <xref:System.Windows.DependencyObject>da herhangi bir ekli özellik sözdizimi kullanılarak ayarlanabilir .  
  
 Ekli özellikler kavramsal olarak genel özelliklere benzer; herhangi bir <xref:System.Windows.DependencyObject> değer için kontrol edebilir ve geçerli bir sonuç elde edebilirsiniz. Bağlı özellikler için tipik senaryo, alt öğeler üzerinde özellik değerlerini ayarlamaktır ve söz konusu özellik ağaçtaki her öğede ()<xref:System.Windows.DependencyObject>her zaman örtülü olarak bulunan ekli bir özellikse, bu senaryo daha etkilidir.  
  
> [!NOTE]
> Özellik değeri devralma bağlı olmayan bağımlılık özellikleri için çalışıyor gibi görünse de, çalışma zamanı ağacında belirli öğe sınırları üzerinden bağlı olmayan bir özellik için devralma davranışı tanımsız. Meta <xref:System.Windows.DependencyProperty.RegisterAttached%2A> verilerde belirttiğiniz <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> özellikleri her zaman kaydetmek için kullanın.  
  
<a name="InheritanceContext"></a>
## <a name="inheriting-property-values-across-tree-boundaries"></a>Ağaç Sınırları Arasında Özellik Değerlerini Devralma  
 Özellik devralma öğeleri bir ağaç geçiş yaparak çalışır. Bu ağaç genellikle mantıksal ağaca paraleldir. Ancak, biçimlendirmeye bir WPF çekirdek düzeyi nesnesi eklediğinizde, örneğin, <xref:System.Windows.Media.Brush>bir , kesintisiz mantıksal ağaç oluşturdunuz. Mantıksal ağaç WPF çerçeve düzeyi <xref:System.Windows.Media.Brush>kavramı olduğundan, gerçek bir mantıksal ağaç kavramsal olarak , Bu yöntemleri kullanırken sonuçlara yansıyan <xref:System.Windows.LogicalTreeHelper>görebilirsiniz. Ancak, özellik değeri devralma mantıksal ağaçta bu boşluğu köprü ve hala devralınan değerleri geçirebilirsiniz, sürece devredilebilir özellik ekli bir özellik olarak <xref:System.Windows.Controls.Frame>kaydedildi ve hiçbir kasıtlı devralma engelleme sınırı (gibi) karşılaşılan.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Ekli Özelliklere Genel Bakış](attached-properties-overview.md)
- [Bağımlılık Özelliği Değer Önceliği](dependency-property-value-precedence.md)

---
title: XamlWriter.Save'in Serileştirme Sınırlamaları
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 0416b92a6264e6a8261355197b4ab2fa61f80ef2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582589"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save'in Serileştirme Sınırlamaları
API <xref:System.Windows.Markup.XamlWriter.Save%2A>, bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamasının içeriğini [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir dosya olarak seri hale getirmek için kullanılabilir. Ancak, tam olarak serileştirildiği bazı önemli sınırlamaları vardır. Bu sınırlamalar ve bazı genel konular bu konuda belgelenmiştir.  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Çalışma zamanı, tasarım zamanı gösterimi değil  
 @No__t_0 çağrısıyla serileştirilin temel felseı, sonucun, çalışma zamanında serileştirilmekte olan nesnenin bir temsili olacağı şeydir. Özgün [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyanın birçok tasarım zamanı özelliği, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bellek içi nesneler olarak yüklendiği zaman en iyi duruma getirilebilir veya kaybedilebilir ve seri hale getirmek için <xref:System.Windows.Markup.XamlWriter.Save%2A> çağırdığınızda korunmaz. Serileştirilmiş sonuç, uygulamanın oluşturulmuş mantıksal ağacının etkili bir gösterimidir, ancak bunu üreten orijinal [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] değildir. Bu sorunlar, kapsamlı bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tasarım yüzeyi kapsamında <xref:System.Windows.Markup.XamlWriter.Save%2A> Serileştirmeyi kullanmayı son derece zorlaştırır.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>Serileştirme kendi Içinde  
 Seri hale getirilmiş <xref:System.Windows.Markup.XamlWriter.Save%2A> çıkışı kendi içindedir; seri hale getirilen her şey tek bir kök öğe olan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tek bir sayfanın içinde bulunur ve URI dışında dış başvurular içermez. Örneğin, sayfanız uygulama kaynaklarından kaynaklara başvuruyorsa, bunlar serileştirilen sayfanın bir bileşeni gibi görünür.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Uzantı başvuruları başvuru başvurusu  
 @No__t_0 veya `Binding` gibi çeşitli biçimlendirme uzantısı biçimleri tarafından oluşturulan nesnelere yapılan ortak başvurular, serileştirme işlemi tarafından başvurulacaktır. Bunlar zaten uygulama çalışma zamanı tarafından bellek içi nesneler oluşturulduğu sırada başvurmuş ve <xref:System.Windows.Markup.XamlWriter.Save%2A> mantığı, seri hale getirilmiş çıktıya bu tür başvuruları geri yüklemek için özgün [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] geri ziyaret etmez. Bu, tüm veri kaynağı veya kaynak elde edilen değeri, çalışma zamanı gösterimi tarafından en son kullanılan değeri, ancak bu tür bir değeri yerel olarak başka bir değer kümesinden ayırt etmek için yalnızca sınırlı veya dolaylı bir özellik olacak şekilde dondurur. Görüntüler Ayrıca, özgün kaynak başvuruları yerine projede var olan görüntülere nesne başvuruları olarak serileştirilir. Aynı sayfada belirtilen kaynaklar bile, kaynak koleksiyonunun bir anahtarı olarak korunmak yerine, başvurdukları noktaya serileştirilmiş olarak görülür.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>Olay Işleme korunmaz  
 @No__t_0 üzerinden eklenen olay işleyicileri serileştirildiğinde, korunmaz. arka plan kodu olmayan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (ve ayrıca ilişkili x:Code mekanizması olmadan) çalışma zamanı yordamsal mantığını serileştirmenin bir yolu yoktur. Serileştirme bağımsız olduğundan ve mantıksal ağacıyla sınırlı olduğundan, olay işleyicilerini depolamak için hiçbir tesis yoktur. Sonuç olarak, olay işleyicisi öznitelikleri, hem özniteliğin kendisi hem de işleyiciyi isimsiz olan dize değeri, çıkış [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaldırılır.  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>XAMLWriter. Save kullanımı için gerçekçi senaryolar  
 Burada listelenen sınırlamalar oldukça önemli olsa da, serileştirme için <xref:System.Windows.Markup.XamlWriter.Save%2A> kullanmaya yönelik birkaç uygun senaryo vardır.  
  
- Vektör veya grafik çıkışı: işlenmiş alanın çıktısı, yeniden yüklendiğinde aynı vektör veya grafikleri yeniden oluşturmak için kullanılabilir.  
  
- Zengin metin ve akış belgeleri: metin ve tüm öğe biçimlendirmesi ve içindeki öğe içerme, çıktıda korunur. Bu, bir pano işlevini yaklaşık olarak gösteren mekanizmalar için yararlı olabilir.  
  
- İş nesnesi verilerini koruma: [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veriler gibi özel öğelerde veri depoladıysanız, iş nesneleriniz için özel oluşturucular sağlama ve başvuru özelliği değerleri için dönüştürme gibi temel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kuralları ve bu iş nesneleri nesneler serileştirme aracılığıyla alınabilir.

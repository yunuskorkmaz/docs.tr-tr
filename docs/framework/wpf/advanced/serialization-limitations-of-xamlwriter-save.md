---
title: XamlWriter.Save'in Serileştirme Sınırlamaları
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 96e917898320fb5d49f4e7dfc27daa7750af9d41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174374"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save'in Serileştirme Sınırlamaları
API, <xref:System.Windows.Markup.XamlWriter.Save%2A> bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamanın içeriğini [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya olarak seri hale getirmek için kullanılabilir. Ancak, serileştirilmiş tam olarak ne bazı önemli sınırlamalar vardır. Bu sınırlamalar ve bazı genel hususlar bu konuda belgelenmiştir.  

<a name="Run_Time__Not_Design_Time_Representation"></a>
## <a name="run-time-not-design-time-representation"></a>Çalışma Zamanı, Tasarım-Zaman Gösterimi Değil  
 Bir çağrı yla serileştirilen şeyin temel <xref:System.Windows.Markup.XamlWriter.Save%2A> felsefesi, sonucun çalışma zamanında serihale edilen nesnenin bir temsili olmasıdır. Özgün [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyanın birçok tasarım zamanı özelliği, bellek nesneleri olarak yüklenene kadar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zaten en iyi duruma getirilmiş veya <xref:System.Windows.Markup.XamlWriter.Save%2A> kaybolmuş olabilir ve serihale çağırdığınızda korunmuyor. Serileştirilmiş sonuç, uygulamanın oluşturulmuş mantıksal ağacının etkili bir temsilidir, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ancak onu üreten orijinalin etkin bir temsilidir. Bu sorunlar, serileştirmeyi <xref:System.Windows.Markup.XamlWriter.Save%2A> kapsamlı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir tasarım yüzeyinin parçası olarak kullanmayı son derece zorlaştırır.  
  
<a name="Serialization_is_Self_Contained"></a>
## <a name="serialization-is-self-contained"></a>Serileştirme Kendi Kendine Yeten  
 Serileştirilmiş çıktı <xref:System.Windows.Markup.XamlWriter.Save%2A> sıyrıktır; seri hale getirilen her [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şey tek bir sayfa içinde, tek bir kök öğesi ile bulunur ve URI'ler dışında harici referanslar içermez. Örneğin, sayfanız uygulama kaynaklarından kaynaklara başvuruyorsa, bunlar seri hale getirilen sayfanın bir bileşeni gibi görünür.  
  
<a name="Extension_References_are_Dereferenced"></a>
## <a name="extension-references-are-dereferenced"></a>Uzantı Başvuruları Dereferenced edilir  
 Çeşitli biçimlendirme uzantısı biçimleri tarafından yapılan nesnelere `StaticResource` yapılan `Binding`yaygın başvurular, serileştirme işlemi tarafından başvurudan çıkarılacaktır. Bunlar zaten bellek nesneleri uygulama çalışma zamanı tarafından oluşturulan zamanda dereferenced edildi <xref:System.Windows.Markup.XamlWriter.Save%2A> ve mantık serileştirilmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çıktı bu tür başvuruları geri yüklemek için özgün yeniden ziyaret etmez. Bu, veri yle bağlanan veya elde edilen herhangi bir değeri, çalışma zamanı gösterimi tarafından en son kullanılan değer olarak dondurur ve bu tür bir değeri yerel olarak ayarlanan diğer değerlerden yalnızca sınırlı veya dolaylı olarak ayırt etme yeteneği yle birlikte. Görüntüler, orijinal kaynak başvuruları olarak değil, projede var oldukları gibi, resimlere nesne başvuruları olarak seri hale getirilir, dosya adı veya URI başlangıçta başvurulan ne olursa olsun kaybedilir. Aynı sayfa içinde bildirilen kaynaklar bile, kaynak koleksiyonunun anahtarı olarak korunmak yerine, başvurulan noktaya seri olarak seri olarak verilir.  
  
<a name="Event_Handling_is_Not_Preserved"></a>
## <a name="event-handling-is-not-preserved"></a>Olay İşleme Korunmuyor  
 Eklenen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olay işleyicileri seri hale getirildiğinde, bunlar korunmaz. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kod arkası olmadan (ve ayrıca ilgili x:Kod mekanizması olmadan) çalışma zamanı yordam mantığını serihale getirmenin bir yolu yoktur. Serileştirme bağımsız olduğundan ve mantıksal ağaçla sınırlı olduğundan, olay işleyicilerini depolamak için bir tesis yoktur. Sonuç olarak, olay işleyicisi öznitelikleri, hem öznitelik kendisi ve işleyici isimleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dize değeri, çıktı kaldırılır.  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>XAMLWriter.Save kullanımı için Gerçekçi Senaryolar  
 Burada listelenen sınırlamalar oldukça önemli olsa da, serileştirme <xref:System.Windows.Markup.XamlWriter.Save%2A> için kullanmak için hala birkaç uygun senaryo vardır.  
  
- Vektör veya grafik çıktısı: İşlenen alanın çıktısı, yeniden yüklendiğinde aynı vektörü veya grafikleri yeniden üretmek için kullanılabilir.  
  
- Zengin metin ve akış belgeleri: Metin ve içindeki tüm öğe biçimlendirme ve eleman kapsama çıktıkorunur. Bu, pano işlevini yaklaşık mekanizmalar için yararlı olabilir.  
  
- İş nesnesi verilerinin korunması: İş nesneleriniz özel oluşturucular ve başvuru salyoluyla özellik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] değerleri için dönüştürme sağlama gibi temel kuralları izlediği sürece, XML verileri gibi özel öğelerde veri depoladıysanız, bu iş nesneleri serileştirme yoluyla devam ettirilebilir.

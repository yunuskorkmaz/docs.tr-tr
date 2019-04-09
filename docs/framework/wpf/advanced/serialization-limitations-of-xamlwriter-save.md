---
title: XamlWriter.Save'in Serileştirme Sınırlamaları
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 89cb36dba63dccdf7e52b7fcafbe3d9fc2fea1e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113288"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save'in Serileştirme Sınırlamaları
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A> İçeriğini serileştirmek için kullanılan bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama olarak bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya. Ancak, tam olarak ne serileştirildiği, bazı önemli sınırlamaları vardır. Bu sınırlamaların ve bazı genel konular, bu konuda belgelenmiştir.  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Çalışma zamanı, tasarım zamanı gösterimi  
 Bir çağrı tarafından sıralanmış olan temel felsefesi <xref:System.Windows.Markup.XamlWriter.Save%2A> sonucu, çalışma zamanında serileştirilmekte olan nesnenin gösterimini olacaktır. Özgün birçok tasarım zamanı özelliklerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya zaten en iyi duruma getirilmiş veya kaybedilmiş, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bellek içi nesneler olarak yüklenir ve çağırdığınızda korunmaz <xref:System.Windows.Markup.XamlWriter.Save%2A> serileştirmek için. Uygulamanın, ancak bu şart değildir özgün oluşturulmuş mantıksal ağacı etkili bir temsilini serileştirilmiş sonucudur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , üretilen. Bu sorunları kullanmayı son derece zor hale <xref:System.Windows.Markup.XamlWriter.Save%2A> kapsamlı bir parçası olarak seri hale getirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tasarım yüzeyi.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>Seri hale getirme müstakil  
 Seri hale getirilmiş çıktısını <xref:System.Windows.Markup.XamlWriter.Save%2A> ; bağımsızdır serileştirilmiş her şeyi içindedir bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tek bir kök öğe ve dışındaki dış başvuru ile tek sayfalı [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]. Sayfanız kaynakları uygulama kaynaklarından başvurulan, örneği için bu sayfanın serileştirilmekte olan bir bileşen oldukları gibi görünür.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Uzantı Başvurular geri alınır.  
 Ortak nesneler gibi çeşitli biçimlendirme uzantısı biçimleri tarafından yapılan başvurular `StaticResource` veya `Binding`, seri hale getirme işlemi tarafından alınacaktır. Bu, bellek içi nesneler uygulama çalışma zamanı tarafından oluşturulan zaman çoktan geri alınmıştır ve <xref:System.Windows.Markup.XamlWriter.Save%2A> mantıksal değil yeniden ziyaret özgün [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gibi seri hale getirilmiş çıktı başvuruları geri yüklemek için. Bu, büyük olasılıkla herhangi bir sınırlama veya kaynaktan elde edilen son ile yerel olarak ayarlanmış başka bir değerden bir değeri ayırmak için yalnızca sınırlı ya da dolaylı özelliği çalışma zamanı gösterimi tarafından kullanılan bir değer olmasını değeri donuyor. Görüntüleri de serileştirilme görüntüleri nesne başvuruları ne olursa olsun, dosya adı, özgün kaynak başvuruları olarak değil, projede var veya [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başlangıçta başvuruldu. Aynı sayfa içinde kaynaklar nerede bunlar, bir kaynak koleksiyonu anahtar olarak korunur yerine başvurulan noktasına serileştirilmiş görülür.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>Olay işleme korunmuş değildir  
 Zaman aracılığıyla eklenen olay işleyicileri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olan seri, bunlar korunmaz. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arka plan kod (Ayrıca olmadan ve ilgili x: Code mekanizması) yordam çalışma zamanı mantığını serileştirilirken bir yolu yoktur. Serileştirme bağımsızdır ve mantıksal ağaç sınırlı olduğundan, olay işleyicileri depolamak için hiçbir olanak yoktur. Sonuç olarak, olay işleyicisi öznitelikleri, öznitelik hem işleyici, adları dize değeri çıktısı kaldırılır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>XamlWriter.Save'in gerçekçi senaryolar  
 Listelenen sınırlamalar burada oldukça, yine de kullanmak için uygun çeşitli senaryolar vardır <xref:System.Windows.Markup.XamlWriter.Save%2A> seri hale getirme.  
  
-   Vektör veya grafik çıktısı: İşlenen alan çıktısı, aynı vektör veya yeniden, grafik yeniden oluşturmak için kullanılabilir.  
  
-   Zengin metin ve akış belgeleri: Metin ve içindeki tüm öğesi biçimlendirme ve öğeyi kapsama çıktısında korunur. Bu Pano işlevselliği yaklaşık mekanizmaları için yararlı olabilir.  
  
-   İş nesnesi veri koruma: Veri, özel öğeler gibi depoladığınız varsa [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri, iş nesnelerinizi temel izleyin sürede [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özel oluşturucular ve başvuruya göre özellik değerlerini dönüştürme sağlamak gibi kuralları, bu iş nesneleri olabilir Serileştirme yöntemiyle perpetuated.

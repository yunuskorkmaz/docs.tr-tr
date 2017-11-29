---
title: "XamlWriter.Save'in Serileştirme Sınırlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06033c6a753dd567f613f0b848e806dfa14ee77d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save'in Serileştirme Sınırlamaları
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A> İçeriğini serileştirmek için kullanılan bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olarak uygulama bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası. Ancak, ne tam olarak serileştirilmiş içinde bazı önemli sınırlamalar vardır. Bu sınırlamaların ve bazı genel konular bu konuda belgelenmiştir.  
  
 
  
<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Çalışma zamanı, tasarım zamanında gösterimi  
 Bir çağrı tarafından sıralanmış olan temel felsefesi <xref:System.Windows.Markup.XamlWriter.Save%2A> sonucu, çalışma zamanında serileştirilen nesnenin gösterimi bulabilirsiniz. Birçok tasarım zamanı özellikleri özgün [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası zaten en iyi duruma getirilmiş olabilir veya kaybedilmiş, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bellek içi nesneler olarak yüklenir ve çağırdığınızda korunmaz <xref:System.Windows.Markup.XamlWriter.Save%2A> seri hale getirilemedi. Uygulamanın, ancak özgün yapılandırılmış mantıksal ağacının etkili bir gösterimidir serileştirilmiş sonucudur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] onu üreten. Bu sorunları kullanmak oldukça zor hale <xref:System.Windows.Markup.XamlWriter.Save%2A> kapsamlı bir parçası olarak serileştirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tasarım yüzeyi.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>Serileştirme kendi içinde bulunan  
 Seri hale getirilmiş çıktısı <xref:System.Windows.Markup.XamlWriter.Save%2A> kendi içinde yer alan; serileştirilen herşey içindedir bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tek bir kök öğe ve dış başvuru dışında ile tek sayfa [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]. Sayfanız uygulama kaynaklarından kaynakları başvurulan, örneği için bu serileştirilen sayfanın bileşeninin oldukları gibi görünür.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Uzantı Başvurular geri alınır.  
 Nesnelere gibi çeşitli biçimlendirme uzantısı biçimleri tarafından yapılan ortak başvurular `StaticResource` veya `Binding`, serileştirme işlemi tarafından alınacaktır. Bunlar, bellek içi nesneler uygulama çalışma zamanı tarafından oluşturulduğu zaman çoktan geri alınmıştır ve <xref:System.Windows.Markup.XamlWriter.Save%2A> mantığı değil yeniden ziyaret özgün [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bu başvuruları serileştirilen çıktıya geri yüklemek için. Bu büyük olasılıkla herhangi bir veriye bağlı veya böyle bir değer yerel olarak ayarlanmış başka bir değerden ayırt etmek için yalnızca sınırlı ya da dolaylı yeteneği olan son çalışma zamanı gösterimi tarafından kullanılan değer olacak şekilde değeri elde kaynak donuyor. Görüntüleri de serileştirilir görüntüleri nesne başvuruları ne olursa olsun, dosya adı, özgün kaynak başvuruları olarak değil, projeye var veya [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ilk olarak başvuruldu. Aynı sayfa içinde bildirilen bile kaynaklar burada bunlar, bir kaynak koleksiyonu anahtar olarak korunur yerine başvurulan noktasına serileştirilmiş görülür.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>Olay işleme korunmuş değildir  
 Zaman üzerinden eklenen olay işleyicileri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olan seri, bunlar korunmaz. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]arka plan kodu olmadan (ve ayrıca ilgili x: Code mekanizması olmadan) çalışma zamanı yordamsal mantığını seri hale getirilirken bir yolu yoktur. Seri hale getirme bağımsızdır ve mantıksal ağacının sınırlı olduğu için olay işleyicileri depolamak için hiçbir olanak yoktur. Sonuç olarak, olay işleyicisi öznitelikleri, özniteliğin kendisi ve işleyiciye ad dize değeri çıktısından kaldırılır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>XamlWriter.Save kullanımı için gerçekçi senaryolar  
 Listelenen sınırlamalar İşte oldukça, hala kullanmaya yönelik çeşitli uygun senaryolar vardır <xref:System.Windows.Markup.XamlWriter.Save%2A> seri hale getirme.  
  
-   Vektör veya grafik çıktısı: işlenen bölgenin çıktısı aynı vektör veya yeniden zaman grafikleri yeniden oluşturmak için kullanılabilir.  
  
-   Zengin metin ve akış belgeleri: metin ve içindeki tüm öğesi biçimlendirme ve öğesi kapsama çıktıda korunur. Bu Pano işlevselliğini yaklaşık mekanizmalar için yararlı olabilir.  
  
-   İş nesnesi veri koruma:, veri özel öğeler, gibi depoladığınız varsa [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri, iş nesnelerinizi temel izleyin kadar uzun süre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özel oluşturucular ve dönüştürme başvuru tarafından özellik değerleri için sağlama gibi kuralları Bu iş nesneleri serileştirme üzerinden etmesindeki.

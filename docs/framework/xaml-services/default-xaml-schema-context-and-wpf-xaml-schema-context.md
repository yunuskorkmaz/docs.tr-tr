---
title: Varsayılan XAML Şema İçeriği ve WPF XAML Şema İçeriği
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 0d6a0aa80d8490c509fa9036f88d4f6863ff040c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295607"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Varsayılan XAML Şema İçeriği ve WPF XAML Şema İçeriği
XAML şema içeriği belirli bir XAML sözlük kullanan XAML üretim yazma davranışını nasıl tür eşlemesi çözümler, derlemelerin nasıl yüklü olduğundan, nasıl belirli okuyucu ve yazıcı dahil olmak üzere, nesne ile nasıl etkileştiğini niteleyen kavramsal bir varlıktır ayarları yorumlanır. Bu konuda, .NET Framework XAML hizmetlerinde CLR tür sistemine dayalı varsayılan XAML şema içeriği ve özellikler açıklanmaktadır. Bu konuda kullanılan WPF XAML şema içeriği anlatılır.  
  
## <a name="default-xaml-schema-context"></a>Varsayılan XAML şema içeriği  
 .NET framework XAML hizmetlerinde hem uygular ve varsayılan XAML şema içeriği kullanır. Varsayılan XAML şema içeriği davranışı her zaman tam olarak API'SİNDE görünür değil <xref:System.Xaml.XamlSchemaContext> sınıfı. Ancak, çoğu durumda varsayılan XAML şema içeriği etkileyen üyeleri gibi XAML tür sistemi, ortak API aracılığıyla gözlemlenebilir bir davranıştır <xref:System.Xaml.XamlMember> veya <xref:System.Xaml.XamlType>, ya da XAML okuyucular ve kullanmakta olduğunuz XAML yazıcılar üzerinde kullanıma sunulan API'ler aracılığıyla Varsayılan XAML şema içeriği.  
  
 Oluşturabileceğiniz bir <xref:System.Xaml.XamlSchemaContext> çağırarak, varsayılan davranışı kapsülleyen <xref:System.Xaml.XamlSchemaContext> Oluşturucusu. Bunu açıkça varsayılan XAML şema içeriği oluşturur. XAML okuyucu veya açıkça almaz API'lerini kullanarak XAML yazıcı başlatmak, aynı varsayılan XAML şema içeriği örtülü olarak oluşturulan bir <xref:System.Xaml.XamlSchemaContext> giriş parametresi.  
  
 Varsayılan XAML şema içeriği türü eşleme davranışını için CLR yansıma kullanır. Bu tanımlama CLR inceleme içerir <xref:System.Type>ve ilgili <xref:System.Reflection.PropertyInfo> veya <xref:System.Reflection.MethodInfo>. Ayrıca, türler ve üyelerle ilgili CLR attribution XAML türü veya tür yedekleme CLR kullanan XAML üye bilgilerini teklifleri hakkındaki ayrıntıları doldurun için kullanılır. Varsayılan XAML şema içeriği türü sistem uzantısı teknikleri gibi gerektirmez `Invoker` CLR türü sistemden gerekli bilgileri kullanılabildiği için desen.  
  
 Varsayılan XAML şema içeriği mantıksal yüklenirken derleme için çoğunlukla XAML ad alanı eşleştirmelerinde sağlanan derleme değerleri kullanır. Ayrıca, <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> bir derlemenin iç türlerine yükleme gibi senaryolar için yükleme ipucu.  
  
## <a name="wpf-xaml-schema-context"></a>WPF XAML şema içeriği  
 WPF uygulaması olmayan varsayılan XAML şema içeriği uygulayarak sunulan özelliklerin türleri ilgi çekici bir resmi sağladığından, WPF XAML şema içeriği bu konuda açıklanmıştır. Ayrıca, XAML şema içeriği kavramı çok WPF XAML ele WPF belgelerinde ele alınmayan; XAML şema içeriği etkinleştiren davranışı, yalnızca varsayılan XAML şema içeriği nasıl çalıştığı ile ilgili bir tartışma bütünleştirdiyseniz tam olarak anlaşılır olabilir. WPF XAML şema içeriği şu davranışı uygular.  
  
 **Arama geçersiz kılar:** WPF XAML için birkaç içerik modeli vardır olmaksızın işlevini XAML İçerik özellikleri olduğu <xref:System.Windows.Markup.ContentPropertyAttribute> öznitelikli. <xref:System.Xaml.XamlType.LookupContentProperty%2A> WPF için bu davranışı geçersiz kılmalarını.  
  
 **Erteleme WPF ifadeler için:** WPF bir çalışma zamanı bağlamı kullanılabilir oluncaya kadar değeri erteleme birkaç ifade sınıflar bulunur. Ayrıca, şablon genişletmesi erteleme teknikleri üzerinde dayanan bir çalışma zamanı davranışı vardır.  
  
 **Sistem arama iyileştirmeleri yazın:** WPF devral yüzlerce WPF tanımlı sınıflar için temel sınıf üye tanımları dahil olmak üzere bir kapsamlı XAML sözlük ve nesne modeli vardır. Ayrıca, WPF kendisini çeşitli derlemeler geneline yayılır. WPF arama tabloları ve diğer teknikleri kullanarak kendi tür araması iyileştirir. Varsayılan XAML şema içeriği ve onun türü CLR tabanlı arama üzerinde performans geliştirmeleri sunar. Burada türleri bir arama tablosunda bulunmayan durumlarda davranış varsayılan XAML şema içeriği için benzer XAML şema içeriği teknikleri kullanır.  
  
 **XamlType ve XamlMember uzantısı:** Bağımlılık özellikleri ile özellik kavramları ve yönlendirilmiş olaylar ile olay kavramları WPF genişletir. Bu kavramlar XAML işlemleri için daha fazla görünürlük vermek için WPF genişletir <xref:System.Xaml.XamlType> ve <xref:System.Xaml.XamlMember>ve rapor bağımlılık özelliği ve olay özelliklerini yönlendirilen iç özellikleri ekler.  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>WPF XAML şema içeriği erişme  
 WPF, temel XAML teknikleri kullanıyorsanız <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> veya <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>, WPF XAML şema içeriği bu XAML okuyucu ve yazıcı uygulamaları XAML kullanılıyor.  
  
 WPF XAML şema içeriği ile diğer XAML okuyucu veya başlatamadı. XAML yazıcı uygulamaları kullanıyorsanız, çalışan bir WPF XAML şema içeriği'nden almak mümkün olabilir <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>. Bu değer daha sonra kullanan diğer API'si için başlatma olarak kullanabilirsiniz bir <xref:System.Xaml.XamlSchemaContext>. Örneğin, çağırabilir <xref:System.Xaml.XamlXmlReader.%23ctor%2A> başlatma ve WPF XAML şema içeriği geçişi için. Ya da WPF XAML şema içeriği XAML türü sistem işlemleri için kullanabilirsiniz. Bu yapı başlatılması içerebilir bir <xref:System.Xaml.XamlType> veya <xref:System.Xaml.XamlMember>, veya çağırma <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.  
  
 WPF XAML bazı yönlerini saf bir XAML düğüm akış perspektiften erişirseniz, WPF framework özelliklerden bazıları henüz etkilediği değil olduğunu unutmayın. Örneğin, Denetim WPF şablonları henüz uygulanmaz. Böylece, çalışma zamanında bir tam görsel ağacını ile doldurulmuş bir özellik erişirseniz, yalnızca bir şablon başvuran bir özellik değeri görebilirsiniz. WPF biçimlendirme uzantıları için sağlanan hizmet bağlamı da bir çalışma zamanı olmayan durumdan sağlanırsa, doğru olmayabilir ve özel durumlar, bir nesne grafiğinin yazmaya çalışırken neden olabilir.  
  
## <a name="xaml-and-assembly-loading"></a>XAML ve derleme yükleme  
 Derleme yükleme için XAML ve .NET Framework XAML hizmetlerinde CLR tanımlı kavramı ile tümleştirilir <xref:System.AppDomain>. XAML şema içeriği nasıl derlemeler yüklemek ya da kullanıma bağlı çalıştırma veya tasarım zamanı türlerini bulun yorumlar <xref:System.AppDomain> ve diğer etkenlere bağlı. Mantıksal XAML gevşek XAML için XAML okuyucu olmasına bağlı olarak biraz daha farklıdır, DLL tarafından içine derlenmiş XAML olduğu `XamlBuildTask`, veya BAML WPF'nin tarafından oluşturulan `PresentationBuildTask`.  
  
 WPF için XAML şema içeriği sırayla kullanan WPF uygulaması modelle tümleştirir <xref:System.AppDomain> WPF Uygulama Ayrıntıları diğer etkenler yanı sıra.  
  
#### <a name="xaml-reader-input-loose-xaml"></a>XAML okuyucu giriş (gevşek XAML)  
  
1. XAML şema içeriği gezinir <xref:System.AppDomain> tüm yönlerini adı ile eşleşen bir zaten yüklü derleme için arama uygulamasının en son başlatma derleme yüklendi. Bir eşleşme bulunursa, o derleme çözümlemesi için kullanılır.  
  
2. CLR aşağıdaki tekniklerden birini temel Aksi takdirde, <xref:System.Reflection.Assembly> API, bir derlemeyi yüklemek için kullanılır:  
  
    -   Eşlemede tam adı, çağrı <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> tam adı.  
  
    -   Önceki adım başarısız olursa, kısa ad (ve ortak anahtar belirteci varsa) kullanan çağrılacak <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
    -   Adı eşlemede nitelenmemiş ise, çağrı <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask` Windows Communication Foundation (WCF) ve Windows Workflow Foundation için kullanılır.  
  
 Aracılığıyla derlemenin başvurduğu Not `XamlBuildTask` her zaman tam yetkilidir.  
  
1. Çağrı <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> tam adı.  
  
2. Önceki adım başarısız olursa, kısa ad (ve ortak anahtar belirteci varsa) kullanan çağrılacak <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 Derleme yükleme BAML için iki önemli nokta vardır: bir bileşen olarak BAML içeren ilk bütünleştirilmiş kod yükleme ve BAML üretim tarafından başvurulan tüm türler için tür yedekleme derlemeleri yükleniyor.  
  
##### <a name="assembly-load-for-initial-markup"></a>Bütünleştirilmiş kod yüklemesi ilk biçimlendirme için:  
 Biçimlendirmeden yüklenecek derlemenin her zaman nitelenmemiş başvurudur.  
  
1. WPF XAML şema içeriği gezinir <xref:System.AppDomain> tüm yönlerini adı ile eşleşen bir zaten yüklü derleme için arama WPF uygulamasının en son başlatma derleme yüklendi. Bir eşleşme bulunursa, o derleme çözümlemesi için kullanılır.  
  
2. Önceki adım başarısız olursa, kısa ad (ve ortak anahtar belirteci varsa) kullanan çağrılacak <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
##### <a name="assembly-references-by-baml-types"></a>Derleme başvuruları BAML türlerine göre:  
 Derleme başvuruları BAML üretimde kullanılan türleri için her zaman yapı görevinin çıkış olarak tam olarak nitelenmiş.  
  
1. WPF XAML şema içeriği gezinir <xref:System.AppDomain> tüm yönlerini adı ile eşleşen bir zaten yüklü derleme için arama WPF uygulamasının en son başlatma derleme yüklendi. Bir eşleşme bulunursa, o derleme çözümlemesi için kullanılır.  
  
2. Aksi takdirde aşağıdaki tekniklerden birini bir derlemeyi yüklemek için kullanılır:  
  
    -   Çağrı <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> tam adı.  
  
    -   Kısa ad + BAML öğesinden yüklenmiş derlemeyle eşleşebilmesi ortak anahtar belirteci bileşimi, bu derleme kullanın.  
  
    -   Çağırmak için kısa ad + ortak anahtar belirteci kullanmanız <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama](understanding-xaml-node-stream-structures-and-concepts.md)

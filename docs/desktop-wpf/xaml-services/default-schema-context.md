---
title: Varsayılan XAML Şema İçeriği ve WPF XAML Şema İçeriği
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 2e92372de61230a98a02282cc28fc3f479cd94eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071866"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Varsayılan XAML Şema İçeriği ve WPF XAML Şema İçeriği
XAML şeması bağlamı, belirli bir XAML sözcük dağarcığı kullanan bir XAML üretiminin, tür eşlemenin nasıl çözümlendiği, derlemelerin nasıl yüklendiği, belirli okuyucu ve yazar ayarlarının nasıl yorumlanacağı gibi nesne yazma davranışıyla nasıl etkileşime girdiğine dair kavramsal bir varlıktır. Bu konu, .NET XAML Hizmetlerinin özelliklerini ve CLR türü sistemini temel alan ilişkili varsayılan XAML şeması bağlamını açıklar. Bu konu, WPF için kullanılan XAML şema bağlamını da açıklar.

## <a name="default-xaml-schema-context"></a>Varsayılan XAML Şema Bağlamı

.NET XAML Hizmetleri varsayılan XAML şeması bağlamı uygular ve kullanır. Varsayılan XAML şema bağlam ı davranışı <xref:System.Xaml.XamlSchemaContext> her zaman sınıfın API'sinde tam olarak görünmez. Ancak, çoğu durumda varsayılan XAML şema bağlamının etkilediği davranış, xaml schema bağlamını kullanan XAML okuyucuları <xref:System.Xaml.XamlMember> ve XAML yazarlarında maruz kalan XAML okuyucuları veya <xref:System.Xaml.XamlType>API'leri gibi XAML türü sistemin ortak API'sı aracılığıyla gözlemlenebilir.

Oluşturucuyu <xref:System.Xaml.XamlSchemaContext> çağırarak varsayılan davranışı kapsülleyen bir oluşturabilirsiniz. <xref:System.Xaml.XamlSchemaContext> Bu açıkça varsayılan XAML şema bağlamını oluşturur. Api'leri kullanarak bir XAML okuyucusunun veya XAML yazarının açık bir <xref:System.Xaml.XamlSchemaContext> giriş parametresi alamayan bir XAML okuyucusunun veya XAML yazarının başlatılmasıdurumunda, aynı varsayılan XAML şeması bağlamı örtülü olarak oluşturulur.

Varsayılan XAML şeması bağlamı, tür eşleme davranışı için CLR yansımasına dayanır. Bu tanımlayıcı CLR <xref:System.Type>incelenmesi içerir ve <xref:System.Reflection.PropertyInfo> <xref:System.Reflection.MethodInfo>ilgili veya . Ayrıca, ClR destek türünü kullanan XAML türü veya XAML üye bilgilerinin özelliklerini doldurmak için, türleri veya üyelere ilişkin CLR atıfları kullanılır. ClR yazı sisteminden gerekli bilgiler mevcut olduğundan, varsayılan `Invoker` XAML şema bağlamı desen gibi tür sistem uzantısı tekniklerini gerektirmez.

Derleme yükleme mantığı için varsayılan XAML şeması bağlamı esas olarak XAML ad alanı eşlemelerinde sağlanan montaj değerlerine dayanır. Ayrıca, <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> iç türleri yükleme gibi senaryolar için bir derlemenin yüklenmesini ipucu verebilir.

## <a name="wpf-xaml-schema-context"></a>WPF XAML Şema Bağlamı

WPF uygulaması varsayılan olmayan bir XAML şeması bağlamı uygulanarak tanıtılabilir özelliklerin türlerinin ilginç bir örnek sağlar, çünkü WPF XAML şeması bağlamında bu konuda açıklanmıştır. Ayrıca, XAML şema bağlamı kavramı WPF XAML adresleri WPF belgelerde çok fazla tartışılır değil; XAML şema bağlamının etkinleştirdığı davranış, yalnızca varsayılan XAML şema bağlamının nasıl çalıştığına dair bir tartışmayla entegre edilirse tam olarak anlaşılabilir olabilir. WPF XAML şeması aşağıdaki davranışı uygular.

**Arama geçersiz kılar:** WPF'nin XAML için birkaç içerik modeli vardır ve burada <xref:System.Windows.Markup.ContentPropertyAttribute> xaml içerik özellikleri atfedilmeden çalışır. <xref:System.Xaml.XamlType.LookupContentProperty%2A>WPF için geçersiz kılar bu davranışı uygulayın.

**WPF ifadeleri için erteleme:** WPF, çalışma zamanı bağlamı kullanılabilir olana kadar bir değeri erteleyen birkaç ifade sınıfı sunar. Ayrıca, şablon genişletme erteleme tekniklerine dayanan bir çalışma zamanı davranışıdır.

**Sistem arama optimizasyonlarını yazın:** WPF, kelimenin tam anlamıyla yüzlerce WPF tanımlı sınıfa miras kalan taban sınıf üye tanımları da dahil olmak üzere kapsamlı bir XAML kelime dağarcığı ve nesne modeline sahiptir. Ayrıca, WPF kendisi çeşitli derlemeler arasında yayılır. WPF, arama tablolarını ve diğer teknikleri kullanarak türünü en iyi duruma getirmektedir. Bu, varsayılan XAML şema bağlamı ve CLR tabanlı türü araması üzerinde performans iyileştirmeleri sağlar. Türlerin bir arama tablosunda bulunmadığı durumlarda, davranış varsayılan XAML şema bağlamına benzer XAML şema bağlamı tekniklerini kullanır.

**XamlType ve XamlMember uzantısı:** WPF, bağımlılık özelliklerine sahip özellik kavramlarını ve yönlendirilmiş olayları içeren olay kavramlarını genişletir. Bu kavramlara XAML işleme işlemleri için daha fazla <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlMember>görünürlük sağlamak için WPF, bağımlılık özelliğini ve yönlendirilmiş olay özelliklerini bildiren dahili özellikleri genişletir ve ekler.

### <a name="accessing-the-wpf-xaml-schema-context"></a>WPF XAML Şema Bağlamına Erişim

WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> veya <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>dayalı XAML teknikleri kullanıyorsanız, WPF XAML şema bağlamı zaten bu XAML okuyucu ve XAML yazar uygulamalarında kullanılmaktadır.

WPF XAML şeması bağlamı yla başlanamayan diğer XAML okuyucu veya XAML yazar uygulamalarını kullanıyorsanız, çalışan bir WPF XAML <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>şeması bağlamından. Daha sonra bu değeri, bir <xref:System.Xaml.XamlSchemaContext>. Örneğin, başlatma çağrısında <xref:System.Xaml.XamlXmlReader.%23ctor%2A> ve WPF XAML şema bağlamında geçmek. Veya XAML türü sistem işlemleri için WPF XAML şeması bağlamını kullanabilirsiniz. Bu, bir <xref:System.Xaml.XamlType> veya <xref:System.Xaml.XamlMember>' in inşaat <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>başlatmaveya arama' yı içerebilir.

WPF XAML'nin belirli yönlerine saf XAML düğüm akışı perspektiflerinden erişirseniz, bazı WPF çerçeve özelliklerinin henüz harekete gememiş olabileceğini unutmayın. Örneğin, denetimler için WPF şablonları henüz uygulanmamıştır. Bu nedenle, çalışma zamanında tam bir görsel ağaçla doldurulabilecek bir özelliğe erişiyorsanız, yalnızca şablona başvuran bir özellik değeri görebilirsiniz. WPF biçimlendirme uzantıları için sağlanan hizmet bağlamı, çalışma zamanı olmayan bir durumdan sağlandığında da doğru olmayabilir ve nesne grafiği yazmaya çalışırken özel durumlara neden olabilir.

## <a name="xaml-and-assembly-loading"></a>XAML ve Montaj Yükleme

XAML ve .NET XAML Hizmetleri için montaj yüklemesi <xref:System.AppDomain>CLR tanımlı . XAML şeması bağlamı, derlemelerin nasıl yüklenir veya çalışma zamanında veya tasarım zamanında türleri <xref:System.AppDomain> nasıl bulabileceğinizi, kullanımı ve diğer etkenlere bağlı olarak yorumlar. Mantık XAML gevşek XAML bir XAML okuyucu için olup olmadığına bağlı olarak biraz farklıdır, XAML tarafından `XamlBuildTask`bir DLL içine `PresentationBuildTask`derlenmiş, ya da BAML WPF tarafından oluşturulan .

WPF için XAML şeması bağlamı, WPF uygulama modeliyle bütünleşir ve bu uygulama nın yanı sıra WPF uygulama ayrıntıları olan diğer etkenleri de kullanır. <xref:System.AppDomain>

#### <a name="xaml-reader-input-loose-xaml"></a>XAML okuyucu girişi (gevşek XAML)

01. XAML şeması bağlamı, en son <xref:System.AppDomain> yüklenen derlemeden başlayarak, adın tüm yönleriyle eşleşen zaten yüklenmiş bir derleme yi arayarak uygulamanın üzerinden yinelenir. Bir eşleşme bulunursa, bu derleme çözüm için kullanılır.

02. Aksi takdirde, clr <xref:System.Reflection.Assembly> API'yi temel alan aşağıdaki tekniklerden biri bir derlemeyi yüklemek için kullanılır:

    - Haritalamada ad nitelikliyse, <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> nitelikli adı arayın.

    - Önceki adım başarısız olursa, çağırmak <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>için kısa adı (ve varsa ortak anahtar belirteci) kullanın.

    - Eşlemede ad niteliksizse, <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>'yi arayın.

#### <a name="xamlbuildtask"></a>XamlBuildTask

`XamlBuildTask`Windows Communication Foundation (WCF) ve Windows İş Akışı Vakfı için kullanılır.

Montaj başvurularının `XamlBuildTask` her zaman tam olarak nitelikli olduğunu unutmayın.

1. Kalifiye <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> ismi arayın.

2. Önceki adım başarısız olursa, çağırmak <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>için kısa adı (ve varsa ortak anahtar belirteci) kullanın.

#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)

BAML için montaj yüklemenin iki yönü vardır: BAML'yi bileşen olarak içeren ilk derlemenin yüklenmesi ve BAML üretiminin başvurulan türleri için tür destek derlemelerinin yüklenmesi.

##### <a name="assembly-load-for-initial-markup"></a>İlk biçimlendirme için montaj yükü:

Biçimlendirmeyi yüklemek için montaja yapılan başvuru her zaman niteliksizdir.

1. WPF XAML şeması bağlamı, en <xref:System.AppDomain> son yüklenen derlemeden başlayarak, adın tüm yönleriyle eşleşen zaten yüklenmiş bir derleme yi arayarak WPF uygulaması aracılığıyla yinelenir. Bir eşleşme bulunursa, bu derleme çözüm için kullanılır.

2. Önceki adım başarısız olursa, çağırmak <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>için kısa adı (ve varsa ortak anahtar belirteci) kullanın.

##### <a name="assembly-references-by-baml-types"></a>BAML türlerine göre montaj başvuruları:

BAML üretiminde kullanılan türler için montaj başvuruları, yapı görevinin çıktısı olarak her zaman tam olarak niteliklidir.

01. WPF XAML şeması bağlamı, en <xref:System.AppDomain> son yüklenen derlemeden başlayarak, adın tüm yönleriyle eşleşen zaten yüklenmiş bir derleme yi arayarak WPF uygulaması aracılığıyla yinelenir. Bir eşleşme bulunursa, bu derleme çözüm için kullanılır.

02. Aksi takdirde, bir derleme yüklemek için aşağıdaki tekniklerden biri kullanılır:

    - Kalifiye <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> ismi arayın.
  
    - Kısa bir ad + ortak anahtar belirteç birleşimi BAML'nin yüklendiği derlemeyle eşleşirse, bu derlemeyi kullanın.

    - Aramak <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>için kısa ad + ortak anahtar belirteci kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama](understanding-xaml-node-stream-structures-and-concepts.md)

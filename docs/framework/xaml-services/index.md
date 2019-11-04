---
title: XAML Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: a99b9f3cb8c008f72eaac7ee1b8790d63c547a8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453962"
---
# <a name="xaml-services"></a>XAML Hizmetleri
Bu konu, .NET Framework XAML Hizmetleri olarak bilinen bir teknoloji kümesinin yeteneklerini açıklamaktadır. Açıklanan hizmetlerin ve API 'lerin çoğunluğu, .NET Core Derlemeleriyle .NET Framework 4 ' te tanıtılan bir derleme olan System. xaml derlemesinde bulunur. Hizmetler okuyucuları ve yazarları, şema sınıflarını ve şema desteğini, fabrikaları, Attributing of sınıfları, XAML dil iç desteğini ve diğer XAML dil özelliklerini içerir.  
  
## <a name="about-this-documentation"></a>Bu belge hakkında  
 .NET Framework XAML Hizmetleri için kavramsal belgeler, XAML dili ile önceki deneyiminizin olduğunu ve bu özelliğin belirli bir çerçeveye nasıl uygulanacağını (örneğin, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] veya Windows Workflow Foundation ya da belirli bir teknoloji özellik alanı) kabul eder. Örneğin <xref:Microsoft.Build.Framework.XamlTypes>yapı özelleştirme özellikleri. Bu belge, XAML temel bilgilerini biçimlendirme dili, XAML sözdizimi terimleri veya diğer tanıtım malzemeleri olarak açıklamaya çalışır. Bunun yerine, bu belgeler özel olarak System. xaml derleme kitaplığı 'nda etkinleştirilen .NET Framework XAML hizmetlerini kullanarak odaklanır. Bu API 'lerin çoğu XAML dil tümleştirmesi ve genişletilebilirlik senaryoları içindir. Bu, aşağıdakilerden herhangi birini içerebilir:  
  
- Temel XAML okuyucuları veya XAML yazıcılarının yeteneklerini genişletme (XAML düğüm akışını doğrudan işleme; kendi XAML okuyucunuzu veya XAML yazıcınızı türeten türetme).  
  
- Belirli çerçeve bağımlılıkları olmayan XAML özellikli özel türleri tanımlama ve xaml tür sistem özelliklerini .NET Framework XAML hizmetlerine iletmek için türler Attributing.  
  
- Xaml okuyucuları veya XAML yazıcılarını, XAML biçimlendirme kaynakları için görsel tasarımcı veya etkileşimli düzenleyici gibi bir uygulamanın bileşeni olarak barındırma.  
  
- XAML değer dönüştürücüleri yazma (biçimlendirme uzantıları; özel türler için tür dönüştürücüler).  
  
- Özel bir XAML şeması bağlamı tanımlama (tür kaynaklarını yedeklemek için alternatif derleme yükleme teknikleri kullanarak) her zaman derlemeleri yansıtma yerine bilinen türler arama tekniklerini kullanarak, CLR `AppDomain` ve onun ilişkili güvenlik modeli).  
  
- Temel XAML tür sistemini genişletme.  
  
- XAML tür sistemini ve tür geri ayarlarını etkilemek için `Lookup` veya `Invoker` tekniklerini kullanma.  
  
 XAML 'de bir dil olarak tanıtım malzemesini arıyorsanız [xaml 'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)deneyebilirsiniz. Bu konu, hem [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] hem de XAML biçimlendirme ve XAML dil özelliklerini kullanmak için yeni olan bir hedef kitle için XAML 'yi açıklamaktadır. Başka bir faydalı belge, [xaml dili belirtiminde](https://go.microsoft.com/fwlink/?LinkId=114525)tanıtım malzemeleridir.  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET mimarisinde XAML Hizmetleri ve System. xaml .NET Framework  
 Microsoft .NET Framework 'ün önceki sürümlerinde XAML dil özellikleri desteği, Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation ve Windows Communication Foundation (WCF)) üzerinde oluşturulmuş çerçeveler tarafından uygulanmıştır ve bu nedenle davranışında ve kullandığınız belirli çerçeveye bağlı olarak kullanılan API. Bu, XAML ayrıştırıcısının ve nesne grafiği oluşturma mekanizmasına, XAML dil iç bilgileri, serileştirme desteğiyle vb. dahil edilmiştir.  
  
 .NET Framework 4 ' te .NET Framework XAML Hizmetleri ve System. Xaml derlemesi XAML dil özelliklerini desteklemek için gerekli olan kadarını tanımlar. Bu, XAML okuyucuları ve XAML yazarları için temel sınıflar içerir. Çerçeveye özgü XAML uygulamalarında mevcut olmayan .NET Framework XAML hizmetlerine eklenen en önemli özellik, XAML için bir tür sistemi gösterimidir. Tür sistemi temsili, XAML 'nin belirli özellikleri üzerinde bağımlılıklar almadan XAML özelliklerini ortalar.  
  
 XAML tür sistemi, XAML başlangıcının biçimlendirme formu veya çalışma zamanı özellikleri ile sınırlı değildir; Ayrıca, belirli bir yedekleme türü sistemiyle sınırlıdır. XAML tür sistemi türler, Üyeler, XAML şema bağlamları, XML düzeyi kavramlar ve diğer XAML dil kavramları ya da XAML iç bilgileri için nesne temsillerini içerir. XAML türü sisteminin kullanılması veya genişletilmesi, XAML okuyucuları ve XAML yazarları gibi sınıflardan türemek ve XAML temsillerini bir çerçeve, teknoloji veya tüketen bir uygulama tarafından etkinleştirilen belirli özelliklere genişletmek mümkün hale getirir. XAML yayar. XAML şeması bağlamı kavramı, bir XAML nesne yazıcı uygulamasının birleşiminden, bir teknolojinin, bağlam içindeki derleme bilgileri ile iletişim kurmakta olan bir teknolojinin yedekleme türü sisteminin ve XAML düğümündeki pratik nesne grafiğinin yazma işlemlerine izin verebilir kaynaktaki. XAML şeması kavramı hakkında daha fazla bilgi için. bkz. [varsayılan xaml şeması bağlamı ve WPF XAML şema bağlamı](default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML düğüm akışları, XAML okuyucuları ve XAML yazarları  
 Xaml Hizmetleri .NET Framework xaml dili ve bir dil olarak XAML kullanan belirli teknolojiler arasındaki ilişkide oynadığı rolü anlamak için, bir XAML düğüm akışı kavramı ve bu kavramın API 'YI nasıl şekillendirildiğinden emin olmak yararlıdır. terminolojiyi. Xaml düğüm akışı, xaml dil temsili ve XAML tarafından temsil edilen veya tanımladığı nesne grafı arasındaki kavramsal bir ara bir ara değer.  
  
- XAML okuyucu, bazı biçimdeki XAML 'yi işleyen ve XAML düğüm akışı üreten bir varlıktır. API 'de, XAML okuyucu <xref:System.Xaml.XamlReader>temel sınıf tarafından temsil edilir.  
  
- XAML yazıcı, XAML düğüm akışını işleyen ve başka bir şey üreten bir varlıktır. API 'de, XAML yazıcı <xref:System.Xaml.XamlWriter>temel sınıf tarafından temsil edilir.  
  
 XAML ile ilgili en yaygın iki senaryo, nesne grafiğinin örneğini oluşturmak ve bir uygulama ya da araçtan bir nesne grafiğini kaydetmek ve bir XAML temsili (genellikle biçimlendirme formu metin dosyası olarak kaydedilir) üretmek için XAML 'yi yüklüyor. XAML yüklemek ve bir nesne grafiğinin oluşturulması, genellikle bu belgelerde yükleme yolu olarak adlandırılır. Varolan bir nesne grafiğinin XAML 'ye kaydedilmesi veya serileştirilmesi, genellikle bu belgelerde kaydetme yolu olarak adlandırılır.  
  
 En yaygın yükleme yolu türü aşağıdaki gibi açıklanabilir:  
  
- UTF kodlu XML biçiminde bir XAML temsili ile başlayın ve metin dosyası olarak kaydedilir.  
  
- Bu XAML <xref:System.Xaml.XamlXmlReader>' ye yükleyin. <xref:System.Xaml.XamlXmlReader> bir <xref:System.Xaml.XamlReader> alt sınıfıdır.  
  
- Sonuç bir XAML düğüm akışıdır. <xref:System.Xaml.XamlXmlReader> / <xref:System.Xaml.XamlReader> API 'sini kullanarak XAML düğüm akışının bağımsız düğümlerine erişebilirsiniz. Burada en sık kullanılan işlem, XAML düğüm akışı aracılığıyla ilerleyecek ve "geçerli kayıt" metaphor kullanılarak her bir düğümün işlenmesine yönelik olur.  
  
- Elde edilen düğümleri XAML düğüm akışından <xref:System.Xaml.XamlObjectWriter> API 'sine geçirin. <xref:System.Xaml.XamlObjectWriter> bir <xref:System.Xaml.XamlWriter> alt sınıfıdır.  
  
- <xref:System.Xaml.XamlObjectWriter>, kaynak XAML düğüm akışı aracılığıyla ilerlemeye uygun olarak bir nesne grafiğini, tek seferde bir nesne olarak yazar. Bu, bir XAML şema bağlamı ve bir yedekleme türü sisteminin ve çerçevesinin derlemelerine ve türlerine erişebilen bir uygulama ile yapılır.  
  
- Nesne grafiğinin kök nesnesini elde etmek için XAML düğüm akışının sonundaki <xref:System.Xaml.XamlObjectWriter.Result%2A> çağırın.  
  
 En yaygın kaydetme yolu türü aşağıdaki gibi açıklanabilir:  
  
- Tüm uygulama çalışma zamanı, Kullanıcı arabirimi içeriği ve çalışma zamanının durumu ya da çalışma zamanında genel uygulamanın nesne gösteriminin daha küçük bir kesimini başlatın.  
  
- Uygulama kökü veya belge kökü gibi mantıksal bir başlangıç nesnesinden nesneleri <xref:System.Xaml.XamlObjectReader>' ye yükleyin. <xref:System.Xaml.XamlObjectReader> bir <xref:System.Xaml.XamlReader> alt sınıfıdır.  
  
- Sonuç bir XAML düğüm akışıdır. <xref:System.Xaml.XamlObjectReader> ve <xref:System.Xaml.XamlReader> API kullanarak XAML düğüm akışının bağımsız düğümlerine erişebilirsiniz. Burada en sık kullanılan işlem, XAML düğüm akışı aracılığıyla ilerleyecek ve "geçerli kayıt" metaphor kullanılarak her bir düğümün işlenmesine yönelik olur.  
  
- Elde edilen düğümleri XAML düğüm akışından <xref:System.Xaml.XamlXmlWriter> API 'sine geçirin. <xref:System.Xaml.XamlXmlWriter> bir <xref:System.Xaml.XamlWriter> alt sınıfıdır.  
  
- <xref:System.Xaml.XamlXmlWriter> XAML 'yi bir XML UTF kodlamasıyla yazar. Bunu bir metin dosyası olarak, akış olarak veya diğer formlarda kaydedebilirsiniz.  
  
- Nihai çıktıyı almak için <xref:System.Xaml.XamlXmlWriter.Flush%2A> çağırın.  
  
 XAML düğüm akışı kavramları hakkında daha fazla bilgi için bkz. [xaml düğüm akışı yapılarını ve kavramlarını anlama](understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>XamlServices sınıfı  
 XAML düğüm akışıyla uğraşmak her zaman gerekli değildir. Temel bir yükleme yolu veya temel bir kayıt yolu istiyorsanız, <xref:System.Xaml.XamlServices> sınıfında API 'Leri kullanabilirsiniz.  
  
- <xref:System.Xaml.XamlServices.Load%2A> çeşitli imzaları bir yükleme yolu uygular. Bir dosya veya akış yükleyebilir ya da bu okuyucunun API 'Leri ile yükleyerek XAML girişinizi saran bir <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> veya <xref:System.Xaml.XamlReader> yükleyebilirsiniz.  
  
- <xref:System.Xaml.XamlServices.Save%2A> çeşitli imzaları bir nesne grafiğini kaydeder ve çıkış, dosya veya <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> örneği olarak çıktı üretir.  
  
- <xref:System.Xaml.XamlServices.Transform%2A>, bir yük yolunu ve kayıt yolunu tek bir işlem olarak bağlayarak XAML 'yi dönüştürür. <xref:System.Xaml.XamlReader> ve <xref:System.Xaml.XamlWriter>için farklı bir şema bağlamı ya da farklı bir yedekleme türü sistemi kullanılabilir ve bu, sonuçta elde edilen XAML 'in nasıl dönüştürüldüğünü etkiler.  
  
 <xref:System.Xaml.XamlServices>kullanma hakkında daha fazla bilgi için bkz. [XamlServices sınıfı ve temel xaml okuma veya yazma](xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>XAML tür sistemi  
 XAML tür sistemi, bir XAML düğüm akışının belirli bir düğümüyle çalışması için gerekli olan API 'Leri sağlar.  
  
 <xref:System.Xaml.XamlType> bir nesnenin gösterimidir-bir başlangıç nesnesi düğümü ve son nesne düğümü arasında işleme yaptığınız işlem.  
  
 <xref:System.Xaml.XamlMember>, bir nesnenin bir üyesinin gösterimidir-bir başlangıç üyesi düğümü ve son üye düğümü arasında işlediklerinizi.  
  
 <xref:System.Xaml.XamlType.GetAllMembers%2A> ve <xref:System.Xaml.XamlType.GetMember%2A> ve <xref:System.Xaml.XamlMember.DeclaringType%2A> gibi API 'Ler, <xref:System.Xaml.XamlType> ve <xref:System.Xaml.XamlMember>arasındaki ilişkileri raporlar.  
  
 XAML türü sisteminin .NET Framework XAML Hizmetleri tarafından uygulanan varsayılan davranışı, ortak dil çalışma zamanı (CLR) ve yansıma kullanılarak derlemelerdeki CLR türlerinin statik analizini temel alır. Bu nedenle, belirli bir CLR türü için XAML türü sisteminin varsayılan uygulanması, bu tür ve üyelerinin XAML şemasını ortaya çıkarır ve XAML tür sistemi açısından rapor edebilir. Varsayılan XAML tür sisteminde, türlerin tür sızma kavramı CLR devralmayla eşlenir ve örneklerin, değer türlerinin ve benzerliği kavramlarını CLR 'nin destekleyici davranışlarına ve özelliklerine de eşlenir.  
  
## <a name="reference-for-xaml-language-features"></a>XAML dil özellikleri için başvuru  
 Xaml 'yi desteklemek için .NET Framework xaml Hizmetleri, XAML dili XAML ad alanı için tanımlanan belirli XAML dil kavramlarının uygulanmasını sağlar. Bunlar, belirli başvuru sayfaları olarak belgelenmiştir. Dil özellikleri, .NET Framework XAML Hizmetleri tarafından tanımlanan XAML okuyucusu veya XAML yazıcı tarafından işlendiğinde bu dil özelliklerinin nasıl davranacağını gösteren perspektifinden belgelenmiştir. Daha fazla bilgi için bkz. [xaml ad alanı (x:) Dil özellikleri](xaml-namespace-x-language-features.md).

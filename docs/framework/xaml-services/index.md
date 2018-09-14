---
title: XAML Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 373478e8c21fca66cbfbf7a58fc7d53f65ce5d0b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617389"
---
# <a name="xaml-services"></a>XAML Hizmetleri
Bu konu, .NET Framework XAML Hizmetleri bilinen bir teknoloji kümesi yeteneklerini açıklar. Çoğu açıklanan API'leri ve Hizmetleri ile sunulan bir derleme System.Xaml, derlemede bulunur [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] .NET core derleme kümesi. Hizmetler dahil okuyucular ve yazıcılar, şema sınıfları ve şema desteği, fabrikaları, sınıflar, XAML dil desteği ve diğer XAML dil özellikleri öznitelik atanıyor.  
  
## <a name="about-this-documentation"></a>Bu belge hakkında  
 .NET Framework XAML hizmetlerinde için kavramsal belgelerde, XAML dili ve nasıl, belirli bir framework örneğin geçerli olabilecek önceki deneyim sahibi olduğunuzu varsayar [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] Windows Workflow Foundation ya da belirli bir teknoloji özelliği alan, örneğin yapı özelleştirmesini özellikleri <xref:Microsoft.Build.Framework.XamlTypes>. Bu belge, bir biçimlendirme dili, XAML sözdizimi terminolojisi veya diğer tanıtım malzemeleri XAML temelleri açıklamak denemez. Bunun yerine, bu belge, etkin .NET Framework XAML hizmetlerinde System.Xaml derleme Kitaplığı'nda özellikle kullanmaya odaklanmıştır. Bu API'lerin çoğu, XAML dili tümleştirme ve genişletilebilirlik senaryoları içindir. Bu, aşağıdakilerden herhangi birini içerebilir:  
  
-   Temel XAML okuyucular veya XAML yazıcılar (XAML düğümü akışı doğrudan işleme; kendi XAML okuyucu veya XAML yazıcı türetme) yeteneklerini genişletme.  
  
-   Sistem özellikleri için .NET Framework XAML hizmetlerinde belirli çerçeve bağımlılıklarını olmayan XAML kullanılabilir özel türleri tanımlama ve bunların XAML iletmek için türlerinden öznitelik atanıyor yazın.  
  
-   Bir görsel tasarımcı veya XAML biçimlendirme kaynakları için etkileşimli bir düzenleyici gibi bir uygulama bileşeni XAML okuyucular veya XAML yazıcılar barındırma.  
  
-   XAML değer dönüştürücüler (biçimlendirme uzantıları; özel türler için tür dönüştürücüleri) yazma.  
  
-   Özel bir XAML şema içeriği tanımlama (yedekleme türü kaynakları için alternatif derleme yükleme teknikleri kullanarak; yerine her zaman bilinen türleri arama teknikleri kullanarak derlemeleri yansıtan; CLR kullanmayın yüklenen derleme kavramları kullanarak `AppDomain` ve kendi ilişkili güvenlik modelini).  
  
-   Temel XAML tür sistemi genişletme.  
  
-   Kullanarak `Lookup` veya `Invoker` XAML etkilemek için teknikleri, sistem ve türü backings nasıl değerlendirilir yazın.  
  
 XAML dil olarak tanıtım ortama arıyorsanız deneyebilecekleriniz [XAML genel bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). XAML bu konuda yeni bir hedef kitle için hem de anlatılmaktadır [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ve ayrıca XAML biçimlendirme ve XAML dil özelliklerini kullanma. Başka bir kullanışlı tanıtım malzeme belgesidir [XAML dil belirtimi](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET framework XAML hizmetlerinde ve .NET mimarisinde System.Xaml  
 XAML dil özellikleri uygulanan Microsoft .NET Framework üzerine inşa edilmiş çerçeveleri tarafından'Microsoft .NET Framework'ün önceki sürümlerinde desteği ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation ve Windows Communication Foundation (WCF)) ve bu nedenle davranışını ve kullanılan API'ye bağlı olarak hangi belirli framework kullanmakta olduğunuz çeşitli. Bu XAML dahil Ayrıştırıcı ve Nesne grafiği oluşturma mekanizması, XAML dili iç bilgi, seri hale getirme desteği ve benzeri.  
  
 İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework XAML hizmetlerinde ve System.Xaml derleme XAML dili özelliklerini desteklemek için ihtiyacınız olan şey çoğunu tanımlayın. Bu, XAML okuyucular ve XAML yazıcılar için temel sınıflar içerir. Çerçeveye özgü XAML uygulamaları hiçbirinde yoktu .NET Framework XAML hizmetlerinde eklenen en önemli özelliği, XAML için tür sistemi gösterimidir. Tür sistemi gösterimi XAML XAML yeteneklerini bağımlılıkları belirli çerçeveleri yeteneklerine duruma geçirmek zorunda kalmadan merkezi bir nesne yönelimli bir şekilde sunar.  
  
 XAML tür sistemi biçimlendirme form veya kaynağın XAML çalışma zamanı özellikleri ile sınırlı değildir; ya da herhangi bir belirli yedekleme tür sistemi tarafından sınırlandırılır. XAML tür sistemi, türleri, üyeler, XAML şema bağlamları, XML düzeyinde kavramları ve diğer XAML dil kavramları veya XAML iç nesne ifadeleri içerir. XAML tür sistemi genişletme veya kullanarak XAML okuyucular ve yazıcılar XAML gibi bir sınıf türetin ve XAML gösterimleri belirli özellikleri çerçevesi, bir teknoloji veya tüketen bir uygulama tarafından etkin olarak genişletmek mümkün kılar veya XAML yayar. Birleşimi, derleme bilgilerini bağlamı ve XAML düğümü üzerinden iletilen gibi bir teknoloji yedekleme tür sistemi bir XAML nesne yazıcı uygulaması pratik nesne grafik yazma işlemlerinden bir XAML şema içeriği kavramı sağlar kaynağı. XAML şema kavramı hakkında daha fazla bilgi için. bkz: [varsayılan XAML şema içeriği ve WPF XAML şema içeriği](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML düğümü akışları, XAML okuyucular ve yazıcılar XAML  
 XAML dil ve XAML kullanan bir dili olarak belirli teknolojileri arasındaki ilişkiye .NET Framework XAML hizmetlerinde oynadığı rol anlamak için bu XAML düğümü akışı ve bu kavramı API'yi nasıl şekilleri kavramı anlamak yararlıdır ve terimler. XAML düğümü akışı XAML dil gösterimi ve XAML temsil eder veya tanımlayan nesne grafiğini arasındaki kavramsal bir Ara ' dir.  
  
-   XAML Okuyucu, XAML bazı biçiminde işler ve XAML düğümü akışı üretir bir varlıktır. API çağrısında bir XAML okuyucu taban sınıfı tarafından temsil edilen <xref:System.Xaml.XamlReader>.  
  
-   XAML yazan bir XAML düğümü akışı işleyen ve başka bir şey üreten bir varlıktır. API'de, XAML yazıcı taban sınıfı tarafından temsil edilen <xref:System.Xaml.XamlWriter>.  
  
 XAML ile ilgili en yaygın senaryolarda bir nesne grafiği oluşturmak için XAML yükleme ve bir uygulama ya da aracı bir nesne grafiğinin kaydediliyor ve XAML gösterimi (formunda metin dosyası olarak kaydedilen genellikle biçimlendirme) üretir. XAML yükleme ve bir nesne grafiği oluşturma genellikle bu belgede yükleme yolu olarak adlandırılır. XAML için var olan bir nesne grafiğinin seri hale getirme veya kaydetme genellikle başvurduğu kaydetme olarak bu belgede yolu.  
  
 Yükleme yolunun en yaygın türü şu şekilde açıklanabilir:  
  
-   UTF-kodlanmış XML biçiminde bir XAML gösterimi ile başlar ve bir metin dosyası olarak kaydedilir.  
  
-   Bu XAML içinde yük <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> olan bir <xref:System.Xaml.XamlReader> öğesinin alt sınıfı.  
  
-   XAML düğümü akışı sonucudur. XAML düğüm akış kullanarak tek tek düğümlere erişebileceğiniz <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API. "Geçerli kayıt" kullanarak her bir düğüm işleme XAML düğüm akış ilerlemek için burada en sık karşılaşılan işlem, benzetimini.  
  
-   XAML düğüm akış için elde edilen düğümlerin geçirmek bir <xref:System.Xaml.XamlObjectWriter> API. <xref:System.Xaml.XamlObjectWriter> olan bir <xref:System.Xaml.XamlWriter> öğesinin alt sınıfı.  
  
-   <xref:System.Xaml.XamlObjectWriter> Kaynak XAML düğümü akışı ilerlemeyi çerçevesinde bir nesne grafiği, her seferinde bir nesne yazar. Bu Yardım XAML şema içeriği ve tür sistemi destekleyen ve framework türlerini ve derlemeleri erişebilen bir uygulama ile gerçekleştirilir.  
  
-   Çağrı <xref:System.Xaml.XamlObjectWriter.Result%2A> Nesne grafiğini kök nesne elde etmek için XAML düğüm akış sonuna.  
  
 Kaydetme yolu en yaygın türü şu şekilde açıklanabilir:  
  
-   Tüm uygulama çalıştırma süresi, kullanıcı Arabirimi içeriği ve çalışma zamanı durumunu veya bir genel uygulamanın çalışma zamanında nesne temsili daha küçük bir parçasını Nesne grafiğini başlayın.  
  
-   Uygulama kök veya belge kökü gibi bir mantıksal başlangıç nesnesinden nesnelerini yük <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> olan bir <xref:System.Xaml.XamlReader> öğesinin alt sınıfı.  
  
-   XAML düğümü akışı sonucudur. XAML düğüm akış kullanarak tek tek düğümlere erişebileceğiniz <xref:System.Xaml.XamlObjectReader> ve <xref:System.Xaml.XamlReader> API. "Geçerli kayıt" kullanarak her bir düğüm işleme XAML düğüm akış ilerlemek için burada en sık karşılaşılan işlem, benzetimini.  
  
-   XAML düğüm akış için elde edilen düğümlerin geçirmek bir <xref:System.Xaml.XamlXmlWriter> API. <xref:System.Xaml.XamlXmlWriter> olan bir <xref:System.Xaml.XamlWriter> öğesinin alt sınıfı.  
  
-   <xref:System.Xaml.XamlXmlWriter> Kodlaması XAML içinde bir XML UTF yazar. Bir akış olarak veya diğer bir metin dosyası olarak kaydedebilirsiniz.  
  
-   Çağrı <xref:System.Xaml.XamlXmlWriter.Flush%2A> son çıkış elde edilir.  
  
 XAML düğüm akış kavramları hakkında daha fazla bilgi için bkz. [anlama XAML düğüm Stream yapılarını ve kavramlarını](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>XamlServices sınıfı  
 Her zaman olan bir XAML düğüm akış dağıtılacak gerekli değildir. Bir temel yük yolu veya temel bir kaydetme yolu istiyorsanız API'leri kullanabilirsiniz <xref:System.Xaml.XamlServices> sınıfı.  
  
-   Çeşitli imzalarını <xref:System.Xaml.XamlServices.Load%2A> bir yükleme yolu uygulayın. Ya da bir dosya veya akışı yükleyebilir veya yükleyebilir ve bir <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> veya <xref:System.Xaml.XamlReader> , sarmalama, XAML giriş, okuyucunun API'lerle yükleyerek.  
  
-   Çeşitli imzalarını <xref:System.Xaml.XamlServices.Save%2A> bir nesne grafiği kaydetmek ve çıktı olarak bir akış oluşturmak, dosya veya <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> örneği.  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> bir yük ile kaydetme bağlayarak XAML dönüştürür tek bir işlem olarak yol. Farklı şema içeriği veya farklı bir yedekleme tür sistemi için kullanılabilir <xref:System.Xaml.XamlReader> ve <xref:System.Xaml.XamlWriter>, olduğu ne elde edilen XAML nasıl dönüştürdüğünü etkiler.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için <xref:System.Xaml.XamlServices>, bkz: [XAMLServices sınıfı ve temel XAML okuma veya yazma](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>XAML tür sistemi  
 XAML tür sistemi, tek bir XAML düğümü akışı düğümünü verilen ile çalışmak için gereken API'ler sağlar.  
  
 <xref:System.Xaml.XamlType> bir nesnenin - ne bir nesne düğümü başlangıç ve bitiş nesne düğümü arasında işleyebildiğini gösterimidir.  
  
 <xref:System.Xaml.XamlMember> bir nesne - üyesi için ne üyesi düğümü başlangıç ve son üye düğümü arasında işleyebildiğini gösterimidir.  
  
 API'leri gibi <xref:System.Xaml.XamlType.GetAllMembers%2A> ve <xref:System.Xaml.XamlType.GetMember%2A> ve <xref:System.Xaml.XamlMember.DeclaringType%2A> arasındaki ilişkileri rapor bir <xref:System.Xaml.XamlType> ve <xref:System.Xaml.XamlMember>.  
  
 XAML tür sistemi .NET Framework XAML hizmetlerinde tarafından uygulanan varsayılan davranışını, yansıma kullanarak derlemelerde CLR türlerini statik analizini ve ortak dil çalışma zamanı (CLR) dayanır. Bu nedenle, belirli bir CLR türü için varsayılan uygulama XAML tür sistemi XAML şema türü ve üyeleri göstermek ve bunu açısından XAML tür sistemi raporlamak için kullanabileceğiniz. Varsayılan XAML tür sisteminde atanabilirliği türlerinin kavramını CLR devralma eşlenir ve örnekleri, değer türleri ve benzeri kavramlarını da destek davranışları ve CLR özelliklerini eşlenir.  
  
## <a name="reference-for-xaml-language-features"></a>XAML dil özellikleri başvurusu  
 XAML desteklemek için .NET Framework XAML hizmetlerinde özel uygulanışı XAML dili XAML ad alanı için tanımlanan XAML dil kavramları sağlar. Bu, belirli bir başvuru sayfalarına belgelenmiştir. Dil özellikleri, XAML okuyucu veya .NET Framework XAML hizmetlerinde tarafından tanımlanan XAML yazan tarafından işlendiğinde, bu dil özellikleri nasıl davranacağını perspektifinden belgelenmiştir. Daha fazla bilgi için [XAML Namespace (x:) Dil özellikleri](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).

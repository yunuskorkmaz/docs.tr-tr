---
title: XAML Hizmetleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
caps.latest.revision: 13
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f36f22e8bf68520f5f57280d33cf37990feb2df6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="xaml-services"></a>XAML Hizmetleri
Bu konu Hizmetleri .NET Framework XAML bilinen bir teknoloji kümesi özelliklerini açıklar. Açıklanan API'leri ve Hizmetleri çoğunluğu ile sunulan bir derleme System.Xaml derlemesindeki bulunur [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] .NET core derlemeler kümesini. Hizmetleri içeren okuyucuları ve yazıcıları, şema sınıfları ve şema desteği oluşturucuları sınıfları, XAML dili iç desteği ve diğer XAML dil özellikleri öznitelik atanıyor.  
  
## <a name="about-this-documentation"></a>Bu belge hakkında  
 .NET Framework XAML Hizmetleri için kavramsal belgeler varsayar, XAML dili ve nasıl, belirli bir framework örneğin geçerli olabilecek önceki deneyim sahibi olduğunuzu [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] veya Windows Workflow Foundation ya da belirli teknoloji özelliği alan, örneğin yapı özelleştirme özelliklerini <xref:Microsoft.Build.Framework.XamlTypes>. Bu belge, bir işaretleme dili, XAML sözdizimi terminolojisi ya da diğer giriş malzeme XAML temelleri açıklamak denemez. Bunun yerine, bu belge etkinleştirilen .NET Framework XAML hizmetlerinde System.Xaml derleme Kitaplığı'nda özellikle kullanarak odaklanır. Bu API'ların XAML dil tümleştirmesi ve genişletilebilirlik senaryoları için durumdadır. Bunu aşağıdakilerden herhangi birini içerebilir:  
  
-   Temel XAML okuyucular veya (XAML düğümü akışı doğrudan işleme; kendi XAML okuyucu ya da XAML yazan türetme) XAML yazıcılarının yeteneklerini genişletmenin.  
  
-   Belirli framework bağımlılıkları olmayan XAML kullanılabilir özel türleri tanımlama ve bunların XAML iletmek için türlerinden öznitelik atanıyor .NET Framework XAML Hizmetleri için sistem özelliklerine yazın.  
  
-   Görsel Tasarımcı veya XAML işaretleme kaynakları için etkileşimli Düzenleyicisi gibi bir uygulama bileşeni olarak XAML okuyucular veya XAML yazıcılarının barındırma.  
  
-   XAML değer dönüştürücüler (biçimlendirme uzantıları; tür dönüştürücüleri özel türleri için) yazma.  
  
-   Özel bir XAML şema içeriği tanımlama (bilinen türleri arama teknikleri yerine her zaman kullanarak derlemeler yansıtma; CLR kullanmayın yüklenen derleme kavramları kullanarak yedekleme türü kaynakları için alternatif derleme yükleme teknikleri kullanarak; `AppDomain` ve kendi ilişkili güvenlik modelini).  
  
-   Temel XAML tür sistemi genişletme.  
  
-   Kullanarak `Lookup` veya `Invoker` XAML etkilemek için teknikler, sistem ve türü backings nasıl değerlendirildiği yazın.  
  
 XAML dili olarak giriş ortama arıyorsanız deneyebilecekleriniz [XAML genel bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Bu konuda XAML yeni bir izleyici için her ikisini de ele alınmıştır [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ve ayrıca XAML biçimlendirme ve XAML dil özellikleri kullanılarak. Başka bir yararlı giriş malzeme belgedir [XAML dil belirtimi](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET framework XAML Hizmetleri ve .NET mimarisinde System.Xaml  
 Önceki sürümlerinde [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)], XAML dili özellikleri uygulanan üzerinde oluşturulan çerçeveleri tarafından desteği [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation ve Windows Communication Foundation (WCF)) ve bu nedenle, değiştirilen kendi davranış ve bağlı olarak belirli hangi framework kullanmakta olduğunuz kullanılan API. Bu XAML dahil Ayrıştırıcı ve onun nesnesinden grafik oluşturma mekanizması, XAML dili yapı, serileştirme desteği ve benzeri.  
  
 İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework XAML hizmetlerinde ve System.Xaml derleme XAML dil özellikleri desteklemek için gerekenleri çoğunu tanımlayın. XAML okuyucuları ve XAML yazıcıları için temel sınıflar içerir. Çerçeveye özel XAML uygulamaları hiçbirinde mevcut olmadığından .NET Framework XAML hizmetlerinde eklenen en önemli XAML tür sistem temsili özelliğidir. Tür sistemi gösterimi XAML çerçeveleri belirli özelliklerini bağımlılıkları bırakmadan XAML yeteneklerini merkezleri nesne yönelimli bir şekilde gösterir.  
  
 XAML tür sistemi biçimlendirme form veya çalışma zamanı özellikleri XAML kaynağı tarafından sınırlı değildir; veya herhangi belirli yedekleme türü sistem tarafından sınırlandırılır. XAML tür sistemi türleri, üyeler, XAML şema bağlamları, XML düzey kavramlarını ve diğer XAML dil kavramları veya XAML yapı nesne ifadeleri içerir. Kullanarak veya XAML tür sistemi genişletme XAML okuyucuları ve XAML yazıcıları gibi sınıflardan türetilir ve belirli özellikleri çerçevesi, bir teknoloji veya tüketen bir uygulama tarafından etkin içine XAML Beyanları işlevselliğini genişletmek mümkün kılar veya XAML yayar. XAML şema içeriği kavramı bir XAML nesne yazan uygulama, içerik ve XAML düğüm derleme bilgilerini aracılığıyla iletilen gibi teknoloji ait yedekleme tür sistemi birleşimi pratik nesne grafik yazma işlemlerini etkinleştirir kaynağı. XAML şema kavram hakkında daha fazla bilgi için. bkz: [varsayılan XAML şema içeriği ve WPF XAML şema içeriği](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>XAML düğümü akışları, XAML okuyucuları ve XAML yazarları  
 .NET Framework XAML hizmetlerinde XAML dili ve XAML dili olarak kullanmak belirli teknolojileri arasındaki ilişkiyi oynadığı rolü anlamak için onu bir XAML düğüm akış ve bu kavram API nasıl şekilleri kavramı anlamaya yardımcı olur ve terminolojisi. XAML düğümü akışı XAML dil gösterimi ve XAML temsil eder veya tanımlayan nesne grafiğinin arasındaki kavramsal bir Ara ' dir.  
  
-   XAML okuyucu XAML bazı biçiminde işler ve XAML düğümü akışı üreten bir varlıktır. API XAML okuyucu temel sınıfı tarafından temsil edilen <xref:System.Xaml.XamlReader>.  
  
-   XAML yazan bir XAML düğüm akış işler ve başka bir şey üreten bir varlıktır. API XAML yazan temel sınıfı tarafından temsil edilen <xref:System.Xaml.XamlWriter>.  
  
 XAML içeren iki en sık karşılaşılan senaryolardan bir nesne grafiğinin örneği oluşturmak için XAML yükleme ve bir uygulama veya aracı bir nesne grafiğinin kaydetme ve (formunda metin dosyası olarak kaydedilen genellikle biçimlendirme) XAML temsili üretir. XAML yükleme ve bir nesne grafiğinin oluşturma genellikle bu belgelerinde yükleme yolu olarak adlandırılır. Kaydetmeden veya XAML için var olan bir nesne grafiğinin seri hale getirme genellikle adlandırılır kaydetme olarak bu belgede yolu.  
  
 Yükleme yolu en yaygın türü şu şekilde açıklanabilir:  
  
-   UTF kodlu XML biçiminde bir XAML gösterimi ile başlar ve bir metin dosyası olarak kaydedilir.  
  
-   Bu XAML içine yük <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> olan bir <xref:System.Xaml.XamlReader> bir alt kümesi.  
  
-   XAML düğümü akışı sonucudur. XAML düğümü akışı kullanmanın tek tek düğümlerin erişebildiği <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API. En tipik burada "geçerli bir kayıt" kullanarak her düğüm XAML düğüm akış işleme, ilerlemek için işlemdir benzetimini.  
  
-   Sonuçta elde edilen düğümler için XAML düğümü akışı geçirmek bir <xref:System.Xaml.XamlObjectWriter> API. <xref:System.Xaml.XamlObjectWriter> olan bir <xref:System.Xaml.XamlWriter> bir alt kümesi.  
  
-   <xref:System.Xaml.XamlObjectWriter> Kaynak XAML düğümü akışı ilerlemeyi uygun her seferinde bir nesne bir nesne grafiğinin yazar. Bu bir XAML şema içeriği ve yedekleme türü sisteminin ve framework türlerini ve derlemeleri erişebileceği uygulaması Yardımı ile gerçekleştirilir.  
  
-   Çağrı <xref:System.Xaml.XamlObjectWriter.Result%2A> nesne grafiğinin kök nesnesi edinmek için XAML düğümü akışı sonunda.  
  
 En yaygın türünü kaydetme yolu şu şekilde açıklanabilir:  
  
-   Tüm uygulama çalıştırma zamanı, kullanıcı Arabirimi içeriğin ve çalışma zamanı durumunu ya da genel bir uygulamanın çalışma zamanında nesne temsili daha küçük bir parçasını nesne grafiğinin başlayın.  
  
-   Bir uygulama kökü veya belge kökü gibi bir mantıksal başlangıç nesnesinden nesnelerine yük <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> olan bir <xref:System.Xaml.XamlReader> bir alt kümesi.  
  
-   XAML düğümü akışı sonucudur. XAML düğümü akışı kullanmanın tek tek düğümlerin erişebildiği <xref:System.Xaml.XamlObjectReader> ve <xref:System.Xaml.XamlReader> API. En tipik burada "geçerli bir kayıt" kullanarak her düğüm XAML düğüm akış işleme, ilerlemek için işlemdir benzetimini.  
  
-   Sonuçta elde edilen düğümler için XAML düğümü akışı geçirmek bir <xref:System.Xaml.XamlXmlWriter> API. <xref:System.Xaml.XamlXmlWriter> olan bir <xref:System.Xaml.XamlWriter> bir alt kümesi.  
  
-   <xref:System.Xaml.XamlXmlWriter> Kodlaması bir XML UTF XAML yazar. Bir akış olarak ya da diğer formlardaki bir metin dosyası olarak kaydedebilirsiniz.  
  
-   Çağrı <xref:System.Xaml.XamlXmlWriter.Flush%2A> son çıktı elde edilir.  
  
 XAML düğümü akışı kavramları hakkında daha fazla bilgi için bkz: [anlama XAML düğüm akış yapılarını ve kavramlarını](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>XamlServices sınıfı  
 Her zaman bir XAML düğüm akış ile mücadele etmek gerekli değildir. Temel yükleme yolu veya temel bir kaydetme yolu istiyorsanız API'leri kullanabilirsiniz <xref:System.Xaml.XamlServices> sınıfı.  
  
-   Çeşitli imzalarını <xref:System.Xaml.XamlServices.Load%2A> bir yükleme yolu uygulayın. Bir dosya veya akış ya da yükleyebilir ya da yükleyebilir bir <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> veya <xref:System.Xaml.XamlReader> , sarmalama XAML girişinizi bu okuyucunun API'leri ile yükleyerek.  
  
-   Çeşitli imzalarını <xref:System.Xaml.XamlServices.Save%2A> bir nesne grafiğinin kaydedin ve bir akış olarak bir çıkış üretemeyecek dosyası veya <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> örneği.  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> bir yükleme yolu ve bir Kaydet bağlanmasıyla XAML dönüştürür yolu tek bir işlem olarak. Farklı şema bağlamı veya farklı yedekleme tür sistemi için kullanılabilecek <xref:System.Xaml.XamlReader> ve <xref:System.Xaml.XamlWriter>, olduğu ne elde edilen XAML nasıl dönüştürülür etkiler.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için <xref:System.Xaml.XamlServices>, bkz: [XAMLServices sınıfı ve temel XAML okuma veya yazma](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>XAML tür sistemi  
 XAML tür sistemi tek bir XAML düğüm akış düğümünü verilen ile çalışmak için gerekli API'ler sağlar.  
  
 <xref:System.Xaml.XamlType> bir nesnenin - ne başlangıç nesne düğümü ve son nesne düğümü arasında işliyor gösterimidir.  
  
 <xref:System.Xaml.XamlMember> bir nesne - üyesi için ne başlangıç üyesi düğümü ve son üye düğümü arasında işliyor gösterimidir.  
  
 API'leri gibi <xref:System.Xaml.XamlType.GetAllMembers%2A> ve <xref:System.Xaml.XamlType.GetMember%2A> ve <xref:System.Xaml.XamlMember.DeclaringType%2A> arasındaki ilişkileri rapor bir <xref:System.Xaml.XamlType> ve <xref:System.Xaml.XamlMember>.  
  
 .NET Framework XAML Hizmetleri tarafından uygulanan gibi XAML tür sistemi varsayılan davranışı ortak dil çalışma zamanı (CLR) ve CLR Türleri derlemelerindeki statik analizini yansıma kullanarak temel alır. Bu nedenle, belirli bir CLR türü için varsayılan uygulama XAML tür sistemi, tür ve üyeleri XAML şema kullanıma ve XAML tür sistemi bakımından rapor. Varsayılan XAML tür sistemi türleri assignability kavramı CLR devralma eşlenen ve örnekleri, değer türleri ve benzeri kavramlarını destekleyen davranışları ve CLR özelliklerini de eşlenir.  
  
## <a name="reference-for-xaml-language-features"></a>XAML dil özellikleri başvurusunu  
 XAML desteklemek için .NET Framework XAML Hizmetleri için XAML dili XAML ad uzayı tanımlanan XAML dil kavramları belirli uygulamasını sağlar. Bu belirli başvuru sayfaları olarak belgelenmiştir. Dil özellikleri XAML okuyucu veya .NET Framework XAML Hizmetleri tarafından tanımlanan XAML yazan tarafından işlendiğinde, bu dil özellikleri nasıl davranacağını açısından belgelenmiştir. Daha fazla bilgi için bkz: [XAML Namespace (x:) Dil özellikleri](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).

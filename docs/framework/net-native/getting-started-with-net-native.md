---
title: .NET Native'i Kullanmaya Başlama
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41679d4041a6a5a7b9b71a451a083c539d6b4c7b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45648034"
---
# <a name="getting-started-with-net-native"></a>.NET Native'i Kullanmaya Başlama
Windows 10 için yeni bir Windows uygulaması yazmak ister mevcut bir Windows Store app geçiriyorsanız, aynı kümesini yordamları izleyebilirsiniz. Oluşturmak için bir [!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulama, şu adımları izleyin:  
  
1.  [Windows 10 hedefleyen Evrensel Windows Platformu (UWP) uygulaması geliştirme](#Step1)ve hata ayıklama derlemeleri düzgün çalıştığından emin olmak için uygulamanızı test.  
  
2.  [Yansıma ve Serileştirme ek kullanım işlemek](#Step2).  
  
3.  [Dağıtma ve sürüm yapıları uygulamanızı test](#Step3).  
  
4.  [Meta veriler eksik el ile çözümlemeniz](#Step4)ve yineleme [3. adım](#Step3) tüm sorunlar çözülene kadar.  
  
> [!NOTE]
>  Mevcut bir Windows Store uygulamaya taşıyorsanız [!INCLUDE[net_native](../../../includes/net-native-md.md)], gözden geçirdiğinizden emin olun [geçirme bilgisayarınızı Windows Store uygulaması için .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).  
  
<a name="Step1"></a>   
## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>1. adım: Geliştirin ve UWP uygulamanızın test hata ayıklama yapıları  
 Yeni bir uygulama geliştirirken veya var olan bir geçiş olsun, herhangi bir Windows uygulaması için aynı süreci izleyin.  
  
1.  Yeni bir UWP projesi, Visual C# veya Visual Basic için evrensel Windows uygulaması şablonunu kullanarak Visual Studio'da oluşturun. Varsayılan olarak, CoreCLR tüm UWP uygulamaları hedefleyen ve yayın yapılarını .NET Native araç zinciri kullanılarak derlenir.  
  
2.  Bulunduğuna bazı bilinen uyumluluk sorunlarına olmadan .NET Native araç zinciri ile UWP uygulaması projelerini derleme arasında dikkat edin. Başvurmak [Geçiş Kılavuzu](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md) daha fazla bilgi için.  
  
 Artık C# veya Visual Basic kodu karşı yazabilirsiniz [!INCLUDE[net_native](../../../includes/net-native-md.md)] yüzey yerel sistem (veya simülatör) çalıştıran alan.  
  
> [!IMPORTANT]
>  Uygulamanızı geliştirirken, serileştirme veya yansıtma kodunuzdaki herhangi bir kullanımına dikkat edin.  
  
 Varsayılan olarak, JIT olarak derlenmiş sürüm yapıları kullanarak derlenen sırada hızlı F5 dağıtımı etkinleştirmek için hata ayıklama yapıları [!INCLUDE[net_native](../../../includes/net-native-md.md)] önceden derleme teknolojisi. Bunlar genellikle .NET Native araç zinciri ile derleme öncesinde çalışmasını sağlamak için uygulamanızı derleme ve hata ayıklama test anlamına gelir oluşturur.  
  
<a name="Step2"></a>   
## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>2. adım: ek yansıma ve Serileştirme kullanım işleme  
 Oluşturduğunuz bir çalışma zamanı yönergeleri dosyası Default.rd.xml, otomatik olarak projenize eklenir. C# dilinde geliştirme yapıyorsanız, projenizin bulunursa **özellikleri** klasör. Visual Basic'te geliştiriyorsanız, projenizin bulunursa **Projem** klasör.  
  
> [!NOTE]
>  Arka plan üzerinde neden sağlayan .NET yerel derleme işlemine genel bakış için bir çalışma zamanı yönergeleri dosyası, bkz. gerekli [.NET Native ve derleme](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Çalışma zamanı yönergeleri dosyası, uygulamanızın çalışma zamanında gereken meta verileri tanımlamak için kullanılır. Bazı durumlarda, dosyanın varsayılan sürümü yeterli olabilir. Ancak, serileştirme veya yansıtma kullanan kod dosyanın çalışma zamanı yönergeleri'daki ek girdiler gerektirebilir.  
  
 **Serileştirme**  
 Seri hale getiricileri genişletme iki kategorisi vardır ve her ikisi de çalışma zamanı yönergeleri dosyasındaki ek girdileri gerektirebilir:  
  
-   Seri hale getiricileri genişletme olmayan yansıma tabanlı. Seri hale getiricileri genişletme bulunan .NET Framework sınıf kitaplığında gibi <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıfları, yansıma kullanan değil. Ancak, gerekli serileştirilecek veya seri durumdan için nesne tabanlı kod oluşturulur.  "Microsoft Serializers" bölümünde daha fazla bilgi için bkz. [serileştirme ve meta veriler](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
-   Üçüncü taraf seri hale getiricileri genişletme Üçüncü taraf serileştirme kitaplıkları, en yaygın biri olan Newtonsoft JSON serileştirici genellikle yansıma tabanlı ve girişleri *. nesne seri hale getirme ve seri durumundan çıkarma desteklemek için rd.xml dosya. Daha fazla bilgi için "Üçüncü taraf seri hale getiricileri genişletme" bölümüne bakın [serileştirme ve meta veriler](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
 **Yansıma kullanan yöntemleri**  
 Bazı durumlarda, kodda yansıma kullanımına açık değil. Bazı ortak API'ler veya programlama modellerini yansıma API'si bir parçası olarak değerlendirilmeyen ancak başarılı bir şekilde yürütmek için yansıma kullanan. Bu, aşağıdaki tür örneği oluşturmada ve yöntemi oluşturma yöntemleri içerir:  
  
-   <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> Yöntemi  
  
-   <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> Ve <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> yöntemleri  
  
-   <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Yöntemi.  
  
 Daha fazla bilgi için [API'leri, Bel yansıma](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
> [!NOTE]
>  Çalışma zamanı yönergeleri dosyalarında kullanılan tür adları, tam olarak nitelenmiş olmalıdır. Örneğin, "Dize" yerine "System.String" dosyası belirtmeniz gerekir.  
  
<a name="Step3"></a>   
## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>3. adım: Dağıtma ve sürüm yapıları uygulamanızı test etme  
 Çalışma zamanı yönergeleri dosyası güncelleştirdikten sonra yeniden oluşturun ve uygulamanızın sürüm yapıları dağıtabilir. .NET yerel ikili dosyaları ILC.out alt belirtilen dizine yerleştirilir **yapı çıkış yolu** projenin metin kutusunun **özellikleri** iletişim kutusu, **derleme**sekmesi. Bu klasörde olmayan ikili dosyaları .NET Native ile derlenmiş henüz. Uygulamanızı baştan sona test edin ve her biri kendi Hedef platformlar üzerinde hata senaryoları da dahil olmak üzere tüm senaryoları test edin.  
  
 Uygulamanızın düzgün çalışmıyorsa (özellikle burada oluşturur durumlarda [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) veya [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) çalışma zamanında özel durumlar), sonraki'ndaki yönergeleri izleyin bölümünde, [4. adım: meta veriler eksik el ile çözümlemeniz](#Step4). İlk fırsat özel durum etkinleştirme bu hataları bulmanıza yardımcı olabilir.  
  
 Ne zaman, test ettiniz ve hata ayıklama hataları ayıklanabilir uygulamanızı oluşturur ve size anlaşılmış olur başarılara [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ve [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) test özel durumlar Uygulamanızı bir en iyi duruma getirilmiş olarak [!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulama. Bunu yapmak için etkin proje yapılandırmanızı değiştirme **hata ayıklama** için **yayın**.  
  
<a name="Step4"></a>   
## <a name="step-4-manually-resolve-missing-metadata"></a>4. adım: Meta veriler eksik el ile çözün.  
 İle karşılaşacağınız en yaygın hata [!INCLUDE[net_native](../../../includes/net-native-md.md)] masaüstünde karşılaştığınız olmayan bir çalışma zamanıdır [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), veya [ MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durum. Bazı durumlarda, meta veri olmaması kendisini öngörülemeyen davranışlara veya hatta uygulama hataları bildirilebilir. Bu bölümde, nasıl hata ayıklama ve çalışma zamanı yönergeleri dosyasına yönergeleri ekleyerek bu özel durumları çözmek açıklanmaktadır. Çalışma zamanı yönergeleri biçimi hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Çalışma zamanı yönergeleri ekledikten sonra yapmanız gerekenler [dağıtın ve uygulamanızı test](#Step3) yeniden ve tüm yeni çözmek [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) daha fazla özel durum yok karşılaştığınız kadar özel durumlar.  
  
> [!TIP]
>  Uygulamanız için kod değişiklikleri dayanıklı olacak şekilde etkinleştirmek için çalışma zamanı yönergeleri yüksek bir düzeyde belirtin.  Ad alanı ve türü düzeyleri üye düzeyi yerine çalışma zamanı yönergeleri eklemenizi öneririz. Dayanıklılık ve büyük ikili dosyalarla uzun derleme sürelerini arasında bir denge olabileceğini unutmayın.  
  
 Eksik bir meta veri özel durum adresleme bu sorunları dikkate alın:  
  
-   Özel durumdan önce yapmak uygulama edebiliyordum ne?  
  
    -   Örneğin, bağlama, seri hale getirme veya verileri seri durumdan çıkarılırken veya yansıma API'si kullanarak doğrudan veri neydi?  
  
-   Bu yalıtılmış bir durumdur veya diğer türleri için aynı sorunu karşılaşacağınız düşünüyorsanız?  
  
    -   Örneğin, bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) uygulamanın nesne modelinde bir tür serileştirilirken özel durumu harekete geçirilir.  Serileştirilecek diğer türleri biliyorsanız, aynı zamanda çalışma zamanı yönergeleri türlerine (veya kodun ne kadar iyi düzenlenmiş bağlı olarak ad alanlarını,) ekleyebilirsiniz.  
  
-   Böylece yansıma kullanmaz kodu yeniden?  
  
    -   Örneğin, kod kullanımı mu `dynamic` bilebilmesi için ne tür bildiğinizde anahtar sözcüğü?  
  
    -   Kod, bazı daha iyi bir alternatif kullanılabilir olduğunda, yansıma bağımlı bir yöntem çağrısı mu?  
  
> [!NOTE]
>  Yansıma ve masaüstü uygulamalarında meta veri kullanılabilirliğini farklılıklar gelen kökü sorunlarını hakkında ek bilgi ve [!INCLUDE[net_native](../../../includes/net-native-md.md)], bakın [API'leri kullanan yansıma üzerinde](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
 Özel durum ve uygulamanızı test ederken ortaya çıkan diğer sorunları işleme bazı belirli örnekler için bkz:  
  
-   [Örnek: Veri Bağlama Sırasında Özel Durum İşleme](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)  
  
-   [Örnek: Dinamik Programlama Sorunlarını Giderme](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)  
  
-   [.NET Native Uygulamalarında Çalışma Zamanı Özel Durumları](../../../docs/framework/net-native/runtime-exceptions-in-net-native-apps.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [NIB: .NET yerel kurulumu ve yapılandırması](https://msdn.microsoft.com/library/7c9bc375-8b87-4c33-bede-72d513e362ec)  
 [.NET Native ve Derleme](../../../docs/framework/net-native/net-native-and-compilation.md)  
 [Yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [Yansıma Kullanan API'ler](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
 [Serileştirme ve Meta Veriler](../../../docs/framework/net-native/serialization-and-metadata.md)  
 [Windows Mağazası Uygulamanızı .NET Native'e Taşıma](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)

---
title: ".NET Native'i Kullanmaya Başlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
caps.latest.revision: "29"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 07882617e7625c07bade85c59116581e16f95121
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-net-native"></a>.NET Native'i Kullanmaya Başlama
Windows 10 için yeni bir Windows uygulaması yazma veya varolan bir Windows mağazası uygulaması geçirdiğiniz yordamları aynı kümesini izleyebilirsiniz. Oluşturmak için bir [!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulama, şu adımları izleyin:  
  
1.  [Windows 10 hedefleyen bir evrensel Windows Platformu (UWP) uygulaması geliştirme](#Step1)ve hata ayıklama derlemeleri düzgün çalıştığından emin olmak için uygulamanızı test.  
  
2.  [Ek yansıma ve Serileştirme kullanım işlemek](#Step2).  
  
3.  [Dağıtma ve yayın derlemeleri, uygulamanızın sınama](#Step3).  
  
4.  [El ile eksik meta veri çözümleme](#Step4)ve yineleyin [3. adım](#Step3) tüm sorunlar çözülene kadar.  
  
> [!NOTE]
>  Varolan bir Windows mağazası uygulaması taşıyorsanız [!INCLUDE[net_native](../../../includes/net-native-md.md)], gözden geçirmeyi unutmayın [geçirme Windows mağazası uygulamanızı .NET yerele](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).  
  
<a name="Step1"></a>   
## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>1. adım: Geliştirmek ve UWP uygulamanızı test hata ayıklama derlemeleri  
 Mevcut bir geçiş veya yeni bir uygulama geliştiren olsun, herhangi bir Windows uygulama için olduğu gibi aynı süreci izleyin.  
  
1.  Visual C# veya Visual Basic için evrensel Windows uygulaması şablonu kullanarak Visual Studio'da yeni bir UWP projesi oluşturun. Varsayılan olarak, tüm UWP uygulamaları CoreCLR hedef ve .NET yerel araç zinciri kullanarak sürüm yapılarına derlenir.  
  
2.  Olduğunu bazı bilinen uyumluluk sorunlarına olmadan .NET yerel araç zinciri ile UWP uygulaması projeleri derleme arasında unutmayın. Başvurmak [Geçiş Kılavuzu](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md) daha fazla bilgi için.  
  
 C# veya Visual Basic kod karşı şimdi yazabilirsiniz [!INCLUDE[net_native](../../../includes/net-native-md.md)] yüzey yerel sistemde (veya benzetici) çalışır alanı.  
  
> [!IMPORTANT]
>  Uygulamanızı geliştirirken, seri hale getirme veya yansıma kodunuzda herhangi bir kullanımından unutmayın.  
  
 JIT-derlenmiş kullanarak sürüm derlemeleri derlenmiş sırada hızlı F5 dağıtımını etkinleştirmek için varsayılan olarak, hata ayıklama yapıları [!INCLUDE[net_native](../../../includes/net-native-md.md)] ön derleme teknolojisi. Derleme ve hata ayıklama test anlamına gelir, bunlar normalde olan .NET yerel araç zinciri derleme önce çalışmasını sağlamak için uygulamanızın oluşturur.  
  
<a name="Step2"></a>   
## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>2. adım: ek yansıma ve seri hale getirme kullanım işleme  
 Oluşturduğunuzda Default.rd.xml, bir çalışma zamanı yönergeleri dosyayı projenize otomatik olarak eklenir. C# geliştirme, projenizin içinde bulunur **özellikleri** klasör. Visual Basic'te ortaya çıkarsa, projenizin içinde bulunur **My proje** klasör.  
  
> [!NOTE]
>  Arka plan üzerinde neden sağlar .NET yerel derleme işlemine genel bakış için bir çalışma zamanı yönergeleri dosyası, bkz: gerekli [.NET yerel ve derleme](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Çalışma zamanı yönergeleri dosya çalışma zamanında uygulamanızın gerektiğini meta verileri tanımlamak için kullanılır. Bazı durumlarda, dosyanın varsayılan sürümü yeterli olabilir. Ancak, serileştirme veya yansıma dayanır biraz kod ek giriş çalışma zamanı yönergeleri dosyası gerektirebilir.  
  
 **Serileştirme**  
 Serileştiricileri iki kategorisi vardır ve her ikisi de ek giriş çalışma zamanı yönergeleri dosyası gerektirebilir:  
  
-   Olmayan yansıma serileştiricileri temel. Serileştiricileri bulunan .NET Framework Sınıf Kitaplığı'nda gibi <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıfları, yansıma bağlı değil. Ancak, gerekli serileştirilecek veya seri için nesne üzerinde temel kod oluşturulabilir.  Daha fazla bilgi için "Microsoft Serializers" bölümüne bakın [serileştirme ve meta veri](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
-   Üçüncü taraf serileştiricileri. Üçüncü taraf serileştirme kitaplıkları, en sık karşılaşılan biri olan Newtonsoft JSON seri hale getirici genellikle yansıma tabanlı ve girişleri *. nesne seri hale getirme ve seri durumdan çıkarma desteklemek için rd.xml dosya. Daha fazla bilgi için "Üçüncü taraf serileştiricileri" bölümüne bakın [serileştirme ve meta veri](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
 **Yansıma kullanan yöntemleri**  
 Bazı durumlarda, kodda yansıma kullanımını açık değil. Bazı ortak API'ler veya programlama desenleri API yansıma bir parçası olarak kabul değil ancak başarıyla yürütmek için yansıma kullanan. Bu aşağıdaki türü örnek oluşturma ve yöntemi oluşturma yöntemleri içerir:  
  
-   <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> Yöntemi  
  
-   <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> Ve <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> yöntemleri  
  
-   <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Yöntemi.  
  
 Daha fazla bilgi için bkz: [API'leri, Bel yansıma](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
> [!NOTE]
>  Çalışma zamanı yönergeleri dosyalarında kullanılan tür adları tam olarak nitelenmiş olmalıdır. Örneğin, dosyayı "Dize" yerine "System.String" belirtmeniz gerekir.  
  
<a name="Step3"></a>   
## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>3. adım: Dağıtın ve yayın derlemeleri, uygulamanızın test edin  
 Çalışma zamanı yönergeleri dosya güncelleştirdikten sonra yeniden oluşturun ve yayın derlemeleri, uygulamanızın dağıtın. .NET yerel ikili dosyaları içinde belirtilen dizin ILC.out alt yerleştirilir **yapı çıkış yolu** projenin metin kutusunun **özellikleri** iletişim kutusu, **derleme**sekmesi. Bu klasörde olmayan ikili dosyaları .NET yerel ile derlenmiş henüz. Uygulamanızı sınamanız ve her hedef platformlar hatası senaryoları dahil olmak üzere tüm senaryoları sınayın.  
  
 Uygulamanızın düzgün çalışmıyorsa (özellikle burada oluşturur durumlarda [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) veya [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) çalışma zamanında özel durumlar), sonraki'ndaki yönergeleri izleyin bölümünde, [4. adım: el ile eksik meta veri çözümleme](#Step4). İlk fırsat özel durum etkinleştirme bu hatalar bulmanıza yardımcı olabilir.  
  
 Ne zaman artık test ve hata ayıklama hata ayıklaması uygulamanızı oluşturur ve bunu ortadan emin [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ve [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) test özel durumlar Uygulamanızı bir en iyi duruma getirilmiş olarak [!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulama. Bunu yapmak için etkin proje yapılandırmasından değiştirin **hata ayıklama** için **sürüm**.  
  
<a name="Step4"></a>   
## <a name="step-4-manually-resolve-missing-metadata"></a>4. adım: El ile eksik meta veri çözümleme  
 En yaygın hatası ile karşılaşırsanız [!INCLUDE[net_native](../../../includes/net-native-md.md)] masaüstünde karşılaştığınız olmayan bir çalışma zamanı olan [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), veya [ MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durum. Bazı durumlarda, meta veri yokluğu kendisini beklenmeyen davranışlara veya bile uygulama hataları bildirilebilir. Bu bölümde, nasıl hata ayıklama ve çalışma zamanı yönergeleri dosyasına yönergeleri ekleyerek bu özel durumları çözmek anlatılmaktadır. Çalışma zamanı yönergeleri biçimi hakkında daha fazla bilgi için bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Çalışma zamanı yönergeleri ekledikten sonra yapmanız gerekenler [dağıtın ve uygulamanızı test](#Step3) yeniden ve herhangi bir yeni çözmek [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) daha fazla hiçbir özel durum karşılaştığınız kadar özel durumları.  
  
> [!TIP]
>  Kod değişikliklerini hataya dayanıklı uygulamanızı etkinleştirmek için çalışma zamanı yönergeleri yüksek bir düzeyde belirtin.  Üye düzeyi yerine ad alanı ve tür düzeyleri çalışma zamanı yönergeleri ekleme öneririz. Esneklik ve daha uzun derleme sürelerine sahip büyük ikili dosyalar arasında kolaylığını olabileceğini unutmayın.  
  
 Eksik bir meta veri özel belirtirken şu noktaları dikkate alın:  
  
-   Önce özel yapmak hangi uygulama çalışıyordu?  
  
    -   Örneğin, bağlama, seri hale getirme verileri seri durumdan veya API yansıma kullanarak doğrudan veri neydi?  
  
-   Bu yalıtılmış bir durumdur veya diğer türleri için aynı sorun karşılaşacağınız düşünüyorsanız?  
  
    -   Örneğin, bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) uygulamanın nesne modelinde bir türü seri hale getirme sırasında özel durum.  Seri hale diğer türleri biliyorsanız, aynı anda çalışma zamanı yönergeleri bu türleri (veya kodun ne kadar iyi organize bağlı olarak yöntem ad alanlarını,) ekleyebilirsiniz.  
  
-   Yansıma kullanmadığı için kod yazabilirsiniz?  
  
    -   Örneğin, kod kullanımı mu `dynamic` beklenir ne tür bildiğinizde anahtar sözcüğü?  
  
    -   Kodu daha iyi bir alternatif kullanılabilir olduğunda yansıma bağımlı olan bir yöntem çağrısı mu?  
  
> [!NOTE]
>  Yansıma ve masaüstü uygulamalarında meta verilerinin kullanılabilirliği farklılıklar gelen gövdesi sorunlarını hakkında ek bilgi ve [!INCLUDE[net_native](../../../includes/net-native-md.md)], bkz: [API'leri, Bel yansıma](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
 Özel durumlar ve uygulamanızı test edilirken oluşan diğer sorunlar işleme bazı belirli örnekler için bkz:  
  
-   [Örnek: Veri Bağlama Sırasında Özel Durum İşleme](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)  
  
-   [Örnek: Dinamik Programlama Sorunlarını Giderme](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)  
  
-   [.NET Native Uygulamalarında Çalışma Zamanı Özel Durumları](../../../docs/framework/net-native/runtime-exceptions-in-net-native-apps.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [NIB: .NET yerel kurulum ve yapılandırma](http://msdn.microsoft.com/en-us/7c9bc375-8b87-4c33-bede-72d513e362ec)  
 [.NET Native ve Derleme](../../../docs/framework/net-native/net-native-and-compilation.md)  
 [Yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [Yansıma Kullanan API'ler](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
 [Serileştirme ve Meta Veriler](../../../docs/framework/net-native/serialization-and-metadata.md)  
 [Windows Mağazası Uygulamanızı .NET Native'e Taşıma](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)

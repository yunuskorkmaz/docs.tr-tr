---
title: .NET Yerel'i Kullanmaya Başlama
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de887f73a5cc3968dda7e0e4dd14493883485d2b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049732"
---
# <a name="getting-started-with-net-native"></a>.NET Yerel'i Kullanmaya Başlama

Windows 10 için yeni bir Windows uygulaması yazıyor veya var olan bir Windows Mağazası uygulamasını geçiriyorsanız aynı yordam kümesini izleyebilirsiniz. .NET Native uygulaması oluşturmak için aşağıdaki adımları izleyin:

1. [Windows 10 ' u hedefleyen bir Evrensel Windows platformu (UWP) uygulaması geliştirin](#Step1)ve düzgün çalıştığından emin olmak için uygulamanızın hata ayıklama yapılarını test edin.

2. [Ek yansıma ve serileştirme kullanımını işleyin](#Step2).

3. [Uygulamanızın yayın yapılarını dağıtın ve test edin](#Step3).

4. [Eksik meta verileri el ile çözümleyin](#Step4)ve tüm sorunlar çözümlenene kadar [3. adımı](#Step3) tekrarlayın.

> [!NOTE]
> Mevcut bir Windows Mağazası uygulamasını .NET Native geçiriyorsanız, [Windows Mağazası uygulamanızın .NET Native geçişini](migrating-your-windows-store-app-to-net-native.md)gözden geçirdiğinizden emin olun.

<a name="Step1"></a>

## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>1\. Adım: UWP uygulamanızın hata ayıklama derlemelerini geliştirin ve test edin

Yeni bir uygulama geliştirirken veya var olan bir uygulamayı geçirdiğinize göre, tüm Windows uygulamaları için aynı süreci takip edersiniz.

1. Visual Studio 'da, Visual C# veya Visual Basic Için Evrensel Windows uygulama şablonunu kullanarak yenı bir UWP projesi oluşturun. Varsayılan olarak, tüm UWP uygulamaları CoreCLR 'yi hedefleyin ve bunların yayın yapıları .NET Native araç zinciri kullanılarak derlenir.

2. .NET Native araç zinciri ve bu olmadan UWP uygulama projelerini derleme arasında bazı bilinen uyumluluk sorunları olduğunu unutmayın. Daha fazla bilgi için [geçiş kılavuzuna](migrating-your-windows-store-app-to-net-native.md) bakın.

Artık yerel sistemde ( C# veya benzeticide) çalışan .NET Native yüzey alanına karşı kod yazabilir veya Visual Basic.

> [!IMPORTANT]
> Uygulamanızı geliştirirken kodunuzda serileştirme veya yansıma kullanımını göz önünde bulabilirsiniz.

Varsayılan olarak, hata ayıklama derlemeleri hızlı F5 dağıtımını etkinleştirmek için JıT olarak derlenir, ancak yayın derlemeleri .NET Native ön derleme teknolojisi kullanılarak derlenir. Bu, .NET Native araç zinciri ile derlemeden önce normal şekilde çalışmadıklarından emin olmak için uygulamanızın hata ayıklama derlemelerini oluşturmanız ve test etmeniz gerekir.

<a name="Step2"></a>

## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>2\. Adım: Ek yansıma ve serileştirme kullanımını işleme

Çalışma zamanı yönergeleri dosyası default. RD. xml, oluşturduğunuzda projenize otomatik olarak eklenir. İçinde C#geliştirirseniz, projenizin **Özellikler** klasöründe bulunur. Visual Basic geliştirirseniz, projenin **Proje** klasöründe bulunur.

> [!NOTE]
> Çalışma zamanı yönergeleri dosyasının neden gerekli olduğuna ilişkin arka plan sağlayan .NET Native derleme işlemine genel bakış için, bkz. [.NET Native ve derleme](net-native-and-compilation.md).

Çalışma zamanı yönergeleri dosyası, uygulamanızın çalışma zamanında ihtiyaç duyacağı meta verileri tanımlamak için kullanılır. Bazı durumlarda, dosyanın varsayılan sürümü yeterli olabilir. Ancak, serileştirme veya yansımaya dayanan bazı kodlar çalışma zamanı yönergeleri dosyasında ek girişler gerektirebilir.

**Serileştirme**

Serileştiricilerin iki kategorisi vardır ve her ikisi de çalışma zamanı yönergeleri dosyasında ek girişler gerektirebilir:

- Yansıma tabanlı olmayan serileştiriciler. <xref:System.Runtime.Serialization.DataContractSerializer> ,<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, Ve<xref:System.Xml.Serialization.XmlSerializer> sınıfları gibi .NET Framework sınıfı kitaplığı 'nda bulunan serileştiriciler, yansıma üzerine güvenmeyin. Ancak, seri hale getirilecek veya seri durumdan çıkarılacak nesne temel alınarak kodun oluşturulmasını gerektirir.  Daha fazla bilgi için [serileştirme ve meta verilerde](serialization-and-metadata.md)"Microsoft serileştiriciler" bölümüne bakın.

- Üçüncü taraf serileştiriciler. En yaygın olarak, Newtonsoft JSON serileştiricisi olan üçüncü taraf serileştirme kitaplıkları genellikle yansıma tabanlıdır ve nesne serileştirme ve serisini kaldırma desteği için \*. RD. xml dosyasında giriş gerektirir. Daha fazla bilgi için [serileştirme ve meta verilerde](serialization-and-metadata.md)"üçüncü taraf serileştiriciler" bölümüne bakın.

**Yansıma kullanan Yöntemler**

Bazı durumlarda, kodda yansıma kullanımı belirgin değildir. Bazı ortak API 'Ler veya programlama desenleri, yansıma API 'sinin bir parçası olarak kabul edilmez, ancak başarıyla yürütmek için yansıma üzerinde yararlanır. Bu, aşağıdaki tür örneklemesi ve yöntem oluşturma yöntemlerini içerir:

- <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> Yöntemi

- <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> Ve yöntemleri<xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>

- <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Yöntemi.

Daha fazla bilgi için bkz. [yansımaya dayanan API 'ler](apis-that-rely-on-reflection.md).

> [!NOTE]
> Çalışma zamanı yönergeleri dosyalarında kullanılan tür adlarının tam nitelikli olması gerekir. Örneğin, dosya "String" yerine "System. String" belirtmelidir.

<a name="Step3"></a>

## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>3\. Adım: Uygulamanızın yayın yapılarını dağıtın ve test edin

Çalışma zamanı yönergeleri dosyasını güncelleştirdikten sonra, uygulamanızın yayın yapılarını yeniden oluşturabilir ve dağıtabilirsiniz. .NET Native ikililer, projenin **Özellikler** Iletişim kutusunun **derleme çıkış yolu** metin kutusunda belirtilen dizinin ILC. out alt dizinine yerleştirilir, **Derle** sekmesi. Bu klasörde olmayan ikili dosyalar .NET Native ile derlenmedi. Uygulamanızı kapsamlı bir şekilde test edin ve her bir hedef platformda hata senaryoları da dahil olmak üzere tüm senaryoları test edin.

Uygulamanız düzgün çalışmıyorsa (özellikle, çalışma zamanında [MissingMetadataException](missingmetadataexception-class-net-native.md) veya [MissingInteropDataException](missinginteropdataexception-class-net-native.md) özel durumları oluşturan durumlarda), sonraki bölümdeki yönergeleri izleyin, [4. Adım: Eksik meta verileri](#Step4)el ile çözümleyin. Birinci şans özel durumlarının etkinleştirilmesi, bu hataları bulmanıza yardımcı olabilir.

Uygulamanızın hata ayıklama yapılarını test etmeniz ve hatalarını ayıkladığınızda ve [MissingMetadataException](missingmetadataexception-class-net-native.md) ve [MissingInteropDataException](missinginteropdataexception-class-net-native.md) özel durumlarını ortadan seçtiğinizden emin olduğunuzda, uygulamanızı iyileştirilmiş bir .NET Native uygulaması olarak sınamalısınız. Bunu yapmak için, etkin proje yapılandırmanızı **hata ayıklama** ' dan **Yayınla**' ya değiştirin.

<a name="Step4"></a>

## <a name="step-4-manually-resolve-missing-metadata"></a>4\. Adım: Eksik meta verileri el ile çözümleyin

Masaüstünde karşılaştığınız .NET Native en yaygın hata, bir Runtime [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)veya [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumu olduğunu öğrenirsiniz. Bazı durumlarda meta verilerin yokluğu, öngörülemeyen davranışta veya uygulama hatalarında bile kendi kendine bildirimde bulunabilir. Bu bölümde, çalışma zamanı yönergeleri dosyasına yönergeler ekleyerek bu özel durumları nasıl ayıklayacağınız ve giderebileceğinizi ele alınmaktadır. Çalışma zamanı yönergelerinin biçimi hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md). Çalışma zamanı yönergeleri eklendikten sonra, [uygulamanızı yeniden dağıtmanız ve test](#Step3) etmeniz ve yeni [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumlarını siz yapana kadar çözmeniz gerekir. daha fazla özel durum olmadan karşılaşırsınız.

> [!TIP]
> Uygulamanızın kod değişikliklerine dayanıklı olmasını sağlamak için çalışma zamanı yönergelerini yüksek düzeyde belirtin.  Çalışma zamanı yönergelerini üye düzeyi yerine ad alanı ve tür düzeylerine eklemeniz önerilir. Daha uzun derleme süreleriyle dayanıklılık ve daha büyük ikili dosyalar arasında bir zorunluluğunu getirir olabileceğini unutmayın.

Eksik bir meta veri özel durumunun adreslenmesi sırasında şu sorunları göz önünde bulundurun:

- Uygulamanın özel durumdan önce ne yapmaya çalıştığı.

  - Örneğin, veri bağlama, verileri serileştirme veya serisini kaldırma ya da doğrudan yansıma API 'sini kullanma.

- Bu yalıtılmış bir durumdur veya diğer türler için aynı sorunla karşılaşacaksınız.

  - Örneğin, uygulamanın nesne modelinde bir tür serileştirilirken bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu oluşturulur.  Seri hale getirilecek diğer türleri biliyorsanız, bu türler için çalışma zamanı yönergeleri (ya da kodun ne kadar iyi düzenlendiğine bağlı olarak, kapsayan ad alanları için) ekleyebilirsiniz.

- Kodu, yansıma kullanmaması için yeniden yazabilir misiniz?

  - Örneğin, ne tür beklendiğini bildiğiniz kod `dynamic` anahtar sözcüğünü kullanır mi?

  - Kod, daha iyi bir alternatif kullanılabilir olduğunda yansımaya bağlı olan bir yöntemi çağırsın mı?

> [!NOTE]
> Yansımanın farklarından ve masaüstü uygulamalarında meta verilerin kullanılabilirliğine ve .NET Native yönelik sorunları işleme hakkında daha fazla bilgi için, bkz. Reflection 'ı [kullanan API 'ler](apis-that-rely-on-reflection.md).

Uygulamanızı test ederken oluşan özel durumları ve diğer sorunları işlemeye yönelik bazı özel örnekler için, bkz.:

- [Örnek: Verileri bağlarken özel durumları işleme](example-handling-exceptions-when-binding-data.md)

- [Örnek: Dinamik programlama sorunlarını giderme](example-troubleshooting-dynamic-programming.md)

- [.NET Native Uygulamalarında Çalışma Zamanı Özel Durumları](runtime-exceptions-in-net-native-apps.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [.NET Native kurulum ve yapılandırma](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))
- [.NET Native ve Derleme](net-native-and-compilation.md)
- [Yansıma ve .NET Native](reflection-and-net-native.md)
- [Yansıma Kullanan API'ler](apis-that-rely-on-reflection.md)
- [Serileştirme ve Meta Veriler](serialization-and-metadata.md)
- [Windows Mağazası Uygulamanızı .NET Native'e Taşıma](migrating-your-windows-store-app-to-net-native.md)

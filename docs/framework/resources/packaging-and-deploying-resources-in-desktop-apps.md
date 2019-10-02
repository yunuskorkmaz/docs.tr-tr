---
title: .NET uygulamalarında kaynakları paketleme ve dağıtma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aae38c8c2446ead128925e0e1d910ae12c8f220f
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736751"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>.NET uygulamalarında kaynakları paketleme ve dağıtma

Uygulamalar, yerelleştirilmiş kaynakları almak için <xref:System.Resources.ResourceManager> sınıfıyla temsil edilen .NET Framework Kaynak Yöneticisi güvenir. Kaynak Yöneticisi, bir hub ve bağlı bileşen modelinin kaynakları paketleyip dağıtmak için kullanıldığını varsayar. Hub, yerelleştirilemeyen yürütülebilir kodu ve bağımsız veya varsayılan kültür olarak adlandırılan tek bir kültürün kaynaklarını içeren ana derlemedir. Varsayılan kültür, uygulamanın geri dönüş kültürüdür; Bu, yerelleştirilmiş kaynaklar bulunamazsa kaynakları kullanılan kültürdür. Her bir bağlı bileşen tek bir kültürün kaynaklarını içeren bir uydu derlemesine bağlanır, ancak herhangi bir kod içermez.

Bu modelin çeşitli avantajları vardır:

- Bir uygulamayı dağıttıktan sonra, yeni kültürler için artımlı olarak kaynak ekleyebilirsiniz. Kültüre özgü kaynakların sonraki geliştirmesi önemli miktarda zaman gerektirebileceğinden, bu, önce ana uygulamanızı serbest bırakmanıza ve daha sonra kültüre özgü kaynaklar sunmanıza olanak tanır.
- Uygulamanın uydu derlemelerini uygulamayı yeniden derlemeden güncelleştirebilir ve değiştirebilirsiniz.
- Uygulamanın yalnızca belirli bir kültür için gereken kaynakları içeren uydu derlemelerini yüklemesi gerekir. Bu, sistem kaynaklarının kullanımını önemli ölçüde azaltabilir.

 Ancak, bu modelin olumsuz yönleri de vardır:

- Birden çok kaynak kümesini yönetmeniz gerekir.
- Birkaç yapılandırmayı test etmeniz gerektiğinden, bir uygulamanın test edilmesine yönelik başlangıç maliyeti artar. Uzun vadede, birden çok uydu ile bir çekirdek uygulamanın test etmek ve birkaç paralel uluslararası sürümü test etmek için daha kolay ve daha düşük maliyetli olacağını unutmayın.

## <a name="resource-naming-conventions"></a>Kaynak adlandırma kuralları

Uygulamanızın kaynaklarını paketlemeyi seçtiğinizde, ortak dil çalışma zamanının beklediği kaynak adlandırma kurallarını kullanarak bunları adlandırmalısınız. Çalışma zamanı bir kaynağı kültür adına göre tanımlar. Her kültüre, genellikle bir dille ilişkili iki harfli, küçük harfli bir kültür adının birleşimi ve gerekirse, bir ülke veya bölgeyle ilişkili iki harfli, büyük harfli bir alt kültür adı olan benzersiz bir ad verilir. Alt kültür adı, bir tire (-) ile ayrılmış olarak kültür adını izler. Japonca, Japonya 'da konuşulan Japonca için ja-JP, Birleşik Devletler Ingilizce için en-US, Almanya 'da konuşulan olarak Almanca için de, Almanya için de ve [Windows tarafından desteklenen dil/bölge adları listesindeki](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) **Dil etiketi** sütununa bakın. Kültür adları [BCP 47](https://tools.ietf.org/html/bcp47)tarafından tanımlanan standardı izler.

> [!NOTE]
> Çince (Basitleştirilmiş) için `zh-Hans` gibi iki harfli kültür adları için bazı özel durumlar vardır.

> [!NOTE]
> Kaynak dosyaları oluşturma hakkında daha fazla bilgi için bkz. [kaynak dosyaları oluşturma](creating-resource-files-for-desktop-apps.md) ve [uydu derlemeleri oluşturma](creating-satellite-assemblies-for-desktop-apps.md).

<a name="cpconpackagingdeployingresourcesanchor1"></a>

## <a name="the-resource-fallback-process"></a>Kaynak geri dönüş Işlemi

Paketleme ve dağıtım kaynakları için merkez ve bağlı bileşen modeli, uygun kaynakları bulmak için bir geri dönüş işlemi kullanır. Bir uygulama kullanılamayan bir yerelleştirilmiş kaynak isterse, ortak dil çalışma zamanı, kullanıcının applicationın isteğiyle en yakından eşleşen uygun bir geri dönüş kaynağı için kültürlerin hiyerarşisini arar ve yalnızca bir özel durum oluşturur Son çare. Hiyerarşinin her düzeyinde, uygun bir kaynak bulunursa çalışma zamanı onu kullanır. Kaynak bulunamazsa, arama bir sonraki düzeyde devam eder.

Arama performansını geliştirmek için, ana derlemenizin <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliğini uygulayın ve ana derlemeinizle birlikte çalışacak bağımsız dilin adını geçirin.

### <a name="net-framework-resource-fallback-process"></a>Kaynak geri dönüş işlemini .NET Framework

.NET Framework kaynak geri dönüş işlemi aşağıdaki adımları içerir:

> [!TIP]
> Kaynak geri dönüş işlemini ve kaynak derlemelerinin çalışma zamanı araştırmalarını iyileştirmek için [\<relativeBindForResources >](../configure-apps/file-schema/runtime/relativebindforresources-element.md) yapılandırma öğesini kullanabilirsiniz. Daha fazla bilgi için [kaynak geri dönüş Işlemini En Iyi duruma getirme](packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) bölümüne bakın.

1. Çalışma zamanı, uygulamanız için istenen kültür ile eşleşen bir derleme için [genel derleme önbelleğini](../app-domains/gac.md) denetler.

     Genel derleme önbelleği, birçok uygulama tarafından paylaşılan kaynak derlemelerini depolayabilirler. Bu, oluşturduğunuz her uygulamanın dizin yapısına belirli kaynak kümelerini dahil etmek zorunda kalmaktan kurtarır. Çalışma zamanı derlemeye bir başvuru bulursa, istenen kaynak için derlemeyi arar. Girdiyi derlemede bulursa, istenen kaynağı kullanır. Girişi bulamazsa, aramaya devam eder.

2. Sonraki çalışma zamanı, istenen kültür ile eşleşen bir alt dizin için şu anda yürütülmekte olan derlemenin dizinini denetler. Alt dizini bulursa, istenen kültür için geçerli bir uydu derlemesi için bu alt dizini arar. Çalışma zamanı daha sonra, istenen kaynak için uydu derlemesinde arama yapar. Kaynağı derlemede bulursa, onu kullanır. Kaynak bulamazsa, aramaya devam eder.

3. Sonraki çalışma zamanı, uydu derlemesinin isteğe bağlı olarak yüklenip yüklenmeyeceğini öğrenmek için Windows Installer sorgular. Bu durumda, yüklemeyi işler, derlemeyi yükler ve veya istenen kaynağı arar. Kaynağı derlemede bulursa, onu kullanır. Kaynak bulamazsa, aramaya devam eder.

4. Çalışma zamanı, uydu derlemesini bulamadığını göstermek için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını oluşturur. Olayı derlemeyi seçerseniz, olay işleyiciniz, kaynakları arama için kullanılacak olan uydu derlemesine bir başvuru döndürebilir. Aksi takdirde, olay işleyicisi `null` döndürür ve arama devam eder.

5. Sonraki çalışma zamanı, genel derleme önbelleğinde bu kez, istenen kültür için üst derleme için yeniden arama yapar. Üst derleme genel derleme önbelleğinde varsa, çalışma zamanı, istenen kaynak için derlemeyi arar.

     Üst kültür uygun geri dönüş kültürü olarak tanımlanır. Herhangi bir kaynağın sağlanması bir özel durum oluşturmak tercih ettiğinden, üst öğeleri geri dönüş adayları olarak değerlendirin. Bu işlem, kaynakları yeniden kullanmanıza da olanak tanır. Yalnızca alt kültürün istenen kaynağı yerelleştirilmesi gerekmiyorsa, üst düzeyde belirli bir kaynağı dahil etmelisiniz. Örneğin, `en` (nötr Ingilizce) için uydu derlemeleri, `en-GB` (Birleşik Krallık 'ta konuşulan Ingilizce) ve `en-US` ' yi (Ingilizce Birleşik Devletler konuşulan gibi) sağlarsanız, `en` uydu ortak terminolojiyi ve @no__ t-4 ve `en-US` uydu yalnızca farklı şartlar için geçersiz kılmalar sağlayabilir.

6. Sonraki çalışma zamanı, ana dizin içerip içermediğini görmek için şu anda yürütülmekte olan derlemenin dizinini denetler. Bir üst dizin varsa, çalışma zamanı, üst kültürün geçerli bir uydu derlemesi için dizini arar. Derlemeyi bulursa, çalışma zamanı, istenen kaynak için derlemeyi arar. Kaynağı bulursa onu kullanır. Kaynak bulamazsa, aramaya devam eder.

7. Sonraki çalışma zamanı, üst uydu derlemesinin isteğe bağlı olarak yüklenip yüklenmeyeceğini öğrenmek için Windows Installer sorgular. Bu durumda, yüklemeyi işler, derlemeyi yükler ve veya istenen kaynağı arar. Kaynağı derlemede bulursa, onu kullanır. Kaynak bulamazsa, aramaya devam eder.

8. Çalışma zamanı, uygun bir geri dönüş kaynağı bulamadığını göstermek için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını oluşturur. Olayı derlemeyi seçerseniz, olay işleyiciniz, kaynakları arama için kullanılacak olan uydu derlemesine bir başvuru döndürebilir. Aksi takdirde, olay işleyicisi `null` döndürür ve arama devam eder.

9. Daha sonra çalışma zamanı, önceki üç adımda olduğu gibi, üst derlemeleri birçok olası düzey aracılığıyla arar. Her kültürün yalnızca bir üst öğesi vardır ve bu, <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> özelliği tarafından tanımlanır, ancak üst öğenin kendi üst öğesi olabilir. Bir kültürün <xref:System.Globalization.CultureInfo.Parent%2A> özelliği <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ' i döndürdüğünde üst kültürleri için arama durduruluyor. kaynak geri dönüşü için, sabit kültür bir üst kültür veya kaynaklara sahip bir kültür olarak kabul edilmez.

10. İlk olarak belirtilen kültür ve tüm ebeveynler arandıysa ve kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürün kaynağı kullanılır. Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesine dahil edilmiştir. Ancak, kaynaklar için en son geri dönüş konumunun ana derleme yerine bir uydu derlemesi olduğunu göstermek için <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliğinin <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> özelliği için <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> değerini belirtebilirsiniz.

    > [!NOTE]
    > Varsayılan kaynak, ana derlemeyle derlenebilecek tek kaynaktır. @No__t-0 özniteliğini kullanarak bir uydu derlemesi belirtmediğiniz müddetçe, bu, son geri dönüş (son üst öğe) öğesidir. Bu nedenle, ana derlemenizin her zaman varsayılan bir kaynak kümesi içermesini öneririz. Bu, özel durumların oluşmasını önlemeye yardımcı olur. Varsayılan bir kaynak dahil ederek, tüm kaynaklar için bir geri dönüş sağlarsınız ve çok önemli olmasa bile Kullanıcı için en az bir kaynağın her zaman mevcut olduğundan emin olabilirsiniz.

11. Son olarak, çalışma zamanı varsayılan (geri dönüş) kültürü için bir kaynak bulamazsa, kaynağın bulunamadığını göstermek için bir <xref:System.Resources.MissingManifestResourceException> veya <xref:System.Resources.MissingSatelliteAssemblyException> özel durumu oluşturulur.

Örneğin, uygulamanın Ispanyolca (Meksika) için yerelleştirilmiş bir kaynak istediğini varsayalım (`es-MX` kültür). Çalışma zamanı önce, `es-MX` ile eşleşen derleme için genel derleme önbelleğinde arama yapmaz, ancak bulamaz. Çalışma zamanı daha sonra `es-MX` dizini için şu anda yürütülmekte olan derlemenin dizinini arar. Çalışma zamanı, genel derleme önbelleğini, uygun geri dönüş kültürünü yansıtan bir üst derleme için yeniden arar — bu durumda, `es` (Ispanyolca). Üst derleme bulunamazsa, çalışma zamanı karşılık gelen bir kaynağı bulana kadar `es-MX` kültürü için tüm olası üst derleme düzeylerini arar. Bir kaynak bulunamazsa, çalışma zamanı varsayılan kültür için kaynağı kullanır.

<a name="Optimizing"></a>

#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>.NET Framework kaynak geri dönüş Işlemini iyileştirme

Aşağıdaki koşullarda, çalışma zamanının uydu derlemelerindeki kaynakları arayacağı süreci iyileştirebilirsiniz

- Uydu derlemeleri kod derlemesiyle aynı konumda dağıtılır. Kod derlemesi [genel derleme önbelleğinde](../app-domains/gac.md)yüklüyse, uydu derlemeleri genel bütünleştirilmiş kod önbelleğine de yüklenir. Kod derlemesi bir dizinde yüklüyse, uydu derlemeleri bu dizinin kültüre özgü klasörlerine yüklenir.

- Uydu derlemeleri isteğe bağlı olarak yüklenmez.

- Uygulama kodu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını işlemez.

Aşağıdaki örnekte gösterildiği gibi [\<relativeBindForResources >](../configure-apps/file-schema/runtime/relativebindforresources-element.md) öğesini ekleyerek ve `enabled` özniteliğini uygulama yapılandırma dosyasında `true` olarak ayarlayarak uydu derlemelerinin araştırmasını iyileştirebilirsiniz.

```xml
<configuration>
   <runtime>
      <relativeBindForResources enabled="true" />
   </runtime>
</configuration>
```

Uydu derlemeleri için iyileştirilmiş araştırma bir katılım özelliğidir. Diğer bir deyişle, çalışma zamanı, uygulamanın yapılandırma dosyasında [\<relativeBindForResources >](../configure-apps/file-schema/runtime/relativebindforresources-element.md) öğesi mevcut olmadığı ve `enabled` özniteliği `true` olarak ayarlandığından [kaynak geri dönüş işleminde](packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) belgelenen adımları izler. Bu durumda, bir uydu derlemesini araştırma işlemi aşağıdaki gibi değiştirilmiştir:

- Çalışma zamanı, uydu derlemesi için araştırma yapmak üzere ana kod derlemesinin konumunu kullanır. Üst derleme genel derleme önbelleğinde yüklüyse, çalışma zamanı önbellekte araştırıyor ancak uygulamanın dizininde değil. Üst derleme bir uygulama dizinine yüklenirse, çalışma zamanı uygulama dizininde araştırıyor ancak genel derleme önbelleğinde değil.

- Çalışma zamanı, uydu derlemelerinin isteğe bağlı yüklemesi için Windows Installer sorgulayamaz.

- Belirli bir kaynak derlemesinin araştırması başarısız olursa, çalışma zamanı <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını yükseltmez.

### <a name="net-core-resource-fallback-process"></a>.NET Core kaynak geri dönüş işlemi

.NET Core kaynak geri dönüş işlemi aşağıdaki adımları içerir:

1. Çalışma zamanı, istenen kültür için bir uydu derlemesini yüklemeye çalışır.
     - İstenen kültür ile eşleşen bir alt dizin için şu anda yürütülmekte olan derlemenin dizinini denetler. Alt dizini bulursa, bu alt dizini istenen kültür için geçerli bir uydu derlemesi için arar ve yükler.

       > [!NOTE]
       > Büyük/küçük harfe duyarlı dosya sistemlerine (Linux ve macOS) sahip işletim sistemlerinde, kültür adı alt dizin araması büyük/küçük harfe duyarlıdır. Alt dizin adı <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (örneğin, `es` veya `es-MX`) durumuyla tam olarak eşleşmelidir.

       > [!NOTE]
       > Programcı <xref:System.Runtime.Loader.AssemblyLoadContext> ' dan özel bir derleme yük bağlamını türediyse, durum karmaşıktır. Yürütülen derleme özel içeriğe yüklenmişse, çalışma zamanı uydu derlemesini özel bağlama yükler. Bu belge için Ayrıntılar kapsam dışında. @No__t-0 ' a bakın.

     - Bir uydu montajı bulunmazsa <xref:System.Runtime.Loader.AssemblyLoadContext>, uydu derlemesini bulamadığını göstermek için <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> olayını oluşturur. Olayı tanıtıcıyı seçerseniz, olay işleyiciniz uydu derlemesine bir başvuru yükleyebilir ve döndürebilir.
     - Bir uydu derlemesi yine de bulunmazsa AssemblyLoadContext, uygulama etki alanının uydu derlemesini bulamadığını göstermek için bir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı tetiklemesine neden olur. Olayı tanıtıcıyı seçerseniz, olay işleyiciniz uydu derlemesine bir başvuru yükleyebilir ve döndürebilir.

2. Bir uydu derlemesi bulunursa, çalışma zamanı istenen kaynak için bunu arar. Kaynağı derlemede bulursa, onu kullanır. Kaynak bulamazsa, aramaya devam eder.

     > [!NOTE]
     > Uydu derlemesi içindeki bir kaynağı bulmak için, çalışma zamanı geçerli <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> için <xref:System.Resources.ResourceManager> tarafından istenen kaynak dosyasını arar. Kaynak dosyasında, istenen kaynak adını arar. Herhangi biri bulunmazsa, kaynak bulunamadı olarak kabul edilir.

3. Sonraki çalışma zamanı, her zaman 1 & 2. adımları her tekrarlanışında, üst kültür derlemelerini çok potansiyel düzeyler aracılığıyla arar.

     Üst kültür uygun bir geri dönüş kültürü olarak tanımlanır. Herhangi bir kaynağın sağlanması bir özel durum oluşturmak tercih ettiğinden, üst öğeleri geri dönüş adayları olarak değerlendirin. Bu işlem, kaynakları yeniden kullanmanıza da olanak tanır. Yalnızca alt kültürün istenen kaynağı yerelleştirilmesi gerekmiyorsa, üst düzeyde belirli bir kaynağı dahil etmelisiniz. Örneğin, `en` (nötr Ingilizce) için uydu derlemeleri, `en-GB` (Birleşik Krallık 'ta konuşulan Ingilizce) ve `en-US` ' yi (Ingilizce Birleşik Devletler konuşulan gibi) sağlarsanız, `en` uydu ortak terminolojiyi ve `en-GB` ' ü içerir. `en-US` uydu yalnızca farklı şartlar için geçersiz kılmalar sağlar.

     Her kültürün yalnızca bir üst öğesi vardır ve bu, <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> özelliği tarafından tanımlanır, ancak üst öğenin kendi üst öğesi olabilir. Bir kültürün @no__t 0 özelliği <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ' i döndürdüğünde üst kültürleri için arama durduruluyor. Kaynak geri dönüşü için, sabit kültür bir üst kültür veya kaynaklara sahip bir kültür olarak kabul edilmez.

4. İlk olarak belirtilen kültür ve tüm ebeveynler arandıysa ve kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürün kaynağı kullanılır. Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesine dahil edilmiştir. Ancak, kaynakların en son geri dönüş konumunun ana derleme yerine bir uydu derlemesi olduğunu göstermek için <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> özelliği için <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> değerini belirtebilirsiniz.

    > [!NOTE]
    > Varsayılan kaynak, ana derlemeyle derlenebilecek tek kaynaktır. @No__t-0 özniteliğini kullanarak bir uydu derlemesi belirtmediğiniz müddetçe, bu, son geri dönüş (son üst öğe) öğesidir. Bu nedenle, ana derlemenizin her zaman varsayılan bir kaynak kümesi içermesini öneririz. Bu, özel durumların oluşmasını önlemeye yardımcı olur. Varsayılan bir kaynak dosyası ekleyerek, tüm kaynaklar için bir geri dönüş sağlarsınız ve çok önemli olmasa bile Kullanıcı için en az bir kaynağın her zaman mevcut olduğundan emin olursunuz.

5. Son olarak, çalışma zamanı varsayılan (geri dönüş) kültürü için bir kaynak dosyası bulamazsa, kaynağın bulunamadığını göstermek için bir <xref:System.Resources.MissingManifestResourceException> veya <xref:System.Resources.MissingSatelliteAssemblyException> özel durumu oluşturulur. Kaynak dosyası bulunursa ancak istenen kaynak yoksa, istek @no__t döndürür-0.

### <a name="ultimate-fallback-to-satellite-assembly"></a>Uydu derlemesine Ultimate geri dönüş

İsteğe bağlı olarak ana derlemeden kaynakları kaldırabilir ve çalışma zamanının, belirli bir kültüre karşılık gelen bir uydu derlemesinden en son geri dönüş kaynaklarını yüklemesi gerektiğini belirtebilirsiniz. Geri dönüş işlemini denetlemek için <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> oluşturucusunu kullanır ve <xref:System.Resources.UltimateResourceFallbackLocation> parametresi için, temel derlemeden veya bir uydu derlemesinden geri dönüş kaynaklarını mi ayıklamalı Kaynak Yöneticisi yoksa bir değer sağlarsınız.

Aşağıdaki .NET Framework örnek, bir uygulamanın geri dönüş kaynaklarını Fransızca (`fr`) diline yönelik bir uydu derlemesinde depolamak için <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliğini kullanır. Örnek, `Greeting` adlı tek bir dize kaynağını tanımlayan iki metin tabanlı kaynak dosyasına sahiptir. Birincisi, Resources. fr. txt, bir Fransızca dil kaynağı içerir.

```text
Greeting=Bon jour!
```

İkinci, kaynak, ru. txt, bir Rusça dil kaynağı içerir.

```text
Greeting=Добрый день
```

Bu iki dosya, komut satırından [kaynak dosya Oluşturucu (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) çalıştırılarak. resources dosyalarına derlenir. Fransızca dil kaynağı için komut şu şekilde olur:

**Resgen. exe resources. fr. txt**

Rusça dil kaynağı için komut şu şekilde olur:

**Resgen. exe resources. ru. txt**

. Resources dosyaları, Fransızca dili kaynağı için komut satırından aşağıdaki gibi, [derleme Bağlayıcısı (al. exe)](../tools/al-exe-assembly-linker.md) çalıştırılarak dinamik bağlantı kitaplıklarına katıştırılır:

**Al/t: lib/Embed: resources. fr. resources/Culture: fr/Out: fr\Example1.resources.dll**

ve Rusça dil kaynağı için aşağıdaki gibi:

**Al/t: lib/Embed: resources. ru. resources/Culture: ru/Out: ru\Example1.resources.dll**

Uygulama kaynak kodu Example1.cs veya example1. vb adlı bir dosyada bulunur. Varsayılan uygulama kaynağının fr alt dizininde olduğunu göstermek için <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliğini içerir. Kaynak Yöneticisi başlatır, `Greeting` kaynağının değerini alır ve bunu konsola görüntüler.

[!code-csharp[Conceptual.Resources.Packaging#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
[!code-vb[Conceptual.Resources.Packaging#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]

Ardından aşağıdaki gibi komut C# satırından kaynak kodu derleyebilirsiniz:

```console
csc Example1.cs
```

Visual Basic Derleyicisi komutu çok benzerdir:

```console
vbc Example1.vb
```

Ana derlemede ekli kaynak olmadığından, `/resource` anahtarını kullanarak derlemek zorunda değilsiniz.

Dilini Rusça dışında bir şey olan bir sistemden çalıştırdığınızda, aşağıdaki çıktıyı görüntüler:

```output
Bon jour!
```

## <a name="suggested-packaging-alternative"></a>Önerilen paketleme alternatifi

Zaman veya bütçe kısıtlamaları, uygulamanızın desteklediği her alt kültür için bir kaynak kümesi oluşturmanızı önleyebilir. Bunun yerine, bir üst kültür için tüm ilgili alt kültürlerin kullanabileceği tek bir uydu derlemesi oluşturabilirsiniz. Örneğin, bölgeye özgü Ingilizce kaynaklar isteyen kullanıcılar tarafından alınan tek bir Ingilizce uydu bütünleştirilmiş kodu (en) ve bölgeye özgü Alman kaynakları isteyen kullanıcılar için tek bir Alman uydu derlemesi (de) sağlayabilirsiniz. Örneğin, Almanya (de-DE), Avusturya (de-AT) ve Isviçre (de-CH) için Almanca için istekler, Almanya uydu derlemesine (de) geri döner. Varsayılan kaynaklar son geri dönüşlerdir ve bu nedenle uygulamanızın kullanıcılarının büyük bölümü tarafından istenen kaynaklar olması gerekir, bu nedenle bu kaynakları dikkatle seçin. Bu yaklaşım, daha az özel olan kaynakları dağıtır, ancak uygulamanızın yerelleştirme maliyetlerini önemli ölçüde azaltabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Masaüstü uygulamalarındaki kaynaklar](index.md)
- [Genel derleme önbelleği](../app-domains/gac.md)
- [Kaynak dosyaları oluşturma](creating-resource-files-for-desktop-apps.md)
- [Uydu derlemeleri oluşturma](creating-satellite-assemblies-for-desktop-apps.md)

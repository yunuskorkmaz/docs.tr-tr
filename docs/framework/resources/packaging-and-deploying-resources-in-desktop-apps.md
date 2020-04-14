---
title: .NET Uygulamalarında Kaynakların Paketlenmesi ve Dağıtılması
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
ms.openlocfilehash: d64e3b5201e34541fdafa5724b0c7e8c3f6c0c0d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243056"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>.NET Uygulamalarında Kaynakların Paketlenmesi ve Dağıtılması

Uygulamalar, yerelleştirilmiş kaynakları almak için <xref:System.Resources.ResourceManager> sınıf tarafından temsil edilen .NET Framework Resource Manager'a güvenir. Kaynak Yöneticisi, kaynakları paketlemek ve dağıtmak için hub ve spoke modelinin kullanıldığını varsayar. Hub, yerelleştirilebilir yürütülebilir kodu ve nötr veya varsayılan kültür adı verilen tek bir kültür için kaynakları içeren ana derlemedir. Varsayılan kültür, uygulama için geri dönüş kültürüdür; yerelleştirilmiş kaynaklar bulunamıyorsa kaynakları kullanılan kültürdür. Her konuşan, tek bir kültür için kaynak içeren, ancak herhangi bir kod içermeyen bir uydu derlemesine bağlanır.

Bu modelin çeşitli avantajları vardır:

- Bir uygulama dağıttıktan sonra yeni kültürler için kaynakları artımlı olarak ekleyebilirsiniz. Kültüre özgü kaynakların sonraki gelişimi önemli miktarda zaman gerektirebileceğinden, bu, önce ana uygulamanızı serbest bırakmanızı ve kültüre özel kaynakları daha sonraki bir tarihte sunmanızı sağlar.
- Uygulamayı yeniden derlemeden bir uygulamanın uydu derlemelerini güncelleyebilir ve değiştirebilirsiniz.
- Bir uygulamanın yalnızca belirli bir kültür için gerekli kaynakları içeren uydu derlemelerini yüklemesi gerekir. Bu, sistem kaynaklarının kullanımını önemli ölçüde azaltabilir.

 Ancak, bu modelin dezavantajları da vardır:

- Birden çok kaynak kümesini yönetmeniz gerekir.
- Birkaç yapılandırmayı sınamanız gerektiğinden, bir uygulamayı sınamanın ilk maliyeti artar. Uzun vadede, birkaç paralel uluslararası sürümü test etmek ve sürdürmek yerine, bir çekirdek uygulamayı birkaç uyduyla test etmek daha kolay ve daha ucuz olacağını unutmayın.

## <a name="resource-naming-conventions"></a>Kaynak adlandırma kuralları

Uygulamanızın kaynaklarını paketlediğinizde, ortak dil çalışma zamanının beklediği kaynak adlandırma kurallarını kullanarak bunları adlandırmanız gerekir. Çalışma zamanı, bir kaynağı kültür adına göre tanımlar. Her kültüre, genellikle bir dille ilişkili iki harfli, küçük bir kültür adının ve gerekirse bir ülke veya bölgeyle ilişkili iki harfli, büyük harfli alt kültür adının birleşimi olan benzersiz bir ad verilir. Alt kültür adı, tire (-) ile ayrılan kültür adını izler. Buna örnek olarak Japonya'da konuşulan Japonca için ja-JP, Abd'de konuşulan İngilizce için en-ABD, Almanya'da konuşulan Almanca için de-DE veya Avusturya'da konuşulan Almanca için de-AT verilebilir. [Windows tarafından desteklenen dil/bölge adları listesindeki](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) **Dil etiketi** sütununa bakın. Kültür adları [BCP 47](https://tools.ietf.org/html/bcp47)tarafından tanımlanan standardı izler.

> [!NOTE]
> İki harfli kültür adları için Çince (Basitleştirilmiş) gibi `zh-Hans` bazı özel durumlar vardır.

> [!NOTE]
> Kaynak dosyaları oluşturma hakkında daha fazla bilgi için kaynak [dosyaları oluşturma](creating-resource-files-for-desktop-apps.md) ve [Uydu Derlemeleri oluşturma](creating-satellite-assemblies-for-desktop-apps.md)hakkında bilgi için bkz.

<a name="cpconpackagingdeployingresourcesanchor1"></a>

## <a name="the-resource-fallback-process"></a>Kaynak Geri Dönüş İşlemi

Kaynakları paketlemek ve dağıtmak için hub ve spoke modeli, uygun kaynakları bulmak için bir geri dönüş işlemi kullanır. Bir uygulama kullanılamayan yerelleştirilmiş bir kaynak isterse, ortak dil çalışma zamanı, kullanıcının isteğiyle en çok eşleşen uygun bir geri dönüş kaynağı için kültürler hiyerarşisini arar ve yalnızca son çare olarak bir özel durum atar. Hiyerarşinin her düzeyinde, uygun bir kaynak bulunursa, çalışma zamanı onu kullanır. Kaynak bulunamazsa, arama bir sonraki düzeyde devam ediyor.

Arama performansını artırmak için, <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliği ana derlemenize uygulayın ve ana derlemenizle çalışacak nötr dilin adını geçirin.

### <a name="net-framework-resource-fallback-process"></a>.NET Framework kaynak geri dönüş süreci

.NET Framework kaynak geri dönüş işlemi aşağıdaki adımları içerir:

> [!TIP]
> Kaynak geri dönüş işlemini ve kaynak derlemeleri için çalışma zamanı sondalama işlemini en iyi duruma getirmek için [göreliBindForResources>yapılandırma öğesini kullanabilirsiniz. \<](../configure-apps/file-schema/runtime/relativebindforresources-element.md) Daha fazla bilgi için [Kaynak Geri Dönüş İşlemi](packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) bölümünü optimize etme bölümüne bakın.

1. Çalışma zamanı ilk olarak, uygulamanız için istenen kültürle eşleşen bir derleme için [genel derleme önbelleğini](../app-domains/gac.md) denetler.

     Genel derleme önbelleği, birçok uygulama tarafından paylaşılan kaynak derlemelerini depolayabilir. Bu, oluşturduğunuz her uygulamanın dizin yapısına belirli kaynak kümelerini eklemek zorunda kalmanızı sağlar. Çalışma zamanı derlemeiçin bir başvuru bulursa, istenen kaynak için derleme arar. Derlemedeki girişi bulursa, istenen kaynağı kullanır. Girişi bulamazsa, aramaya devam ediyor.

2. Çalışma zamanı sonraki, istenen kültürle eşleşen bir alt dizini için şu anda çalıştırılan derlemenin dizinini denetler. Alt dizini bulursa, istenen kültür için geçerli bir uydu derlemesi için bu alt dizini arar. Çalışma zamanı daha sonra istenen kaynak için uydu derlemesini arar. Derlemede kaynağı bulursa, onu kullanır. Kaynağı bulamazsa, aramaya devam ediyor.

3. Uydu derlemesinin isteğe bağlı olarak yüklenip yüklenmeyeceğini belirlemek için sonraki çalışma zamanı Windows Yükleyici'yi sorgular. Bu nedenle, yüklemeyi işler, derlemeyi yükler ve onu veya istenen kaynağı arar. Derlemede kaynağı bulursa, onu kullanır. Kaynağı bulamazsa, aramaya devam ediyor.

4. Çalışma süresi, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> uydu derlemesini bulamadığını belirtmek için olayı yükseltir. Olayı işlemeyi seçerseniz, olay işleyiciniz, kaynakları arama için kullanılacak olan uydu derlemesine bir başvuru döndürebilir. Aksi takdirde, olay `null` işleyicisi döndürür ve arama devam ediyor.

5. Çalışma zamanı sonraki genel derleme önbelleğini yeniden arar, bu kez istenen kültürün üst derlemesi için. Üst derleme genel derleme önbelleğinde varsa, çalışma zamanı istenen kaynak için derlemearar.

     Ana kültür uygun geri dönüş kültürü olarak tanımlanır. Herhangi bir kaynak sağlamak bir özel durum atma tercih edilir, çünkü geri dönüş adayları olarak ebeveynler düşünün. Bu işlem, kaynakları yeniden kullanmanıza da olanak tanır. Yalnızca alt kültürün istenen kaynağı yerelleştirmesi gerekmiyorsa, ana düzeye belirli bir kaynak eklemeniz gerekir. Örneğin, (tarafsız `en` İngilizce), `en-GB` (Birleşik Krallık'ta konuşulan İngilizce) ve `en-US` (ABD'de konuşulan İngilizce) için `en` uydu derlemeleri sağlarsanız, uydu `en-GB` `en-US` ortak terminolojiyi içerir ve uydular yalnızca farklı terimler için geçersiz kılma sağlayabilir.

6. Çalışma zamanı sonraki bir üst dizini içerip içermeden görmek için şu anda çalıştırılatan derlemedizini denetler. Bir üst dizini varsa, çalışma zamanı ana kültür için geçerli bir uydu derlemesi için dizin arar. Derlemeyi bulursa, çalışma zamanı istenen kaynağı derlemeyi arar. Kaynağı bulursa, kullanır. Kaynağı bulamazsa, aramaya devam ediyor.

7. Çalışma zamanı sonraki sorguları Windows Installer üst uydu derlemesi isteğe bağlı yüklü olup olmadığını belirlemek için. Bu nedenle, yüklemeyi işler, derlemeyi yükler ve onu veya istenen kaynağı arar. Derlemede kaynağı bulursa, onu kullanır. Kaynağı bulamazsa, aramaya devam ediyor.

8. Çalışma <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> süresi, uygun bir geri dönüş kaynağı bulamadığını belirtmek için olayı yükseltir. Olayı işlemeyi seçerseniz, olay işleyiciniz, kaynakları arama için kullanılacak olan uydu derlemesine bir başvuru döndürebilir. Aksi takdirde, olay `null` işleyicisi döndürür ve arama devam ediyor.

9. Çalışma zamanı sonraki aramaüst derlemeleri, önceki üç adımda olduğu gibi, birçok potansiyel düzeyleri arasında. Her <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> kültürün, özellik tarafından tanımlanan yalnızca bir üst öğesi vardır, ancak bir üst öğenin kendi üst öğesi olabilir. Bir kültürün <xref:System.Globalization.CultureInfo.Parent%2A> özelliği geri döndüğünde <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>ana kültürleri arama durur; kaynak geri dönüş için, değişmez kültür bir üst kültür veya kaynakları olabilir bir kültür olarak kabul edilmez.

10. Başlangıçta belirtilen kültür ve tüm ebeveynler aranmışsa ve kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürü için kaynak kullanılır. Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesi dahildir. Ancak, kaynaklar <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> için nihai geri <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> dönüş <xref:System.Resources.NeutralResourcesLanguageAttribute> konumunun ana derleme yerine uydu derlemesi olduğunu belirtmek için özniteliğin özelliği için bir değer belirtebilirsiniz.

    > [!NOTE]
    > Varsayılan kaynak, ana derleme yle derlenebilecek tek kaynaktır. Özniteliği kullanarak bir uydu <xref:System.Resources.NeutralResourcesLanguageAttribute> derlemesi belirtmediğiniz sürece, bu nihai geri dönüş (son ana). Bu nedenle, ana derlemenize her zaman varsayılan bir kaynak kümesi eklemenizi öneririz. Bu, özel durumların atılmasını önlemeye yardımcı olur. Varsayılan bir kaynak ekleyerek, dosya tüm kaynaklar için bir geri dönüş sağlar ve kültürel olarak özel olmasa bile, kullanıcı için her zaman en az bir kaynağın bulunduğundan emin olursunuz.

11. Son olarak, çalışma zamanı varsayılan (geri dönüş) kültürü için bir <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> kaynak bulamazsa, kaynağın bulunamadıgini belirtmek için bir veya özel durum atilir.

Örneğin, uygulamanın İspanyolca (Meksika) `es-MX` (kültür) için yerelleştirilmiş bir kaynak istediğini varsayalım. Çalışma zamanı, eşleşen `es-MX`derleme için ilk olarak genel derleme önbelleğini arar, ancak bulamaz. Çalışma zamanı daha sonra bir `es-MX` dizin için şu anda çalıştırılatan derlemenin dizinini arar. Aksi takdirde, çalışma zamanı, uygun geri dönüş kültürünü yansıtan bir üst derleme için genel derleme `es` önbelleğini yeniden arar — bu durumda, (İspanyolca). Üst derleme bulunamazsa, çalışma zamanı, ilgili bir kaynak bulana `es-MX` kadar kültür için tüm ana derleme düzeylerini arar. Bir kaynak bulunamazsa, çalışma zamanı varsayılan kültür için kaynağı kullanır.

<a name="Optimizing"></a>

#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>.NET Framework Resource Geri Dönüş İşlemini Optimize Etme

Aşağıdaki koşullar altında, uydu meclislerinde kaynakları arama zamanı nın hangi işlemi optimize edebilirsiniz

- Uydu derlemeleri kod derlemesi ile aynı konumda dağıtılır. Kod derlemesi [Genel Montaj Önbelleğine](../app-domains/gac.md)yüklenmişse, uydu derlemeleri de genel montaj önbelleğine yüklenir. Kod derlemesi bir dizine yüklenirse, uydu derlemeleri bu dizinin kültüre özgü klasörlerine yüklenir.

- Uydu montajları isteğe bağlı olarak kurulmamaktadır.

- Uygulama kodu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı işlemez.

Aşağıdaki örnekte gösterildiği `enabled` `true` [gibi, relativeBindForResources>öğesini ekleyerek ve özniteliğini uygulama yapılandırma dosyasına ayarlayarak uydu derlemeleri için sondayı optimize \<](../configure-apps/file-schema/runtime/relativebindforresources-element.md) edeyim.

```xml
<configuration>
   <runtime>
      <relativeBindForResources enabled="true" />
   </runtime>
</configuration>
```

Uydu montajları için optimize edilmiş sonda bir opt-in özelliğidir. Diğer bir deyişle, çalışma süresi, [ \<ilgilibindForResources>](../configure-apps/file-schema/runtime/relativebindforresources-element.md) öğesi uygulamanın yapılandırma dosyasında [bulunmadıkça](packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) ve `enabled` özniteliği . `true` Bu durumda, uydu derlemesi için sondalama işlemi aşağıdaki gibi değiştirilir:

- Çalışma süresi, uydu derlemesini araştırmak için ana kod derlemesinin konumunu kullanır. Üst derleme genel derleme önbelleğine yüklüyse, çalışma zamanı önbellekte sondalanır, ancak uygulamanın dizininde değil. Üst derleme bir uygulama dizinine yüklenmişse, çalışma zamanı sondaları uygulama dizininde kalır, ancak genel derleme önbelleğinde değil.

- Çalışma zamanı, uydu derlemelerinin isteğe bağlı olarak yüklenmesi için Windows Yükleyici'yi sorgulamaz.

- Belirli bir kaynak derlemesi için sonda başarısız <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olursa, çalışma süresi olayı yükseltmez.

### <a name="net-core-resource-fallback-process"></a>.NET Çekirdek kaynak geri dönüş süreci

.NET Core kaynak geri dönüş işlemi aşağıdaki adımları içerir:

1. Çalışma zamanı, istenen kültür için uydu derlemesi yüklemeye çalışır.
     - İstenen kültürle eşleşen bir alt dizini için şu anda çalıştırılan derlemenin dizinini denetler. Alt dizini bulursa, bu alt dizini istenen kültür için geçerli bir uydu derlemesi arar ve yükler.

       > [!NOTE]
       > Büyük/küçük harf duyarlı dosya sistemleri (yani, Linux ve macOS) ile işletim sistemlerinde, kültür adı alt dizin arama büyük/küçük harf duyarlıdır. Alt dizin adı tam olarak <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (örneğin, `es` veya) `es-MX`durumda eşleşmelidir.

       > [!NOTE]
       > Programcı özel bir montaj yük bağlamı <xref:System.Runtime.Loader.AssemblyLoadContext>türetilmişse, durum karmaşıktır. Yürütme derlemesi özel içeriğe yüklenmişse, çalışma zamanı uydu derlemesini özel içeriğe yükler. Bu belgenin ayrıntıları kapsam dışıdır. Bkz. <xref:System.Runtime.Loader.AssemblyLoadContext>.

     - Uydu montajı bulunamadıysa, <xref:System.Runtime.Loader.AssemblyLoadContext> <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> uydu montajını bulamadığını gösteren olay yükselir. Olayı işlemeyi seçerseniz, olay işleyiciniz uydu derlemesine bir başvuru yükleyebilir ve döndürebilir.
     - Uydu derlemesi hala bulunamadıysa, AssemblyLoadContext AppDomain'in <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> uydu derlemesini bulamadığını belirten bir olayı tetiklemesi için neden olur. Olayı işlemeyi seçerseniz, olay işleyiciniz uydu derlemesine bir başvuru yükleyebilir ve döndürebilir.

2. Uydu derlemesi bulunursa, çalışma zamanı istenen kaynağı arar. Derlemede kaynağı bulursa, onu kullanır. Kaynağı bulamazsa, aramaya devam ediyor.

     > [!NOTE]
     > Uydu derlemesi içinde bir kaynak bulmak <xref:System.Resources.ResourceManager> için, çalışma zamanı geçerli <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>için istenen kaynak dosyası için arar. Kaynak dosyası içinde istenen kaynak adını arar. Ya bulunamazsa, kaynak bulunamadı olarak kabul edilir.

3. Çalışma zamanı sonraki aramaları, ana kültür derlemelerini birçok olası düzeyde arar ve her seferinde 1 & 2 adımlarını yineler.

     Ana kültür uygun bir geri dönüş kültürü olarak tanımlanır. Herhangi bir kaynak sağlamak bir özel durum atma tercih edilir, çünkü geri dönüş adayları olarak ebeveynler düşünün. Bu işlem, kaynakları yeniden kullanmanıza da olanak tanır. Yalnızca alt kültürün istenen kaynağı yerelleştirmesi gerekmiyorsa, ana düzeye belirli bir kaynak eklemeniz gerekir. Örneğin, (tarafsız `en` İngilizce), `en-GB` (Birleşik Krallık'ta konuşulan İngilizce) ve `en-US` (ABD'de konuşulan İngilizce) için `en` uydu derlemeleri sağlıyorsanız, `en-GB` uydu `en-US` ortak terminolojiyi içerir ve uydular yalnızca farklı terimler için geçersiz kılma sağlar.

     Her <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> kültürün, özellik tarafından tanımlanan yalnızca bir üst öğesi vardır, ancak bir üst öğenin kendi üst öğesi olabilir. Bir kültürün <xref:System.Globalization.CultureInfo.Parent%2A> özelliği geri döndüğünde <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>ana kültürleri arama durur. Kaynak geri dönüşiçin değişmez kültür bir üst kültür veya kaynakları olan bir kültür olarak kabul edilmez.

4. Başlangıçta belirtilen kültür ve tüm ebeveynler aranmışsa ve kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürü için kaynak kullanılır. Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesi dahildir. Ancak, kaynakların nihai geri <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> dönüş <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> konumunun ana derleme yerine uydu derlemesi olduğunu belirtmek için özelliğin değerini belirtebilirsiniz.

    > [!NOTE]
    > Varsayılan kaynak, ana derleme yle derlenebilecek tek kaynaktır. Özniteliği kullanarak bir uydu <xref:System.Resources.NeutralResourcesLanguageAttribute> derlemesi belirtmediğiniz sürece, bu nihai geri dönüş (son ana). Bu nedenle, ana derlemenize her zaman varsayılan bir kaynak kümesi eklemenizi öneririz. Bu, özel durumların atılmasını önlemeye yardımcı olur. Varsayılan bir kaynak dosyası ekleyerek, tüm kaynaklar için bir geri dönüş sağlar ve kültürel olarak özel olmasa bile, kullanıcı için her zaman en az bir kaynağın bulunduğundan emin olursunuz.

5. Son olarak, çalışma zamanı varsayılan (geri dönüş) kültürü için bir <xref:System.Resources.MissingManifestResourceException> kaynak <xref:System.Resources.MissingSatelliteAssemblyException> dosyası bulamazsa, kaynağın bulunamadıgini belirtmek için bir veya özel durum atilir. Kaynak dosyası bulunursa ancak istenen kaynak yoksa istek `null`geri döner.

### <a name="ultimate-fallback-to-satellite-assembly"></a>Uydu Derlemesi için Ultimate Geri Dönüş

Kaynakları isteğe bağlı olarak ana derlemeden kaldırabilir ve çalışma zamanının belirli bir kültüre karşılık gelen bir uydu derlemesinden nihai geri dönüş kaynaklarını yüklemesi gerektiğini belirtebilirsiniz. Geri dönüş işlemini denetlemek için, oluşturucuyu <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29> kullanır <xref:System.Resources.UltimateResourceFallbackLocation> ve Kaynak Yöneticisi'nin geri dönüş kaynaklarını ana montajdan mı yoksa uydu derlemesinden mi ayıklaması gerektiğini belirten parametre için bir değer sağlarsınız.

Aşağıdaki .NET Framework örneği, bir uygulamanın <xref:System.Resources.NeutralResourcesLanguageAttribute> geri dönüş kaynaklarını Fransızca (`fr`) dili için uydu derlemesinde depolamak için özniteliği kullanır. Örnekte, adlı `Greeting`tek bir dize kaynağını tanımlayan iki metin tabanlı kaynak dosyası vardır. İlk, resources.fr.txt, Fransızca bir dil kaynağı içerir.

```text
Greeting=Bon jour!
```

İkincisi, kaynaklar, ru.txt, Rusça bir kaynak içerir.

```text
Greeting=Добрый день
```

Bu iki dosya, komut satırından [kaynak dosyası üretecisini (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) çalıştırarak .resources dosyalarına derlenir. Fransızca dil kaynağı için komut şudur:

**resgen.exe resources.fr.txt**

Rusça dil kaynağı için komut şudur:

**resgen.exe resources.ru.txt**

.resources dosyaları, Fransızca dil kaynağının komut satırından [derleme bağlantı layıcısını (Al.exe)](../tools/al-exe-assembly-linker.md) çalıştırarak dinamik bağlantı kitaplıklarına gömülür:

**al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**

ve Rusça dil kaynağı için aşağıdaki gibidir:

**al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**

Uygulama kaynak kodu Example1.cs veya Example1.vb adlı bir dosyada bulunur. Varsayılan uygulama <xref:System.Resources.NeutralResourcesLanguageAttribute> kaynağının fr alt dizininde olduğunu belirtmek için özniteliği içerir. Kaynak Yöneticisi'ni anında alır, `Greeting` kaynağın değerini alır ve konsola görüntüler.

[!code-csharp[Conceptual.Resources.Packaging#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
[!code-vb[Conceptual.Resources.Packaging#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]

Daha sonra komut satırından C# kaynak kodunu aşağıdaki gibi derleyebilirsiniz:

```console
csc Example1.cs
```

Visual Basic derleyicisinin komutu çok benzer:

```console
vbc Example1.vb
```

Ana derlemeye katışılmış kaynak olmadığından, `/resource` anahtarı kullanarak derlemeniz gerekmez.

Örneği Rusça'dan başka bir dili olan bir sistemden çalıştırdığınızda, aşağıdaki çıktıyı görüntüler:

```output
Bon jour!
```

## <a name="suggested-packaging-alternative"></a>Önerilen Paketleme Alternatifi

Zaman veya bütçe kısıtlamaları, uygulamanızın desteklediği her alt kültür için bir kaynak kümesi oluşturmanızı engelleyebilir. Bunun yerine, ilgili tüm alt kültürlerin kullanabileceği bir üst kültür için tek bir uydu derlemesi oluşturabilirsiniz. Örneğin, bölgeye özgü İngilizce kaynaklar isteyen kullanıcılar tarafından alınan tek bir İngilizce uydu derlemesi (tr) ve bölgeye özgü Alman kaynakları isteyen kullanıcılar için tek bir Alman uydu derlemesi (de) sağlayabilirsiniz. Örneğin, Almanya (de-DE), Avusturya (de-AT) ve İsviçre'de (de-CH) konuşulan Almanca talepleri Alman uydu meclisine (de) geri döner. Varsayılan kaynaklar son geri dönüştür ve bu nedenle uygulamanızın kullanıcılarının çoğunluğu tarafından istenecek kaynaklar olmalıdır, bu nedenle bu kaynakları dikkatle seçin. Bu yaklaşım, kültürel açıdan daha az özel olan, ancak uygulamanızın yerelleştirme maliyetlerini önemli ölçüde azaltabilecek kaynakları dağıtmaktadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Masaüstü Uygulamalarında Kaynaklar](index.md)
- [Genel Derleme Önbelleği](../app-domains/gac.md)
- [Kaynak Dosyaları Oluşturma](creating-resource-files-for-desktop-apps.md)
- [Uydu Derlemeleri Oluşturma](creating-satellite-assemblies-for-desktop-apps.md)

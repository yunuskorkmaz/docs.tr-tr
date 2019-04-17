---
title: Paketleme ve dağıtma kaynakları .NET uygulamaları
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
ms.openlocfilehash: 19f1d3d1d94db885938a5da3f3b66c8e554205b5
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611399"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>Paketleme ve dağıtma kaynakları .NET uygulamaları

Uygulamaları üzerinde .NET Framework kaynak tarafından temsil edilen Yöneticisi kullanan <xref:System.Resources.ResourceManager> yerelleştirilmiş kaynakları almak için sınıf. Resource Manager, paketleme ve dağıtma kaynakları için bir merkez ve ışınsal modelini kullanıldığını varsayar. Yerelleştirilemez yürütülebilir kod ve nötr olarak adlandırılan tek bir kültürü için kaynaklar içeren ana derleme hub'ı olan veya varsayılan kültür. Geri dönüş kültürü uygulamanın varsayılan kültürüdür; yerelleştirilmiş kaynaklar bulunamazsa kullanılan kültürdür. Her bir uçtaki tek bir kültür için kaynaklar içeriyor ancak hiçbir kod içermiyor bir uydu derlemeye bağlanır.

Bu model için çeşitli avantajları vardır:

- Bir uygulamayı dağıttıktan sonra yeni kültürleri için kaynakları artımlı olarak ekleyebilirsiniz. Kültüre özgü kaynaklar sonraki geliştirme süresini önemli ölçüde gerektirdiğinden bu, ana uygulamanızın ilk sürüm ve kültüre özgü kaynaklar daha sonraki bir tarihte teslim sağlar.

- Güncelleştirme ve uygulamayı yeniden derlemeye gerek kalmadan uygulama uydu derlemeleri değiştirin.

- Belirli bir kültür için gerekli tüm kaynakları içeren uydu derlemeleri yüklemek bir uygulama gerekir. Bu durum, sistem kaynaklarının kullanımını önemli ölçüde azaltabilir.

 Ancak, vardır de dezavantajları Bu model için:

- Birden fazla kaynakları yönetmeniz gerekir.

- Bazı yapılandırmalar test etmeniz gerekir çünkü bir uygulamayı test ilk maliyetini artırır. Uzun vadede, daha kolay ve daha az pahalı bir çekirdek uygulamayı test edin ve çeşitli paralel uluslararası sürümlerinden korumak için daha birçok Uyduları ile test etmek olacağını unutmayın.

## <a name="resource-naming-conventions"></a>Kaynak Adlandırma Kuralları

Uygulamanızdaki kaynaklarından paketlediğinizde, ortak dil çalışma zamanı bekliyor kaynak adlandırma kuralları kullanarak bunları adı olmalıdır. Çalışma zamanı kaynak kültür adını kullanarak tanımlar. Her kültür, genellikle bir dili ile ilişkilendirilmiş bir iki harf, küçük harf kültür adı birleşimi olan benzersiz bir ad verilir ve gerekirse, bir iki harfli, büyük bir alt ad ilişkili bir ülke veya bölge ile. Alt ad ayrılmış bir tire (-), bir kültür adı izler. Örnek, Japonya'da en-US olarak Amerika Birleşik Devletleri, Avusturya konuşulan gibi Almanca için Almanya veya de AT konuşulan gibi Almanca için de-DE, konuşulan İngilizce konuşulan olarak Japonca için ja-JP verilebilir. Bkz: [Ulusal dil desteği (NLS) API Başvurusu](https://go.microsoft.com/fwlink/?LinkId=200048) Go Global Geliştirme Merkezi kültür adları tam listesi için.

> [!NOTE]
> Kaynak dosyaları oluşturma hakkında daha fazla bilgi için bkz: [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) ve [uydu derlemeleri oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).

<a name="cpconpackagingdeployingresourcesanchor1"></a>

## <a name="the-resource-fallback-process"></a>Kaynak Geri Dönüş İşlemi

Paketleme ve dağıtma kaynakları için merkez ve ışınsal modelini, uygun kaynakları bulmak için bir geri dönüş işlemi kullanır. Bir uygulama, mevcut olmayan bir yerelleştirilmiş kaynak isterse, kullanıcının uygulama en yakından eşleşen uygun bir geri dönüş kaynak bilgisayarın istemek ve bir özel durum oluşturur ortak dil çalışma zamanı kültürler hiyerarşisini arar olarak yalnızca bir Son çare. Uygun bir kaynak bulunamıyorsa hiyerarşinin her düzeyinde çalışma zamanı otomatik olarak bunu kullanır. Kaynak bulunamazsa, arama, İleri düzeyde devam eder.

Arama performansını artırmak için uygulama <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliği ana derlemenizi ve ana bütünleştirilmiş kod ile çalışacak dilden adını geçirin.

### <a name="net-framework-resource-fallback-process"></a>.NET framework kaynak geri dönüş işlemi

.NET Framework kaynak geri dönüş işlemi aşağıdaki adımları içerir:

> [!TIP]
> Kullanılacak çözebileceğiniz [ \<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) kaynak geri dönüş işlemi ve işlemin çalışma zamanı araştırmaları için kaynak derlemeleri en iyi duruma getirmek için yapılandırma öğesi. Daha fazla bilgi için [kaynak geri dönüş işlemini en iyi duruma getirme](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) bölümü.

1. Çalışma zamanı ilk denetimleri [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md) uygulamanız için istenen kültürüyle eşleşen bir derleme için.

     Birçok uygulama tarafından paylaşılan kaynak derlemeleri genel derleme önbelleğine depolayabilirsiniz. Bu, her uygulamada dizin yapısını kaynakların belirli kümeleri eklemek zorunda kalmaktan kurtarır. Çalışma zamanı derlemeye bir başvuruda bulunursa, derleme istenen kaynak için arama yapar. Bu derlemede giriş bulunursa, istenen kaynak kullanır. Giriş bulamazsa arama devam eder.

2. Çalışma zamanı şu anda yürütülen derleme için istenen kültürüyle eşleşen bir alt dizinin sonraki denetler. Bu alt bulunursa, o alt istenen kültürü için geçerli bir uydu derlemesine arar. Çalışma zamanı, ardından istenen kaynak için uydu derleme arar. Derlemede kaynak bulursa, onu kullanır. Kaynak bulamazsa arama devam eder.

3. Çalışma zamanı uydu derlemeye isteğe bağlı olarak yüklü olup olmadığını belirlemek için Windows Yükleyici sonraki sorgular. Bu nedenle, yüklemesini ele alır, derlemeyi yükler ve, veya istenen kaynak arar. Derlemede kaynak bulursa, onu kullanır. Kaynak bulamazsa arama devam eder.

4. Çalışma zamanı oluşturur <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> uydu derlemesini bulamıyor olduğunu belirtmek için olay. Olayı işlemek seçerseniz, olay işleyicisi kaynaklarını arama için kullanılacak olan uydu derlemeye bir başvuruda döndürebilir. Aksi takdirde, olay işleyicisini döndürür `null` ve aramaya devam eder.

5. Çalışma zamanı sonraki aramaları genel derleme önbelleği yeniden, bu süre için istenen üst derlemenin kültür. Ana derleme genel derleme önbelleğinde varsa, çalışma zamanı derleme istenen kaynak için arama yapar.

     Üst kültüre uygun geri dönüş kültürü tanımlanır. Geri dönüş aday olarak üst öğeleri sağlayan herhangi bir kaynağa bir özel durum için tercih edilir çünkü göz önünde bulundurun. Bu işlem kaynakları yeniden sağlar. İstenen kaynak yerelleştirmek alt kültürü yalnızca gerektirmez üst düzeyde belirli bir kaynağa içermelidir. Örneğin, uydu derlemeler için sağlarsanız `en` (nötr İngilizce) `en-GB` (Birleşik Krallık'ta konuşulan olarak İngilizce), ve `en-US` (Amerika Birleşik Devletleri'nde konuşulan olarak İngilizce), `en` uydu ortak içerebilir terminolojisinde ve `en-GB` ve `en-US` Uyduları farklı koşullar için geçersiz kılmalar sağlayabilirdi.

6. Çalışma zamanı, bir üst dizin içerip içermediğini görmek için şu anda çalıştırılan derlemenin dizinin sonraki denetler. Bir üst dizin varsa, çalışma zamanı üst kültürü için geçerli bir uydu derlemesine dizinde arar. Derleme bulursa, çalışma zamanı derleme istenen kaynak için arama yapar. Kaynak bulursa, onu kullanır. Kaynak bulamazsa arama devam eder.

7. Çalışma zamanı üst uydu derlemeye isteğe bağlı olarak yüklü olup olmadığını belirlemek için Windows Yükleyici sonraki sorgular. Bu nedenle, yüklemesini ele alır, derlemeyi yükler ve, veya istenen kaynak arar. Derlemede kaynak bulursa, onu kullanır. Kaynak bulamazsa arama devam eder.

8. Çalışma zamanı oluşturur <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> uygun bir geri dönüş kaynağı bulamadı olduğunu belirtmek için olay. Olayı işlemek seçerseniz, olay işleyicisi kaynaklarını arama için kullanılacak olan uydu derlemeye bir başvuruda döndürebilir. Aksi takdirde, olay işleyicisini döndürür `null` ve aramaya devam eder.

9. Çalışma zamanı sonraki arar önceki üç adımı birçok olası düzeyleri ile olduğu gibi derlemelerini üst. Her bir kültür tarafından tanımlanan yalnızca bir üste sahip <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> özelliği, ancak üst öğesi kendi üst sahip olabilir. Üst arama kültürler durakları bir kültür ayarlandığında <xref:System.Globalization.CultureInfo.Parent%2A> özelliği döndürür <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>; temel, sabit kültür olarak kabul edilmez üst kültür veya kaynaklarınız olamayacağı bir kültür kaynak.

10. Başlangıçta belirtilen kültürü ve tüm üst öğeleri aranır ve kaynak tarafından hala bulunamazsa, kaynak varsayılan (Temel) kültürü için kullanılır. Genellikle, kaynaklar için varsayılan kültürü ana uygulama derlemesinde dahil edilir. Değerini belirtmek ancak <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> için <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> özelliği <xref:System.Resources.NeutralResourcesLanguageAttribute> kaynaklar için ultimate geri dönüş konumu ana derleme yerine, bir uydu derlemesine olduğunu belirtmek için özniteliği.

    > [!NOTE]
    > Varsayılan kaynak ana derleme ile derlenmiş yalnızca bir kaynaktır. Kullanarak bir uydu derlemesine belirtmediğiniz sürece <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliği, ultimate geri dönüş (son üst öğe) olan. Bu nedenle, varsayılan bir kaynak kümesini her zaman, ana derlemeye dahil öneririz. Bu durum, oluşturulan öğesinden özel durumlar önlemeye yardımcı olur. Duyarlıymış belirli olsa bile varsayılan kaynak dahil olmak üzere, tüm kaynaklar için bir geri dönüş sunulabilmesi ve bu en az bir kaynak dosyası her zaman kullanıcı için mevcuttur.

11. Son olarak, çalışma zamanı varsayılan (Temel) kültürü için bir kaynak bulmazsa bir <xref:System.Resources.MissingManifestResourceException> veya <xref:System.Resources.MissingSatelliteAssemblyException> kaynak bulunamadı belirtmek için özel durum oluştu.

Örneğin, İspanyolca (Meksika) için yerelleştirilmiş bir kaynağı uygulama isteklerini varsayalım ( `es-MX` kültür). Çalışma zamanı, Genel Derleme Önbelleği ilk eşleşen derleme için arama yapar. `es-MX`, ancak bunun yerine bulmuyorsa. Çalışma zamanı için o anda yürütülen derlemenin dizini ardından araması bir `es-MX` dizin. Bu başarısız olursa, çalışma zamanı genel derleme önbelleği yeniden uygun geri dönüş kültürü yansıtan bir üst derleme için arama yapar; bu durumda, `es` (İspanyolca). Ana derleme bulunamazsa, çalışma zamanı üst derlemeler için tüm olası düzeylerini arar `es-MX` karşılık gelen kaynak bulana kadar kültür. Bir kaynak bulunmazsa, çalışma zamanı kaynağı için varsayılan kültürü kullanır.

<a name="Optimizing"></a>

#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>.NET Framework kaynak geri dönüş işlemi en iyi duruma getirme

Aşağıdaki koşullarda, çalışma zamanı kaynakları uydu derlemelerinde arar işlem iyileştirebilirsiniz.

- Uydu derlemeleri, kod derleme ile aynı konumda dağıtılır. Kod derleme yüklüyse [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md), uydu derlemeleri genel derleme önbelleğinde da yüklenir. Bir kod derlemesi bir dizinde yüklü değilse, uydu derlemelerinin bu dizinin kültüre özgü klasörlere yüklenir.

- Uydu derlemeleri isteğe bağlı olarak yüklü değildir.

- Uygulama kodu işlemiyor <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.

Araştırma için uydu derlemeleri dahil ederek en iyi duruma [ \<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) öğesi ve ayarı kendi `enabled` özniteliğini `true` gösterildiği gibi uygulama yapılandırma dosyası Aşağıdaki örnekte.

```xml
<configuration>
   <runtime>
      <relativeBindForResources enabled="true" />
   </runtime>
</configuration>
```

Uydu derlemeler için en iyi duruma getirilmiş araştırma, bir katılım özelliğidir. Diğer bir deyişle, çalışma zamanı konusunda belgelenen adımları izler [kaynak geri dönüş işlemi](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) sürece [ \<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) öğedir uygulamanın yapılandırmada mevcut Dosya ve kendi `enabled` özniteliği `true`. Bu durumda, bir uydu derlemesi için yoklama işlemi şu şekilde değiştirilir:

- Çalışma zamanı uydu derlemesi için araştırma için üst kod derleme konumunu kullanır. Ana derleme genel derleme önbelleğinde yüklü değilse, çalışma zamanı önbelleğinde ancak uygulamanın dizinine araştırmaları. Ana derlemenin bir uygulama dizininde yüklü değilse, çalışma zamanı uygulama dizininde, ancak genel derleme önbelleğinde araştırmaları.

- Çalışma zamanı uydu derlemelerinin isteğe bağlı yükleme için Windows Installer sorgu değil.

- Belirli kaynak derlemesi için yoklama başarısız olursa, çalışma zamanı yükseltmez <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.

### <a name="net-core-resource-fallback-process"></a>.NET core kaynak geri dönüş işlemi

.NET Core kaynak geri dönüş işlemi aşağıdaki adımları içerir:

1. Çalışma zamanı, istenen kültürü için bir uydu derlemesini yüklemeyi dener.
     * Şu anda yürütülen derleme için istenen kültürüyle eşleşen bir alt dizinden denetler. Bu alt bulunursa, o alt istenen kültürü için geçerli bir uydu derlemesine arar ve yükler.

       > [!NOTE]
       > Büyük küçük harfe duyarlı dosya sistemleri (diğer bir deyişle, Linux ve macOS) ile işletim sistemlerinde, kültür adı alt arama büyük/küçük harf duyarlıdır. Alt ad durumunu tam olarak eşleşmelidir <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (örneğin, `es` veya `es-MX`).

       > [!NOTE]
       > Programcı bir özel bütünleştirilmiş kod yükleme bağlamından türetilen değilse <xref:System.Runtime.Loader.AssemblyLoadContext>, karmaşık bir durumdur. Yürütülen derleme özel bağlamına yüklendi, çalışma zamanı uydu derlemesini özel bağlamına yükler. Bu belgenin kapsamı dışındadır ayrıntılar bulunur. Bkz: <xref:System.Runtime.Loader.AssemblyLoadContext>.

     * Uydu birleştirin, bulunmadı, <xref:System.Runtime.Loader.AssemblyLoadContext> başlatır <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> uydu derlemesini bulamıyor olduğunu belirtmek için olay. Olayı işlemek seçerseniz, olay işleyicisi yükleyin ve uydu derlemeye bir başvuru döndürür.
     * Bir uydu derlemesine hala bulunamadı, AssemblyLoadContext tetiklemek AppDomain neden olan bir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> uydu derlemesini bulamıyor olduğunu belirtmek için olay. Olayı işlemek seçerseniz, olay işleyicisi yükleyin ve uydu derlemeye bir başvuru döndürür.

2. Çalışma zamanı uydu derlemesi bulunursa, istenen kaynak için arar. Derlemede kaynak bulursa, onu kullanır. Kaynak bulamazsa arama devam eder.

     > [!NOTE]
     > Kaynak uydu bütünleştirilmiş kod içinde bulmak için çalışma zamanı tarafından istenen kaynak dosyası için arar <xref:System.Resources.ResourceManager> geçerli <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>. Kaynak dosya içinde istenen kaynak adını arar. Ya da bulunmazsa, kaynak değerlendirilir olarak bulunamadı.

3. Çalışma zamanı üst kültür derlemeler birçok olası düzeyleri, her zaman 1 ve 2 adımları yinelemekten sonraki arar.

     Üst kültüre uygun bir geri dönüş kültürü tanımlanır. Geri dönüş aday olarak üst öğeleri sağlayan herhangi bir kaynağa bir özel durum için tercih edilir çünkü göz önünde bulundurun. Bu işlem kaynakları yeniden sağlar. İstenen kaynak yerelleştirmek alt kültürü yalnızca gerektirmez üst düzeyde belirli bir kaynağa içermelidir. Örneğin, uydu derlemeler için sağlarsanız `en` (nötr İngilizce), `en-GB` (Birleşik Krallık'ta konuşulan olarak İngilizce), ve `en-US` (Amerika Birleşik Devletleri'nde konuşulan olarak İngilizce), `en` uydu ortak içerir terminolojisinde ve `en-GB` ve `en-US` Uyduları farklı koşullar için geçersiz kılmalar sağlar.

     Her bir kültür tarafından tanımlanan yalnızca bir üste sahip <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> özelliği, ancak üst öğesi kendi üst sahip olabilir. Üst arama kültürler durakları bir kültür ayarlandığında <xref:System.Globalization.CultureInfo.Parent%2A> özelliği döndürür <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Geri dönüş kaynağı için bir üst kültür veya kaynaklarınız olamayacağı bir kültür sabit kültür dikkate alınmaz.

4. Başlangıçta belirtilen kültürü ve tüm üst öğeleri aranır ve kaynak tarafından hala bulunamazsa, kaynak varsayılan (Temel) kültürü için kullanılır. Genellikle, kaynaklar için varsayılan kültürü ana uygulama derlemesinde dahil edilir. Değerini belirtmek ancak <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> için <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> kaynaklar için ultimate geri dönüş konumu ana derleme yerine bir uydu derlemesine olduğunu belirtmek için özellik.

    > [!NOTE]
    > Varsayılan kaynak ana derleme ile derlenmiş yalnızca bir kaynaktır. Kullanarak bir uydu derlemesine belirtmediğiniz sürece <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliği, ultimate geri dönüş (son üst öğe) olan. Bu nedenle, varsayılan bir kaynak kümesini her zaman, ana derlemeye dahil öneririz. Bu durum, oluşturulan öğesinden özel durumlar önlemeye yardımcı olur. Varsayılan kaynak dosyası dahil, bir geri dönüş için tüm kaynakları sağlamak ve duyarlıymış belirli olsa bile en az bir kaynağı her zaman kullanıcı için mevcut olduğundan emin olun.

5. Son olarak, çalışma zamanı (Temel) varsayılan kültür için bir kaynak dosyası bulamazsa bir <xref:System.Resources.MissingManifestResourceException> veya <xref:System.Resources.MissingSatelliteAssemblyException> kaynak bulunamadı belirtmek için özel durum oluştu. Kaynak dosya bulundu, ancak istenen kaynak mevcut değil. istek döndürür `null`.

### <a name="ultimate-fallback-to-satellite-assembly"></a>Uydu Derlemesi için Ultimate Geri Dönüş

İsteğe bağlı olarak, ana derlemesinden kaynakları kaldırmak ve çalışma zamanı ultimate geri dönüş kaynakları belirli bir kültüre karşılık gelen bir uydu derlemesinden yükleyeceğini belirtin. Geri dönüş işlemini denetlemek için kullandığınız <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> oluşturucusu ve için bir değer <xref:System.Resources.UltimateResourceFallbackLocation> parametresi ana derleme veya bir uydu derlemesine Resource Manager geri dönüş kaynakları ayıklamak olup olmadığını belirtir.

Aşağıdaki .NET Framework örnekte <xref:System.Resources.NeutralResourcesLanguageAttribute> Fransızca için bir uydu derlemeye bir uygulamanın geri dönüş kaynakları depolamak için öznitelik (`fr`) dili. Örnek adlı bir tek dize kaynağını tanımlayan iki metin tabanlı kaynak dosyalarına sahip `Greeting`. İlk olarak resources.fr.txt, Fransızca Dil kaynağı içeriyor.

```
Greeting=Bon jour!
```

İkincisi, resources,ru.txt, Rusça Dil kaynağı içeriyor.

```
Greeting=Добрый день
```

Bu iki dosyayı çalıştırarak .resources dosyalarına derlenir [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) komut satırından. Fransızca Dil kaynağı için komut şöyledir:

**resgen.exe resources.fr.txt**

Rusça Dil kaynağı için komut şöyledir:

**resgen.exe resources.ru.txt**

Çalıştırarak dinamik bağlantı kitaplıkları içinde gömülü .resources dosyaları [derleme Bağlayıcısı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) komuttan satır için Fransızca Dil kaynağı şu şekilde:

**al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**

ve aşağıdaki gibi Rusça Dil kaynağı için:

**al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**

Uygulama kaynak kodunu Example1.cs veya Example1.vb adındaki bir dosyada yer alıyor. İçerdiği <xref:System.Resources.NeutralResourcesLanguageAttribute> varsayılan uygulama kaynağı fr alt dizinde olduğunu belirtmek için özniteliği. Kaynak Yöneticisi'ni başlatır, değerini alır `Greeting` kaynak ve konsolda görüntüler.

[!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
[!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]

Ardından, C# kaynak kodunu komut satırından şu şekilde derleyebilirsiniz:

```console
csc Example1.cs
```

Visual Basic Derleyicisi için komutu çok benzer:

```console
vbc Example1.vb
```

Ana derlemede gömülü kaynak olduğundan, kullanarak derleme gerekmez `/resource` geçin.

Örnek dilinden Rusça dışındaki herhangi bir sistemde çalıştırdığınızda, aşağıdaki çıkışı görüntüler:

```
Bon jour!
```

## <a name="suggested-packaging-alternative"></a>Önerilen Paketleme Alternatifi

Zaman ve bütçe kısıtlamaları bir kaynak için uygulamanızın desteklediği her bir alt kümesini oluşturmasını engelleyebilir. Bunun yerine, tüm subcultures ilgili bir üst kültür kullanabilir, tek bir uydu derlemesi oluşturabilirsiniz. Örneğin, bölgeye özgü İngilizce kaynakları isteği kullanıcılar tarafından alınan tek bir İngilizce uydu derlemesi (TR) ve bölgeye özgü Almanca kaynakları isteyen kullanıcılar için tek Almanca uydu derlemesi (de) sağlayabilirsiniz. Örneğin, Almanca için (de-DE), Almanya'da konuşulan gibi Avusturya (de-AT) ve İsviçre (de-CH) Alman uydu derlemeye (de) dönmesi ister. Varsayılan kaynakları son geri dönüş olan ve bu nedenle, uygulamanızın kullanıcılarının çoğunluğu tarafından istenen kaynakları olmalıdır böylece bu kaynaklara dikkatle seçin. Bu yaklaşım, daha az duyarlıymış özgüdür, ancak uygulamanızın yerelleştirme maliyetlerini önemli ölçüde azaltabilirsiniz kaynakları dağıtır.

## <a name="see-also"></a>Ayrıca bkz.

- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)
- [Kaynak Dosyaları Oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Uydu Derlemeleri Oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)

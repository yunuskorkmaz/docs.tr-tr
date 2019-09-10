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
ms.openlocfilehash: 808f0f8ac6caf15be0bf1ba8735521871c9b94d7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851604"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>.NET uygulamalarında kaynakları paketleme ve dağıtma

Uygulamalar, yerelleştirilmiş kaynakları almak için <xref:System.Resources.ResourceManager> sınıfı tarafından temsil edilen .NET Framework kaynak yöneticisi güvenir. Kaynak Yöneticisi, bir hub ve bağlı bileşen modelinin kaynakları paketleyip dağıtmak için kullanıldığını varsayar. Hub, yerelleştirilemeyen yürütülebilir kodu ve bağımsız veya varsayılan kültür olarak adlandırılan tek bir kültürün kaynaklarını içeren ana derlemedir. Varsayılan kültür, uygulamanın geri dönüş kültürüdür; Bu, yerelleştirilmiş kaynaklar bulunamazsa kaynakları kullanılan kültürdür. Her bir bağlı bileşen tek bir kültürün kaynaklarını içeren bir uydu derlemesine bağlanır, ancak herhangi bir kod içermez.

Bu modelin çeşitli avantajları vardır:

- Bir uygulamayı dağıttıktan sonra, yeni kültürler için artımlı olarak kaynak ekleyebilirsiniz. Kültüre özgü kaynakların sonraki geliştirmesi önemli miktarda zaman gerektirebileceğinden, bu, önce ana uygulamanızı serbest bırakmanıza ve daha sonra kültüre özgü kaynaklar sunmanıza olanak tanır.

- Uygulamanın uydu derlemelerini uygulamayı yeniden derlemeden güncelleştirebilir ve değiştirebilirsiniz.

- Uygulamanın yalnızca belirli bir kültür için gereken kaynakları içeren uydu derlemelerini yüklemesi gerekir. Bu, sistem kaynaklarının kullanımını önemli ölçüde azaltabilir.

 Ancak, bu modelin olumsuz yönleri de vardır:

- Birden çok kaynak kümesini yönetmeniz gerekir.

- Birkaç yapılandırmayı test etmeniz gerektiğinden, bir uygulamanın test edilmesine yönelik başlangıç maliyeti artar. Uzun vadede, birden çok uydu ile bir çekirdek uygulamanın test etmek ve birkaç paralel uluslararası sürümü test etmek için daha kolay ve daha düşük maliyetli olacağını unutmayın.

## <a name="resource-naming-conventions"></a>Kaynak Adlandırma Kuralları

Uygulamanızın kaynaklarını paketlemeyi seçtiğinizde, ortak dil çalışma zamanının beklediği kaynak adlandırma kurallarını kullanarak bunları adlandırmalısınız. Çalışma zamanı bir kaynağı kültür adına göre tanımlar. Her kültüre, genellikle bir dille ilişkili iki harfli, küçük harfli bir kültür adının birleşimi ve gerekirse, bir ülke veya bölgeyle ilişkili iki harfli, büyük harfli bir alt kültür adı olan benzersiz bir ad verilir. Alt kültür adı, bir tire (-) ile ayrılmış olarak kültür adını izler. Japonca, Japonya 'da konuşulan Japonca için ja-JP, Birleşik Devletler Ingilizce için en-US, Almanya 'da konuşulan olarak Almanca için de, Almanya için de ve [Windows tarafından desteklenen dil/bölge adları listesindeki](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) **Dil etiketi** sütununa bakın. Kültür adları [BCP 47](https://tools.ietf.org/html/bcp47)tarafından tanımlanan standardı izler.

> [!NOTE]
> Kaynak dosyaları oluşturma hakkında daha fazla bilgi için bkz. [kaynak dosyaları oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) ve [uydu derlemeleri oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).

<a name="cpconpackagingdeployingresourcesanchor1"></a>

## <a name="the-resource-fallback-process"></a>Kaynak Geri Dönüş İşlemi

Paketleme ve dağıtım kaynakları için merkez ve bağlı bileşen modeli, uygun kaynakları bulmak için bir geri dönüş işlemi kullanır. Bir uygulama kullanılamayan bir yerelleştirilmiş kaynak isterse, ortak dil çalışma zamanı, kullanıcının applicationın isteğiyle en yakından eşleşen uygun bir geri dönüş kaynağı için kültürlerin hiyerarşisini arar ve yalnızca bir özel durum oluşturur Son çare. Hiyerarşinin her düzeyinde, uygun bir kaynak bulunursa çalışma zamanı onu kullanır. Kaynak bulunamazsa, arama bir sonraki düzeyde devam eder.

Arama performansını geliştirmek için, <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliği ana derlemenizin içine uygulayın ve ana derlemeinizle birlikte çalışacak bağımsız dilin adını geçirin.

### <a name="net-framework-resource-fallback-process"></a>Kaynak geri dönüş işlemini .NET Framework

.NET Framework kaynak geri dönüş işlemi aşağıdaki adımları içerir:

> [!TIP]
> Kaynak geri dönüş işlemini ve kaynak derlemeler için çalışma zamanı araştırmalarını iyileştirmek için [ \<relativebindforresources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) yapılandırma öğesini kullanabilirsiniz. Daha fazla bilgi için [kaynak geri dönüş Işlemini En Iyi duruma getirme](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) bölümüne bakın.

1. Çalışma zamanı, uygulamanız için istenen kültür ile eşleşen bir derleme için [genel derleme önbelleğini](../../../docs/framework/app-domains/gac.md) denetler.

     Genel derleme önbelleği, birçok uygulama tarafından paylaşılan kaynak derlemelerini depolayabilirler. Bu, oluşturduğunuz her uygulamanın dizin yapısına belirli kaynak kümelerini dahil etmek zorunda kalmaktan kurtarır. Çalışma zamanı derlemeye bir başvuru bulursa, istenen kaynak için derlemeyi arar. Girdiyi derlemede bulursa, istenen kaynağı kullanır. Girişi bulamazsa, aramaya devam eder.

2. Sonraki çalışma zamanı, istenen kültür ile eşleşen bir alt dizin için şu anda yürütülmekte olan derlemenin dizinini denetler. Alt dizini bulursa, istenen kültür için geçerli bir uydu derlemesi için bu alt dizini arar. Çalışma zamanı daha sonra, istenen kaynak için uydu derlemesinde arama yapar. Kaynağı derlemede bulursa, onu kullanır. Kaynak bulamazsa, aramaya devam eder.

3. Sonraki çalışma zamanı, uydu derlemesinin isteğe bağlı olarak yüklenip yüklenmeyeceğini öğrenmek için Windows Installer sorgular. Bu durumda, yüklemeyi işler, derlemeyi yükler ve veya istenen kaynağı arar. Kaynağı derlemede bulursa, onu kullanır. Kaynak bulamazsa, aramaya devam eder.

4. Çalışma zamanı <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı, uydu derlemesini bulamadığını belirtecek şekilde oluşturur. Olayı derlemeyi seçerseniz, olay işleyiciniz, kaynakları arama için kullanılacak olan uydu derlemesine bir başvuru döndürebilir. Aksi takdirde, olay işleyicisi döndürülür `null` ve arama devam eder.

5. Sonraki çalışma zamanı, genel derleme önbelleğinde bu kez, istenen kültür için üst derleme için yeniden arama yapar. Üst derleme genel derleme önbelleğinde varsa, çalışma zamanı, istenen kaynak için derlemeyi arar.

     Üst kültür uygun geri dönüş kültürü olarak tanımlanır. Herhangi bir kaynağın sağlanması bir özel durum oluşturmak tercih ettiğinden, üst öğeleri geri dönüş adayları olarak değerlendirin. Bu işlem, kaynakları yeniden kullanmanıza da olanak tanır. Yalnızca alt kültürün istenen kaynağı yerelleştirilmesi gerekmiyorsa, üst düzeyde belirli bir kaynağı dahil etmelisiniz. Örneğin, ( `en` bağımsız İngilizce) için uydu derlemeleri, `en-GB` (Birleşik Krallık 'ta konuşulan İngilizce) ve `en-US` (Birleşik Devletler `en` İngilizcede İngilizce) sağlarsanız, uydu ortak terminoloji ve `en-GB` ve `en-US` uydular, yalnızca farklı şartlar için geçersiz kılmalar sağlayabilir.

6. Sonraki çalışma zamanı, ana dizin içerip içermediğini görmek için şu anda yürütülmekte olan derlemenin dizinini denetler. Bir üst dizin varsa, çalışma zamanı, üst kültürün geçerli bir uydu derlemesi için dizini arar. Derlemeyi bulursa, çalışma zamanı, istenen kaynak için derlemeyi arar. Kaynağı bulursa onu kullanır. Kaynak bulamazsa, aramaya devam eder.

7. Sonraki çalışma zamanı, üst uydu derlemesinin isteğe bağlı olarak yüklenip yüklenmeyeceğini öğrenmek için Windows Installer sorgular. Bu durumda, yüklemeyi işler, derlemeyi yükler ve veya istenen kaynağı arar. Kaynağı derlemede bulursa, onu kullanır. Kaynak bulamazsa, aramaya devam eder.

8. Çalışma zamanı <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı, uygun bir geri dönüş kaynağı bulamadığını belirtecek şekilde oluşturur. Olayı derlemeyi seçerseniz, olay işleyiciniz, kaynakları arama için kullanılacak olan uydu derlemesine bir başvuru döndürebilir. Aksi takdirde, olay işleyicisi döndürülür `null` ve arama devam eder.

9. Daha sonra çalışma zamanı, önceki üç adımda olduğu gibi, üst derlemeleri birçok olası düzey aracılığıyla arar. Her kültürün, <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan yalnızca bir üst öğesi vardır ancak bir üst öğenin kendi üst öğesi olabilir. Bir kültürün <xref:System.Globalization.CultureInfo.Parent%2A> <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>özelliği döndürüldüğünde üst kültürler için arama işlemi duraklar; kaynak geri dönüşü için, sabit kültür bir üst kültür veya kaynaklara sahip olan bir kültür olarak kabul edilmez.

10. İlk olarak belirtilen kültür ve tüm ebeveynler arandıysa ve kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürün kaynağı kullanılır. Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesine dahil edilmiştir. Ancak, kaynaklar için en son geri dönüş <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> konumunun ana <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> derleme yerine bir <xref:System.Resources.NeutralResourcesLanguageAttribute> uydu derlemesi olduğunu göstermek için özniteliğinin özelliği için bir değer belirtebilirsiniz.

    > [!NOTE]
    > Varsayılan kaynak, ana derlemeyle derlenebilecek tek kaynaktır. <xref:System.Resources.NeutralResourcesLanguageAttribute> Özniteliğini kullanarak bir uydu derlemesi belirtmediğiniz müddetçe, bu, en son geri dönüş (son üst öğe) öğesidir. Bu nedenle, ana derlemenizin her zaman varsayılan bir kaynak kümesi içermesini öneririz. Bu, özel durumların oluşmasını önlemeye yardımcı olur. Varsayılan bir kaynak dahil ederek, tüm kaynaklar için bir geri dönüş sağlarsınız ve çok önemli olmasa bile Kullanıcı için en az bir kaynağın her zaman mevcut olduğundan emin olabilirsiniz.

11. Son olarak, çalışma zamanı varsayılan (geri dönüş) kültürü için bir kaynak bulamazsa, kaynağın bulunamadığını <xref:System.Resources.MissingManifestResourceException> göstermek <xref:System.Resources.MissingSatelliteAssemblyException> için bir veya özel durum oluşturulur.

Örneğin, uygulamanın İspanyolca (Meksika) için yerelleştirilmiş bir kaynak istediğini varsayalım ( `es-MX` kültür). Çalışma zamanı önce, eşleşen `es-MX`derleme için genel derleme önbelleğinde arama yapmaz, ancak bulamaz. Çalışma zamanı daha sonra bir `es-MX` dizin için yürütülmekte olan derlemenin dizinini arar. Çalışma zamanı, genel derleme önbelleğini, uygun geri dönüş kültürünü yansıtan bir üst derleme için yeniden arar — bu durumda `es` (İspanyolca). Üst derleme bulunamazsa, çalışma zamanı karşılık gelen bir kaynağı bulana kadar `es-MX` kültür için tüm olası üst derleme düzeylerini arar. Bir kaynak bulunamazsa, çalışma zamanı varsayılan kültür için kaynağı kullanır.

<a name="Optimizing"></a>

#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>.NET Framework kaynak geri dönüş Işlemini iyileştirme

Aşağıdaki koşullarda, çalışma zamanının uydu derlemelerindeki kaynakları arayacağı süreci iyileştirebilirsiniz

- Uydu derlemeleri kod derlemesiyle aynı konumda dağıtılır. Kod derlemesi [genel derleme önbelleğinde](../../../docs/framework/app-domains/gac.md)yüklüyse, uydu derlemeleri genel bütünleştirilmiş kod önbelleğine de yüklenir. Kod derlemesi bir dizinde yüklüyse, uydu derlemeleri bu dizinin kültüre özgü klasörlerine yüklenir.

- Uydu derlemeleri isteğe bağlı olarak yüklenmez.

- Uygulama kodu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı işlemez.

`enabled` [ \<Relativebindforresources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) öğesini ekleyerek ve özniteliğini `true` aşağıdaki gibi uygulama yapılandırma dosyasında olarak ayarlayarak uydu derlemeleri için araştırmayı iyileştirebilirsiniz örneğinde.

```xml
<configuration>
   <runtime>
      <relativeBindForResources enabled="true" />
   </runtime>
</configuration>
```

Uydu derlemeleri için iyileştirilmiş araştırma bir katılım özelliğidir. Diğer bir deyişle, çalışma zamanı, `enabled` uygulama yapılandırma dosyasında [ \<relativebindforresources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) öğesi mevcut olmadığı ve özniteliği ayarlanmış olmadığı sürece [kaynak geri dönüş işleminde](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) belgelenen adımları izler. `true`. Bu durumda, bir uydu derlemesini araştırma işlemi aşağıdaki gibi değiştirilmiştir:

- Çalışma zamanı, uydu derlemesi için araştırma yapmak üzere ana kod derlemesinin konumunu kullanır. Üst derleme genel derleme önbelleğinde yüklüyse, çalışma zamanı önbellekte araştırıyor ancak uygulamanın dizininde değil. Üst derleme bir uygulama dizinine yüklenirse, çalışma zamanı uygulama dizininde araştırıyor ancak genel derleme önbelleğinde değil.

- Çalışma zamanı, uydu derlemelerinin isteğe bağlı yüklemesi için Windows Installer sorgulayamaz.

- Belirli bir kaynak derlemesinin araştırması başarısız olursa, çalışma zamanı <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı oluşturmaz.

### <a name="net-core-resource-fallback-process"></a>.NET Core kaynak geri dönüş işlemi

.NET Core kaynak geri dönüş işlemi aşağıdaki adımları içerir:

1. Çalışma zamanı, istenen kültür için bir uydu derlemesini yüklemeye çalışır.
     - İstenen kültür ile eşleşen bir alt dizin için şu anda yürütülmekte olan derlemenin dizinini denetler. Alt dizini bulursa, bu alt dizini istenen kültür için geçerli bir uydu derlemesi için arar ve yükler.

       > [!NOTE]
       > Büyük/küçük harfe duyarlı dosya sistemlerine (Linux ve macOS) sahip işletim sistemlerinde, kültür adı alt dizin araması büyük/küçük harfe duyarlıdır. Alt dizin adı, <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (örneğin, `es` veya `es-MX`) durumuyla tam olarak eşleşmelidir.

       > [!NOTE]
       > Programcı, ' den <xref:System.Runtime.Loader.AssemblyLoadContext>özel bir derleme yük bağlamını türediyse, durum karmaşıktır. Yürütülen derleme özel içeriğe yüklenmişse, çalışma zamanı uydu derlemesini özel bağlama yükler. Bu belge için Ayrıntılar kapsam dışında. Bkz <xref:System.Runtime.Loader.AssemblyLoadContext>.

     - Bir uydu montajı bulunmazsa <xref:System.Runtime.Loader.AssemblyLoadContext> , bu <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> olayı uydu derlemesini bulamadığını belirtecek şekilde oluşturur. Olayı tanıtıcıyı seçerseniz, olay işleyiciniz uydu derlemesine bir başvuru yükleyebilir ve döndürebilir.
     - Bir uydu derlemesi yine de bulunmazsa assemblyloadcontext, uygulama etki alanının uydu derlemesini bulamadığını göstermek için bir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay tetiklemesine neden olur. Olayı tanıtıcıyı seçerseniz, olay işleyiciniz uydu derlemesine bir başvuru yükleyebilir ve döndürebilir.

2. Bir uydu derlemesi bulunursa, çalışma zamanı istenen kaynak için bunu arar. Kaynağı derlemede bulursa, onu kullanır. Kaynak bulamazsa, aramaya devam eder.

     > [!NOTE]
     > Uydu derlemesi içindeki bir kaynağı bulmak için, çalışma zamanı, <xref:System.Resources.ResourceManager> <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>için tarafından istenen kaynak dosyasını arar. Kaynak dosyasında, istenen kaynak adını arar. Herhangi biri bulunmazsa, kaynak bulunamadı olarak kabul edilir.

3. Sonraki çalışma zamanı, her zaman 1 & 2. adımları her tekrarlanışında, üst kültür derlemelerini çok potansiyel düzeyler aracılığıyla arar.

     Üst kültür uygun bir geri dönüş kültürü olarak tanımlanır. Herhangi bir kaynağın sağlanması bir özel durum oluşturmak tercih ettiğinden, üst öğeleri geri dönüş adayları olarak değerlendirin. Bu işlem, kaynakları yeniden kullanmanıza da olanak tanır. Yalnızca alt kültürün istenen kaynağı yerelleştirilmesi gerekmiyorsa, üst düzeyde belirli bir kaynağı dahil etmelisiniz. Örneğin, ( `en` bağımsız İngilizce) için uydu derlemeleri, `en-GB` (Birleşik Krallık 'ta konuşulan İngilizce) ve (Birleşik Devletler İngilizce) `en` ile `en-US` , uydu ortak terminoloji ve `en-GB` ve `en-US` uydular, yalnızca farklı şartlar için geçersiz kılmalar sağlar.

     Her kültürün, <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan yalnızca bir üst öğesi vardır ancak bir üst öğenin kendi üst öğesi olabilir. Bir kültürün <xref:System.Globalization.CultureInfo.Parent%2A> <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>özelliği döndürüldüğünde üst kültürleri için arama durduruluyor. Kaynak geri dönüşü için, sabit kültür bir üst kültür veya kaynaklara sahip bir kültür olarak kabul edilmez.

4. İlk olarak belirtilen kültür ve tüm ebeveynler arandıysa ve kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürün kaynağı kullanılır. Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesine dahil edilmiştir. Ancak, kaynaklar için en son geri dönüş <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> konumunun ana <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> derleme yerine bir uydu derlemesi olduğunu göstermek için özelliği için bir değer belirtebilirsiniz.

    > [!NOTE]
    > Varsayılan kaynak, ana derlemeyle derlenebilecek tek kaynaktır. <xref:System.Resources.NeutralResourcesLanguageAttribute> Özniteliğini kullanarak bir uydu derlemesi belirtmediğiniz müddetçe, bu, en son geri dönüş (son üst öğe) öğesidir. Bu nedenle, ana derlemenizin her zaman varsayılan bir kaynak kümesi içermesini öneririz. Bu, özel durumların oluşmasını önlemeye yardımcı olur. Varsayılan bir kaynak dosyası ekleyerek, tüm kaynaklar için bir geri dönüş sağlarsınız ve çok önemli olmasa bile Kullanıcı için en az bir kaynağın her zaman mevcut olduğundan emin olursunuz.

5. Son olarak, çalışma zamanı varsayılan (geri dönüş) kültürü için bir kaynak dosyası bulamazsa, kaynağın bulunamadığını <xref:System.Resources.MissingManifestResourceException> göstermek <xref:System.Resources.MissingSatelliteAssemblyException> için bir veya özel durum oluşturulur. Kaynak dosyası bulunursa ancak istenen kaynak yoksa istek geri döner `null`.

### <a name="ultimate-fallback-to-satellite-assembly"></a>Uydu Derlemesi için Ultimate Geri Dönüş

İsteğe bağlı olarak ana derlemeden kaynakları kaldırabilir ve çalışma zamanının, belirli bir kültüre karşılık gelen bir uydu derlemesinden en son geri dönüş kaynaklarını yüklemesi gerektiğini belirtebilirsiniz. Geri dönüş işlemini denetlemek için, <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> oluşturucuyu kullanır ve Kaynak Yöneticisi bir <xref:System.Resources.UltimateResourceFallbackLocation> parametre için, temel derlemeden veya bir uydu derlemesinden geri dönüş kaynakları ayıklanıp ayıklanmayacağını belirten bir değer sağlarsınız.

Aşağıdaki .NET Framework örnek, bir uygulamanın <xref:System.Resources.NeutralResourcesLanguageAttribute> geri dönüş kaynaklarını Fransızca (`fr`) dili için bir uydu derlemesinde depolamak üzere özniteliğini kullanır. Örnek, adlı `Greeting`tek bir dize kaynağını tanımlayan iki metin tabanlı kaynak dosyasına sahiptir. Birincisi, Resources. fr. txt, bir Fransızca dil kaynağı içerir.

```text
Greeting=Bon jour!
```

İkinci, kaynak, ru. txt, bir Rusça dil kaynağı içerir.

```text
Greeting=Добрый день
```

Bu iki dosya, komut satırından [kaynak dosya Oluşturucu (Resgen. exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) çalıştırılarak. resources dosyalarına derlenir. Fransızca dil kaynağı için komut şu şekilde olur:

**Resgen. exe resources. fr. txt**

Rusça dil kaynağı için komut şu şekilde olur:

**Resgen. exe resources. ru. txt**

. Resources dosyaları, Fransızca dili kaynağı için komut satırından aşağıdaki gibi, [derleme Bağlayıcısı (al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) çalıştırılarak dinamik bağlantı kitaplıklarına katıştırılır:

**Al/t: lib/Embed: resources. fr. resources/Culture: fr/Out: fr\Example1.resources.dll**

ve Rusça dil kaynağı için aşağıdaki gibi:

**Al/t: lib/Embed: resources. ru. resources/Culture: ru/Out: ru\Example1.resources.dll**

Uygulama kaynak kodu Example1.cs veya example1. vb adlı bir dosyada bulunur. Varsayılan uygulama kaynağının <xref:System.Resources.NeutralResourcesLanguageAttribute> fr alt dizininde olduğunu göstermek için özniteliğini içerir. Kaynak Yöneticisi başlatır, `Greeting` kaynağın değerini alır ve bunu konsola görüntüler.

[!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
[!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]

Ardından aşağıdaki gibi komut C# satırından kaynak kodu derleyebilirsiniz:

```console
csc Example1.cs
```

Visual Basic Derleyicisi komutu çok benzerdir:

```console
vbc Example1.vb
```

Ana derlemede ekli kaynak olmadığından, `/resource` anahtarını kullanarak derlemeniz gerekmez.

Dilini Rusça dışında bir şey olan bir sistemden çalıştırdığınızda, aşağıdaki çıktıyı görüntüler:

```output
Bon jour!
```

## <a name="suggested-packaging-alternative"></a>Önerilen Paketleme Alternatifi

Zaman veya bütçe kısıtlamaları, uygulamanızın desteklediği her alt kültür için bir kaynak kümesi oluşturmanızı önleyebilir. Bunun yerine, bir üst kültür için tüm ilgili alt kültürlerin kullanabileceği tek bir uydu derlemesi oluşturabilirsiniz. Örneğin, bölgeye özgü Ingilizce kaynaklar isteyen kullanıcılar tarafından alınan tek bir Ingilizce uydu bütünleştirilmiş kodu (en) ve bölgeye özgü Alman kaynakları isteyen kullanıcılar için tek bir Alman uydu derlemesi (de) sağlayabilirsiniz. Örneğin, Almanya (de-DE), Avusturya (de-AT) ve Isviçre (de-CH) için Almanca için istekler, Almanya uydu derlemesine (de) geri döner. Varsayılan kaynaklar son geri dönüşlerdir ve bu nedenle uygulamanızın kullanıcılarının büyük bölümü tarafından istenen kaynaklar olması gerekir, bu nedenle bu kaynakları dikkatle seçin. Bu yaklaşım, daha az özel olan kaynakları dağıtır, ancak uygulamanızın yerelleştirme maliyetlerini önemli ölçüde azaltabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)
- [Kaynak Dosyaları Oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Uydu Derlemeleri Oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)

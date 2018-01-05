---
title: "Ngen.exe (Yerel Görüntü Oluşturucu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
caps.latest.revision: "57"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 074b5aae9d92b83d310a003e85709a4ba8e40c46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (Yerel Görüntü Oluşturucu)
Yerel Görüntü Oluşturucusu (Ngen.exe), yönetilen uygulamaların performansını artıran bir araçtır. Ngen.exe, işlemciye özel derlenmiş makine kodu içeren dosyalar olan yerel görüntüler oluşturur ve bunları yerel bilgisayarın yerel görüntü önbelleğine yükler. Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.  
  
 Ngen.exe içinde yapılan değişiklikleri [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:  
  
-   Ngen.exe artık derlemeleri tam güven ile derler ve kod erişimi güvenliği (CAS) ilkesi artık değerlendirilmez.  
  
-   Ngen.exe ile oluşturulan yerel görüntüler artık kısmi güvende çalışan uygulamaların içine yüklenemez.  
  
 Ngen.exe'ye .NET Framework 2.0 içinde yapılan değişiklikler:  
  
-   Bir derlemeyi yüklemek ayrıca bağımlılıklarını da yükleyerek Ngen.exe'nin sözdizimini basitleştirir.  
  
-   Yerel görüntüler artık uygulama etki alanları arasında paylaşılabilir.  
  
-   Yeni bir eylem `update`, geçersiz kılındı görüntüleri yeniden oluşturur.  
  
-   Eylemler, görüntüleri oluşturmak ve yüklemek için bilgisayardaki boşta kalma süresini kullanan bir servis tarafından ertelenebilir.  
  
-   Görüntü geçersiz kılmanın bazı nedenleri kaldırıldı.  
  
 Windows 8'de bkz [yerel görüntü görev](http://msdn.microsoft.com/en-us/9b1f7590-4e0d-4737-90ef-eaf696932afb).  
  
 Ngen.exe ve yerel görüntü hizmetini kullanma hakkında ek bilgi için bkz: [yerel görüntü hizmeti](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).  
  
> [!NOTE]
>  Ngen.exe sözdizimi sürüm 1.0 ve 1.1 .NET Framework'ün bulunabilir [yerel Görüntü Oluşturucu (Ngen.exe) eski sözdizimi](http://msdn.microsoft.com/en-us/5a69fc7a-103f-4afc-8ab4-606adcb46324).  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a>Eylemler  
 Aşağıdaki tabloda her söz dizimi görülmektedir `action`. Ürününün parçaları açıklamaları için bir `action`, bkz: [bağımsız değişkenleri](#ArgumentTable), [öncelik düzeyleri](#PriorityTable), [senaryoları](#ScenarioTable), ve [Config](#ConfigTable)tablo. [Seçenekleri](#OptionTable) tabloda açıklanmaktadır `options` ve Yardım anahtarlar.  
  
|Eylem|Açıklama|  
|------------|-----------------|  
|`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]|Bir derleme ve bağımlılıkları için yerel görüntüler oluştur ve görüntüleri yerel görüntü önbelleğine yükle.<br /><br /> Varsa `/queue` belirtilmemişse, yerel görüntü hizmet için eylem sıraya alındı. Varsayılan öncelik 3'tür. Bkz: [öncelik düzeyleri](#PriorityTable) tablo.|  
|`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|Bir derleme ve bağımlılıklarının yerel görüntülerini yerel görüntü önbelleğinden sil.<br /><br /> Tek bir görüntüyü ve bağımlılıklarını kaldırmak için, görüntüyü yüklemek için kullanılan aynı komut satırı bağımsız değişkenlerini kullanın. **Not:** başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], eylem `uninstall` * artık desteklenmiyor.|  
|`update` [`/queue`]|Geçersiz olan yerel görüntüleri güncelleştir.<br /><br /> Varsa `/queue` belirtilirse, güncelleştirmeleri yerel görüntü hizmet için sıraya alınır. Güncelleştirmeler her zaman 3 önceliğindedir ve bilgisayar boşta olduğunda çalışır.|  
|`display` [`assemblyName` &#124; `assemblyPath`]|Bir derleme ve bağımlılıkları için yerel görüntülerin durumunu görüntüle.<br /><br /> Eğer bağımsız değişken sağlanmazsa, yerel görüntü önbelleğindeki her şey görüntülenir.|  
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> veya<br /><br /> `eqi` [1&#124;2&#124;3]|Sıraya alınan derleme işlerini yürüt.<br /><br /> Eğer bir öncelik belirtilirse, ona eşit veya daha büyük önceliğe sahip derleme işleri yürütülür. Eğer öncelik belirtilmezse, sıraya alınan tüm derleme işleri yürütülür.|  
|`queue` {`pause` &#124; `continue` &#124; `status`}|Yerel görüntü hizmetini duraklat, duraklatılan hizmetin devam etmesine izin ver veya hizmetin durumunu sorgula.|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a>Arguments  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`assemblyName`|Derlemenin tam görünen adı. Örneğin, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Not:** bir kısmi derleme adı gibi sağlayabilir `myAssembly`, için `display` ve `uninstall` eylemler. <br /><br /> Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.|  
|`assemblyPath`|Derlemenin açık yolu. Tam veya göreli bir yol belirtebilirsiniz.<br /><br /> Eğer bir yol belirtmeden dosya adı belirtilseniz, derleme geçerli dizinde bulunmalıdır.<br /><br /> Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a>Öncelik Düzeyleri  
  
|Öncelik|Açıklama|  
|--------------|-----------------|  
|`1`|Yerel görüntüler, boşta kalma süresi beklenmeden hemen oluşturulur ve yüklenir.|  
|`2`|Yerel görüntüler boşta kalma süresi beklenmeden, ancak tüm 1 öncelikli eylemler (ve bağımlılıkları) tamamlandıktan sonra yüklenir.|  
|`3`|Yerel görüntüler, yerel görüntü hizmeti bilgisayarın boşta olduğunu algıladığında yüklenir. Bkz: [yerel görüntü hizmet](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).|  
  
<a name="ScenarioTable"></a>   
## <a name="scenarios"></a>Senaryolar  
  
|Senaryo|Açıklama|  
|--------------|-----------------|  
|`/Debug`|Bir hata ayıklayıcı altında kullanılabilen yerel görüntüler oluştur.|  
|`/Profile`|Bir profil oluşturucu altında kullanılabilen yerel görüntüler oluştur.|  
|`/NoDependencies`|Belirli senaryo seçeneklerinin gerektirdiği en az sayıda yerel görüntü oluştur.|  
  
<a name="ConfigTable"></a>   
## <a name="config"></a>Config  
  
|Yapılandırma|Açıklama|  
|-------------------|-----------------|  
|`/ExeConfig:``exePath`|Belirtilen çalıştırılabilir derlemesinin yapılandırmasını kullan.<br /><br /> Ngen.exe, bağımlılıklara bağlarken yükleyici ile aynı kararları almalıdır. Paylaşılan bir bileşen çalışma zamanında yüklendiğinde kullanarak <xref:System.Reflection.Assembly.Load%2A> yöntemi, uygulamanın yapılandırma dosyasına belirler paylaşılan bileşeni için yüklenen bağımlılıkları — Örneğin, yüklenen bir bağımlılık sürümü. `/ExeConfig` Anahtar üzerinde bağımlılıkları yüklenmiş çalışma zamanında Ngen.exe rehberlik sağlar.|  
|`/AppBase:``directoryPath`|Bağımlılıkları bulurken, uygulama tabanı olarak belirtilen dizini kullan.|  
  
<a name="OptionTable"></a>   
## <a name="options"></a>Seçenekler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/nologo`|Microsoft başlangıç başlığını bastır.|  
|`/silent`|Başarı iletilerinin görüntülenmesini bastır.|  
|`/verbose`|Hata ayıklama için ayrıntılı bilgi görüntüle. **Not:** işletim sistemi kısıtlamaları nedeniyle kadar ek bilgiler bu seçenek Windows 98 ve Windows Millennium Edition görüntülemez.|  
|`/help`, `/?`|Geçerli yayın için komut sözdizimi ve seçenekleri görüntüle.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ngen.exe'yi çalıştırabilmek için yönetici ayrıcalıklarınızın olması gerekir.  
  
> [!CAUTION]
>  Ngen.exe'yi tam güvenilir olmayan derlemeler üzerinde çalıştırmayın. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]Ngen.exe derlemeleri tam güven ile derler ve kod erişim güvenliği (CAS) ilkesi artık değerlendirilir.  
  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Ngen.exe ile oluşturulan yerel görüntüler kısmi güvende çalışan uygulamalara artık yüklenebilir. Bunun yerine anlık (JIT) derleyici çağrılır.  
  
 Ngen.exe tarafından belirtilen derleme için doğal görüntüleri oluşturur `assemblyname` bağımsız değişkeni `install` eylem ve tüm bağımlılıklarını. Bağlılıklar derleme bildirisindeki referanslar ile belirlenir. Yansıma, örneğin çağırarak kullanarak uygulama yüklendiğinde, bir bağımlılık ayrı olarak yüklemeniz gereken tek senaryodur <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.  
  
> [!IMPORTANT]
>  Kullanmayın <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi ile yerel görüntüler. Bu metotla yüklenen bir görüntü, yürütme bağlamındaki diğer derlemeler tarafından kullanılamaz.  
  
 Ngen.exe bağımlılıklar için bir sayaç tutar. Örneğin, varsayalım `MyAssembly.exe` ve `YourAssembly.exe` her ikisi de yerel görüntü önbelleği yüklenir ve her ikisi de başvuran `OurDependency.dll`. Varsa `MyAssembly.exe` kaldırılır, `OurDependency.dll` kaldırılmamış. Yalnızca zaman kaldırılan `YourAssembly.exe` de kaldırılır.  
  
 Eğer genel derleme önbelleğindeki bir derleme için doğal görüntü üretiyorsanız, onun görünür ismini belirtiniz. Bkz: <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.  
  
 Ngen.exe'nin ürettiği doğal görüntüler uygulama alanı içerisinde paylaşılabilir. Bu, Ngen.exe'yi derlemelerin uygulama etki alanları arasında paylaşılması gerektiği senaryolarda kullanabileceğiniz anlamına gelir. Alan bağımsızlığını belirtmek için:  
  
-   Uygulama <xref:System.LoaderOptimizationAttribute> uygulamanıza özniteliği.  
  
-   Ayarlama <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> kurulum bilgilerini almak için yeni bir uygulama etki alanı oluşturduğunuzda özelliği.  
  
 Birden çok uygulama alanına aynı derleme yüklediğiniz zaman mutlaka alan-bağımsız kod kullanın. Eğer bir doğal görüntü paylaşılmış alana yüklendikten sonra paylaşılmamış alana yüklenirse, görüntü kullanılamaz.  
  
> [!NOTE]
>  Alan-bağımsız kod yüklemesi geri alınamaz (geri döndürülemez) ve performans, özellikle statik elemanlara erişildiği zaman, çok az daha yavaş olabilir.  
  
 Bu açıklamalar bölümünde:  
  
-   [Farklı senaryolar için görüntüleri oluşturma](#Scenarios)  
  
-   [Ne zaman yerel görüntüler kullanılacağını belirleme](#WhenToUse)  
  
    -   [Bellek kullanımını geliştirilmiş](#Memory)  
  
    -   [Hızlı Uygulama Başlatma](#Startup)  
  
    -   [Kullanım değerlendirmelerine özeti](#UsageSummary)  
  
-   [Derleme temel adresler önemini](#BaseAddresses)  
  
-   [Sabit bağlama](#HardBinding)  
  
    -   [Bir bağımlılık için bağlama ipucu belirtme](#DependencyHint)  
  
    -   [Varsayılan bağlama ipucu bir derleme için belirtme](#AssemblyHint)  
  
-   [Ertelenmiş işleme](#Deferred)  
  
-   [Yerel görüntüler ve JIT derleme](#JITCompilation)  
  
    -   [Geçersiz görüntüler](#InvalidImages)  
  
-   [Sorun giderme](#Troubleshooting)  
  
    -   [Derleme bağlaması Günlük Görüntüleyici](#Fusion)  
  
    -   [JITCompilationStart yönetilen hata ayıklama Yardımcısı](#MDA)  
  
    -   [Yerel görüntü oluşturma dışında kullanmama](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a>Farklı senaryolar için görüntüleri oluşturma  
 Yerel görüntü için derlemeyi oluşturduktan sonra çalışma zamanı bulun ve bu yerel görüntü derleme her çalıştığında kullanmak otomatik olarak çalışır. Kullanım senaryolarına göre, birden fazla görüntüler oluşturulabilir.  
  
 Bir hata ayıklama veya senaryo profil derleme çalıştırırsanız, örneğin, çalışma zamanı ile oluşturulan yerel bir görüntü arar `/Debug` veya `/Profile` seçenekleri. Eğer eşleşen bir doğal görüntü bulamazsa, çalışma zamanı standart JIT derlemesine geri döner. Yerel görüntüler hata ayıklamak için tek yolu ile yerel bir görüntü oluşturmaktır `/Debug` seçeneği.  
  
 `uninstall` Eylem tüm senaryoları veya yalnızca seçilen senaryolar kaldırabilmeniz için senaryolar de algılar.  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a>Ne zaman yerel görüntüler kullanılacağını belirleme  
 Yerel görüntüler iki alanda performans iyileştirmesi sağlayabilir: daha iyi bellek kullanımı ve daha az başlangıç zamanı.  
  
> [!NOTE]
>  Yerel görüntülerin performansı; kod ve veri erişim desenleri, modül sınırları dışına yapılan çağrı sayısı ve diğer uygulamalar tarafından şimdiye kadar yüklenmiş olan bağımlılık sayısı gibi analizi zorlaştıran çeşitli etkenlere bağlıdır. Yerel görüntülerin uygulamanıza yararlı olup olmadığını belirlemenin tek yolu, anahtar dağıtım senaryolarınızda yapacağını dikkatli performans ölçümleridir.  
  
<a name="Memory"></a>   
### <a name="improved-memory-use"></a>Bellek kullanımını geliştirilmiş  
 Yerel görüntüler kod işlemler arasında paylaşıldığında bellek kullanımını önemli ölçüde iyileştirebilirler. Yerel görüntüler Windows PE dosyalarıdır, yani bir .dll dosyasının tek kopyası birden çok işlem tarafından paylaşılabilir; buna karşılık, JIT derleyicisi tarafından üretilen yerel kod özel bellekte tutulur ve paylaşılamaz.  
  
 Terminal hizmetleri altında çalışan uygulamalar da paylaşılan kod sayfalarından yararlanabilir.  
  
 Ek olarak, JIT derleyicisini yüklememek her uygulama örneği için sabit bir miktarda bellek kazandırır.  
  
<a name="Startup"></a>   
### <a name="faster-application-startup"></a>Hızlı Uygulama Başlatma  
 Derlemeleri Ngen.exe ile ön derlemek bazı uygulamalar için başlangıç süresini iyileştirebilir. Genel olarak, uygulamalar bileşen derlemelerini paylaştığında kazanç olabilir, çünkü ilk uygulama başladıktan sonra paylaşılan bileşenler sonraki uygulamalar için zaten yüklü olur. Uygulamadaki tüm derlemelerin sabit diskten yüklenmesini gerektiren soğuk başlangıç yerel görüntülerden pek fayda kazanmaz, çünkü sabit disk erişim süresi baskın olur.  
  
 Sabit bağlama başlatma süresini etkileyebilir, çünkü ana uygulama derlemesine sabit bağlı olan tüm resimler aynı anda yüklenmelidirler.  
  
> [!NOTE]
>  Önce [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], yükleyici genel derleme önbelleğinde etkili bir şekilde tüm geliştirme ortadan değil tanımlayıcı adlı derlemeler ek doğrulama gerçekleştirdiğinden genel derleme önbelleğinde paylaşılan, tanımlayıcı adlı bileşenleri yerleştirileceği Yerel görüntüler kullanılarak elde başlangıç süre. Sürümünde sunulan en iyi duruma getirme [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] ek doğrulama kaldırıldı.  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a>Kullanım değerlendirmelerine özeti  
 Aşağıdaki genel önemli noktalar ve uygulama önemli noktaları uygulamanız için yerel görüntüleri değerlendirmek üzere çaba harcayıp harcamamaya karar vermenize yardımcı olabilir:  
  
-   Yerel görüntüler MSIL'den daha hızlı yüklenir çünkü JIT derlemesi ve tür güvenliği doğrulaması gibi pek çok başlangıç aktivitesine gereksinimi ortadan kaldırırlar.  
  
-   Yerel görüntüler daha küçük ilk çalışma kümesi gerektirirler çünkü JIT derleyicisine gerek yoktur.  
  
-   Yerel görüntüler işlemler arasında kod paylaşımını etkinleştirir.  
  
-   Yerel görüntüler MSIL derlemelerinden daha fazla sabit disk alanı gerektirir ve üretmek için büyük miktarda zaman gerektirebilir.  
  
-   Yerel görüntüler bakılmalıdır.  
  
    -   Orijinal derleme veya bağımlılıklarından biri değiştiğinde görüntüler yeniden oluşturulmalıdır.  
  
    -   Tek bir derleme farklı uygulamalarda ya da farklı senaryolarda kullanılması için birden çok yerel görüntüye ihtiyaç duyabilir. Örneğin, iki uygulamadaki yapılandırma bilgileri aynı bağımlı derleme için farklı bağlama kararlarına neden olabilir.  
  
    -   Yerel görüntüler bir yönetici, yani Yöneticiler grubu içindeki bir Windows hesabı, tarafından üretilmelidir.  
  
 Bu genel önemli noktalara ek olarak, yerel görüntülerin bir performans kazancı sağlayıp sağlamayacağını belirlerken uygulamanızın doğası da göz önüne alınmalıdır:  
  
-   Eğer uygulamanız pek çok paylaşılan bileşen kullanan bir ortamda çalışıyorsa, yerel görüntüler bileşenlerin birden çok işlem tarafından paylaşılmasını sağlar.  
  
-   Eğer uygulamanız birden çok uygulama alanı kullanıyorsa, yerel görüntüler alanlar arasında kod sayfalarının paylaşılmasını sağlar.  
  
    > [!NOTE]
    >  .NET Framework 1.0 ve 1.1 sürümlerinde, yerel görüntüler uygulama etki alanları arasında paylaşılamaz. Bu, sürüm 2.0 ve sonrasında geçerli değildir.  
  
-   Eğer uygulamanız Terminal Server altında çalışacaksa, yerel görüntüler kod sayfalarının paylaşılmasını sağlar.  
  
-   Büyük uygulamalar yerel görüntülere derlemekten genellikle yarar görür. Küçük uygulamalar genellikle yarar görmez.  
  
-   Uzun süre çalışan uygulamalarda, çalışma zamanı JIT derlemesi yerel görüntülerden biraz daha iyi çalışır. (Sabit bağlama bu performans farkını belirli bir ölçüde azaltabilir.)  
  
<a name="BaseAddresses"></a>   
## <a name="importance-of-assembly-base-addresses"></a>Derleme temel adresler önemini  
 Yerel görüntüler Windows PE dosyaları olduğu için, diğer çalıştırılabilir dosyalardaki aynı yeniden temellendirme sorunlarıyla karşılaşırlar. Eğer sıkı bağlama kullanılırsa, yeniden konumlandırmanın performans maliyeti daha da belirgin olur.  
  
 Bir yerel görüntü için temel adresi ayarlamak için, derlemenin temel adresini ayarlama amacıyla derleyicinizin uygun seçeneğini kullanın. Ngen.exe yerel görüntü için bu temel adresi kullanır.  
  
> [!NOTE]
>  Yerel görüntüler, oluşturuldukları yönetilen derlemelerden daha büyüktür. Bu daha büyük boyutlara izin vermek için temel adresler hesaplanmalıdır.  
  
 Bir yerel görüntünün tercih edilen temel adresini görüntülemek için dumpbin.exe gibi bir araç kullanabilirsiniz.  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a>Sabit bağlama  
 Sıkı bağlama doğal görüntüler için birim zamanda yapılan işi artırır ve çalışma seti alanını azaltır. Sıkı bağlamanın dezavantajı, bir derleme yüklendiğinde o derlemeye sıkı bağlı olan tüm görüntülerin de yüklenmesinin gerekmesidir. Bu büyük bir uygulama için başlatma zamanını önemli derecede artırabilir.  
  
 Sıkı bağlama, uygulamanızın performansının kritik olduğu senaryolarda yüklenen bağımlılıklar için uygundur. Herhangi bir doğal görüntü kullanımında, sıkı bağlanmanın uygulamanızın performansını arttırıp arttırmadığını öğrenmenin tek yolu dikkatli(hassas) performans ölçümleridir.  
  
 <xref:System.Runtime.CompilerServices.DependencyAttribute> Ve <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> öznitelikleri için Ngen.exe sabit bağlama ipuçları sağlayan izin verir.  
  
> [!NOTE]
>  Bu değerler Ngen.exe'ye teknik/tavsiyelerdir, komutlar değillerdir. Bunları kullanmak sıkı bağlamayı garanti etmez. Bu değerlerin anlamları ileri yayınlarda değişebilir.  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a>Bir bağımlılık için bağlama ipucu belirtme  
 Uygulama <xref:System.Runtime.CompilerServices.DependencyAttribute> belirtilen bağımlılık yüklenecek olasılığını belirtmek için bir derleme. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>Sabit bağlama uygun olduğunu gösteren <xref:System.Runtime.CompilerServices.LoadHint.Default> varsayılan bağımlılık için kullanılması gereken, gösterir ve <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> sabit bağlama uygun olmadığını gösterir.  
  
 Aşağıdaki kod, iki bağlılığı olan bir derlemenin özniteliklerini gösterir. İlk bağımlılık (Assembly1) sıkı bağlama için uygun bir adaydır ve ikinci bağımlılık (Assembly2) değildir.  
  
```vb  
Imports System.Runtime.CompilerServices  
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>  
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>  
```  
  
```csharp  
using System.Runtime.CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]  
```  
  
```cpp  
using namespace System::Runtime::CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];  
```  
  
 Derleme ismi dosya ismi uzantısını içermez. Görünür isim kullanılabilir.  
  
<a name="AssemblyHint"></a>   
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Varsayılan bağlama ipucu bir derleme için belirtme  
 Varsayılan bağlama ipuçları, yalnızca onlara bağlılığı olan herhangi bir uygulama tarafından anında ve sıkça kullanılacak olan derlemeler için gereklidir. Uygulama <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> ile <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> sabit bağlama kullanılması gerektiğini belirtmek için bu tür derlemeler için.  
  
> [!NOTE]
>  Uygulamak için bir sebep olmadığı <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> Bu, herhangi bir değer özniteliğiyle dışında uygulama çünkü kategoriye değil .dll derlemelerine <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> öznitelik hiç yapmamayı aynı etkiye sahiptir.  
  
 Microsoft kullanır <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> sabit bağlama mscorlib.dll gibi .NET Framework derlemelerde çok az sayıda için varsayılan değer olduğunu belirtmek için.  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a>Ertelenmiş işleme  
 Çok büyük bir uygulama için yerel görüntü oluşturmak uzun bir süre alabilir. Benzer şekilde, paylaşılan bir bileşene veya bilgisayar seçeneklerine yapılan değişiklikler pek çok yerel görüntünün güncellenmesini gerektirebilir. `install` Ve `update` Eylemler sahip bir `/queue` ertelenmiş yürütme işlemi yerel görüntü hizmeti tarafından sıraya koyar seçeneği. Ayrıca, Ngen.exe sahip `queue` ve `executeQueuedItems` hizmet üzerinde biraz denetim sağlamanıza eylemler. Daha fazla bilgi için bkz: [yerel görüntü hizmeti](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a>Yerel görüntüler ve JIT derleme  
 Eğer Ngen.exe assembly içerisinde oluşturamayacağı herhangi bir metotla karşılaşırsa, onları doğal görüntü (özgün görüntü) içerisine dahil etmez. Çalışma zamanı bu derlemeyi çalıştırdığı zaman, doğal görüntünün içerisine dahil edilmeyen metotlar için JIT derleme işlemine döner  
  
 Ek olarak, derleme yükseltildiyse veya görüntü herhangi bir sebeple geçersiz kılındıysa yerel görüntüler kullanılmaz.  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a>Geçersiz görüntüler  
 Ngen.exe'yi bir derlemenin yerel görüntüsünü oluşturmak için kullandığınızda; çıktı, belirlediğin komut satırı seçeneklerine ve bilgisayarınızdaki belirli ayarlara bağlıdır. Bu ayarlar aşağıdakileri içerir:  
  
-   .NET Framework sürümü.  
  
-   Windows 9 x ailesi Windows NT ailesine değişiklikse işletim sistemi, sürümü.  
  
-   Derlemenin tam kimliği (yeniden derleme kimliği değiştirir).  
  
-   Derlemenin başvurduğu tüm derlemelerin tam kimliği (yeniden derleme kimliği değiştirir).  
  
-   Güvenlik etkenleri.  
  
 Ngen.exe bir doğal görüntü oluşturduğu zaman bu bilgiyi kaydeder. Bir derlemeyi çalıştırdığınız zaman, çalışma zamanı bilgisayarın o anki çevresine uyan seçenekler ve ayarlarla oluşturulmuş olan doğal görüntüyü arar. Çalışma zamanı eğer eşleşen bir doğal görüntü bulamazsa, derlemeyi JIT ile derleme yoluna gider. Bilgisayarın ayarlarına ve çevresine uygulanan aşağıdaki değişiklikler doğal görüntünün geçersiz olmasına sebep olur:  
  
-   .NET Framework sürümü.  
  
     Eğer .NET framework'e güncelleme uygularsanız, Ngen.exe kullanarak oluşturduğunuz bütün imajlar geçersiz sayılır. Bu nedenle, .NET Framework'ün tüm güncelleştirmeleri yürütme `Ngen Update` tüm yerel görüntüler yeniden emin olmak için komutu. .NET framework kuracağı .Net framework kütüphaneleri için yeni görüntüleri otomatik olarak oluşturur.  
  
-   Windows 9 x ailesi Windows NT ailesine değişiklikse işletim sistemi, sürümü.  
  
     Örneğin, bir bilgisayarda çalışan işletim sisteminin sürümü Windows XP için Windows 98'den değişirse, yerel görüntü önbellekte depolanan tüm yerel görüntüler geçersiz hale gelir. İşletim sistemi Windows XP için Windows 2000'den değişirse, ancak, görüntüleri geçersiz kılınır değil.  
  
-   Derlemenin kesin kimliği.  
  
     Eğer derlemeyi yeniden derlerseniz, derlemeye karşılık gelen doğal görüntü geçersiz olur.  
  
-   Derlemenin referans ettiği bütün derlemelerin tam kimliği.  
  
     Eğer yönetilmiş bir derlemeyi güncellerseniz, o derlemeye direk ya da dolaylı yoldan bağlı olan bütün doğal görüntüler geçersiz olur ve yeniden oluşturulması gerekir. Bu hem normal tercihleri/ayarları hem de sıkı-bağlama bağlılıklarını içerir. Bir yazılım güncelleştirmesi uygulandığı zaman, yükleme programı yürütülecek bir `Ngen Update` tüm bağımlı yerel görüntüler yeniden emin olmak için komutu.  
  
-   Güvenlik etkenleri.  
  
     Önceden yetkilendirilmiş bir derlemenin izinlerini kısıtlamak için makina güvenlik politikasında değişiklik yapmak, o derleme için önceden derlenmiş olan doğal imajın geçersiz olmasına sebep olabilir  
  
     Ortak dil çalışma zamanı kod erişim güvenliği nasıl yönetir ve izinleri kullanma hakkında ayrıntılı bilgi için bkz: [kod erişim güvenliği](../../../docs/framework/misc/code-access-security.md).  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a>Sorun giderme  
 Aşağıdaki sorun giderme konularına hangi yerel görüntüler kullanılır ve uygulamanız tarafından kullanılamaz görmenize olanak veren, JIT Derleyici bir yöntem derlemek başlar ve dışında yerel görüntü derlenmesini opt gösterilmektedir belirlemek için belirtilen yöntemleri.  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a>Derleme Bağlaması Günlük Görüntüleyici  
 Yerel görüntüler, uygulamanız tarafından kullanılmakta onaylamak için kullanabileceğiniz [Fuslogvw.exe (Derleme bağlaması Günlük Görüntüleyici)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md). Seçin **yerel görüntüler** içinde **günlük kategorileri** bağlaması Günlük Görüntüleyici penceresinde kutusu. Fuslogvw.exe bir doğal imajın neden reddedildiği hakkında bilgi sağlar.  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>JITCompilationStart yönetilen hata ayıklama Yardımcısı  
 Kullanabileceğiniz [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) yönetilen hata ayıklama Yardımcısı (JIT Derleyici bir işlev derleme başladığında belirlemek için MDA).  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a>Yerel görüntü oluşturma dışında kullanmama  
 Bazı durumlarda, belirli bir yöntemi veya yöntem derlenmiş JIT olması tercih edebilirsiniz için yerel bir görüntü yerine yerel bir görüntü için derlenmiş zorluk oluşturma NGen.exe olabilir. Bu durumda, kullanabileceğiniz `System.Runtime.BypassNGenAttribute` belirli bir yöntem için yerel bir görüntü oluşturma NGen.exe önlemek için öznitelik. Öznitelik kodu yerel görüntüde eklemek istiyor musunuz her yöntemi için ayrı ayrı uygulanması gerekir. NGen.exe öznitelik tanır ve kodu buna karşılık gelen yöntemi için yerel görüntü oluşturmaz.  
  
 Ancak, unutmayın, `BypassNGenAttribute` .NET Framework Sınıf Kitaplığı'nda bir türü olarak tanımlı değil. Kodunuzu özniteliğinde kullanmak için önce aşağıdaki gibi tanımlamanız gerekir:  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
 [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]  
  
 Daha sonra bir yöntem başına temelinde öznitelik uygulayabilirsiniz. Aşağıdaki örnek, yerel bir görüntü için üretmemelidir yerel Görüntü Oluşturucu talimatı verir `ExampleClass.ToJITCompile` yöntemi.  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
 [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komutu için yerel bir görüntü oluşturur `ClientApp.exe`, geçerli dizinde bulunan ve yerel görüntü önbelleği görüntüsü yükler. Derleme için bir yapılandırma dosyası varsa, onu Ngen.exe kullanır. Yerel görüntüler tüm .dll dosyaları için ek olarak, oluşturulan `ClientApp.exe` başvuruları.  
  
```  
ngen install ClientApp.exe  
```  
  
 Ngen.exe ile yüklenmiş bir resim, bir kök olarak da adlandırılır. Kök, bir uygulama veya paylaşılan bir bileşen olabilir.  
  
 Aşağıdaki komutu için yerel bir görüntü oluşturur `MyAssembly.exe` belirtilen yola sahip.  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 Derlemeler ve bağımlılıklarını belirlerken Ngen.exe ortak dil çalışma zamanı tarafından kullanılan aynı algılama mantığını kullanır. Varsayılan olarak, dizin içeren `ClientApp.exe` uygulamanın ana dizin kullanılır ve bu dizinde tüm derleme yoklama başlar. Kullanarak bu davranışı geçersiz kılabilirsiniz `/AppBase` seçeneği.  
  
> [!NOTE]
>  Bu, uygulama temel dizininin geçerli dizin olarak ayarlandığı .NET Framework 1.0 ve 1.1 sürümlerindeki Ngen.exe davranışından farklıdır.  
  
 Bir derlemeyi kullanarak bir .dll dosyası yüklenirse, örneğin bir başvuru olmadan bir bağımlılık olabilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi. Bu tür bir .dll dosyası için yerel bir görüntü ile uygulama derleme için yapılandırma bilgilerini kullanarak oluşturabileceğiniz `/ExeConfig` seçeneği. Aşağıdaki komutu için yerel bir görüntü oluşturur `MyLib.dll,` yapılandırma bilgilerini kullanarak `MyApp.exe`.  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 Uygulamayı kaldırdığınızda, bu şekilde yüklenen derlemeler kaldırılmaz.  
  
 Bir bağımlılık kaldırmak için yüklemek için kullanılan aynı komut satırı seçeneklerini kullanın. Aşağıdaki komutu kaldırır `MyLib.dll` önceki örnekten.  
  
```  
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 Genel bütünleştirilmiş kod önbelleğindeki bir derleme için yerel görüntü oluşturmak için, derlemenin görünen adını kullanın. Örneğin:  
  
```  
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
```  
  
 NGen.exe yüklediğiniz her senaryo için ayrı bir görüntü kümesi oluşturur. Örneğin, aşağıdaki komutlar normal işlemler için tamamen yerel görüntü kümesi, hata ayıklama için farklı bir küme ve belirleme için üçüncüyü yükler:  
  
```  
ngen install MyApp.exe  
ngen install MyApp.exe /debug  
ngen install MyApp.exe /profile  
```  
  
### <a name="displaying-the-native-image-cache"></a>Yerel Görüntü Önbelleğini Görüntüleme  
 Yerel görüntüler önbelleğe yüklendikten sonra, Ngen.exe kullanılarak görüntülenebilirler. Aşağıdaki komut yerel görüntü belleğindeki tüm yerel görüntüleri görüntüler.  
  
```  
ngen display  
```  
  
 `display` Eylem listeler tüm kök derlemeler önce bilgisayarda ardında tüm yerel görüntülerin bir listesi.  
  
 Yalnızca bir derlemenin bilgilerini görüntülemek için o derlemenin basit adını kullanın. Aşağıdaki komutu tüm yerel görüntüler kısmi adı ile eşleşen yerel görüntü önbelleği görüntüler `MyAssembly`, bağımlılıklarını ve üzerinde bir bağımlılığa sahip tüm kökleri `MyAssembly`:  
  
```  
ngen display MyAssembly  
```  
  
 Hangi kökleri bir paylaşılan bileşen derlemeye dayanan bilerek yararlıdır etkisini hesaplanan bir `update` paylaşılan bileşen yükseltildikten sonra eylem.  
  
 Eğer bir derlemenin dosya uzantısını belirtirseniz, ya yolu belirtmeniz ya da Ngen.exe'yi derlemeyi içeren dizinden yürütmeniz gerekir:  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 Aşağıdaki komutu tüm yerel görüntüler ada sahip yerel görüntü önbelleği görüntüler `MyAssembly` ve sürüm 1.0.0.0.  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a>Görüntüleri Güncelleştirme  
 Görüntüler genellikle paylaşılan bir bileşen yükseltildikten sonra güncelleştirilir. Değiştirilmesi veya bağımlılıklarını değişti tüm yerel görüntülerini güncelleştirmek için kullanmak `update` bağımsız değişken içermeyen eylem.  
  
```  
ngen update  
```  
  
 Tüm görüntüleri güncelleştirmek uzun süren bir işlem olabilir. Yürütme için güncelleştirmeleri kullanarak yerel görüntü hizmeti tarafından sıraya koyar `/queue` seçeneği. Daha fazla bilgi için `/queue` seçeneği ve yükleme öncelikleri bkz [yerel görüntü hizmeti](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a>Görüntüleri Kaldırma  
 Ngen.exe bağımlılıkların bir listesini tutar, yani paylaşılan bileşenler yalnızca onlara bağlı olan tüm derlemeler kaldırıldığında kaldırılır. Ek olarak kök olarak yüklenmiş ortak bileşenler silinmez.  
  
 Aşağıdaki komut tüm senaryolar için kök kaldırır `ClientApp.exe`:  
  
```  
ngen uninstall ClientApp  
```  
  
 `uninstall` Eylemi, belirli senaryolar kaldırmak için kullanılabilir. Tüm hata ayıklama senaryoları için aşağıdaki komutu kaldırır `ClientApp.exe`:  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  Kaldırma `/debug` senaryoları her ikisini de içeren bir senaryo kaldırmaz `/profile` ve`/debug.`  
  
 Tüm senaryolarda belirli bir sürümü için aşağıdaki komutu kaldırır `ClientApp.exe`:  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 Tüm senaryoları için aşağıdaki komutları kaldırma `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` veya yalnızca bu derleme için hata ayıklama senaryosu:  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 İle `install` eylem, bir uzantı sağladığını da Ngen.exe derlemeyi içeren veya tam yolunu belirterek dizininden yürütme gerektirir.  
  
 Yerel görüntü hizmetle ilgili örnekler için bkz: [yerel görüntü hizmeti](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).  
  
## <a name="native-image-task"></a>Yerel Görüntü Görevi  
 Yerel görüntü görev oluşturur ve yerel görüntüler tutar Windows bir görevdir. Yerel görüntü görev oluşturur ve yerel görüntüler desteklenen senaryolar için otomatik olarak geri kazanır. (Bkz [yerel görüntü oluşturma](http://msdn.microsoft.com/en-us/2bc8b678-dd8d-4742-ad82-319e9bf52418).) Ayrıca kullanmak yükleyiciler sağlar [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) oluşturmak ve yerel görüntüler ertelenmiş aynı anda güncelleştirmek için.  
  
 Yerel görüntü görev her CPU mimarisi hedefleyen uygulamalar için derleme izin vermek için bilgisayarda her mimari desteklenen bir kez kaydedilir:  
  
|Görev adı|32 bit bilgisayar|64 bit bilgisayar|  
|---------------|----------------------|----------------------|  
|NET Framework NGEN v4.0.30319|Evet|Evet|  
|NET Framework NGEN v4.0.30319 64|Hayır|Evet|  
  
 Yerel görüntü görev, Windows 8 veya daha sonra çalıştırırken .NET Framework 4.5 ve sonraki sürümlerinde kullanılabilir. Windows'un önceki sürümlerinde, .NET Framework kullanan [yerel görüntü hizmeti](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).  
  
### <a name="task-lifetime"></a>Görev yaşam süresi  
 Genel olarak, Windows Görev Zamanlayıcısı'nı yerel görüntü görev bilgisayar boşta olduğunda her gece başlatır. Görev uygulama yükleyicilerini, tüm ertelenmiş yerel görüntü güncelleştirme isteklerinin ve Otomatik görüntü oluşturma tarafından sıraya herhangi bir ertelenmiş iş olup olmadığını denetler. Görev bekleyen iş öğeleri tamamlandıktan ve kapanır. Bilgisayar Görev yürütülürken boşta kaldıktan durursa, görev durdurur.  
  
 Yerel görüntü görev NGen.exe el ile çağrıları veya Görev Zamanlayıcı kullanıcı Arabirimi aracılığıyla el ile de başlatabilirsiniz. Görev bu yöntemlerden birini başlatılmışsa, bilgisayar artık boştayken çalışmaya devam edecek. Görüntüleri el ile NGen.exe kullanılarak oluşturulan uygulama yükleyicileri için tahmin edilebilir bir davranış etkinleştirmek için önceliklendirilir.  
  
## <a name="native-image-service"></a>Yerel Görüntü Hizmeti  
 Yerel görüntü hizmeti oluşturur ve yerel görüntüler tutan bir Windows hizmetidir. Yerel görüntü hizmeti yükleme ve yerel görüntüler için bilgisayar boşta olduğunda nokta güncelleştirmesi erteleme Geliştirici sağlar.  
  
 Normalde, yerel görüntü hizmeti, bir uygulama veya güncelleştirme için yükleme programını (Yükleyici) tarafından başlatılır. Öncelik 3 eylemler için hizmetin bilgisayarda boşta kalma süresi sırasında yürütür. Hizmet durumunu kaydeder ve birden çok yeniden başlatma gerekirse, devam etmeden yeteneğine sahiptir. Birden çok görüntü derlemeleri sıraya.  
  
 Hizmet ayrıca Ngen.exe komutu ile el ile etkileşime girer. El ile komutları arka plan etkinliği göre önceliklidir.  
  
> [!NOTE]
>  Windows Vista'da, yerel görüntü hizmet için görüntülenen ad "Microsoft.NET Framework NGEN sürüm 2.0.50727_X86" veya "Microsoft.NET Framework NGEN sürüm 2.0.50727_x64" dir. Tüm önceki sürümlerinde, Microsoft Windows'un, adı ".NET çalışma zamanı en iyi duruma getirme hizmeti sürüm 2.0.50727_X86" veya ".NET çalışma zamanı en iyi duruma getirme hizmeti sürüm 2.0.50727_x64" dir.  
  
### <a name="launching-deferred-operations"></a>Ertelenmiş işlemleri başlatma  
 Bir yükleme veya yükseltme işlemine başlamadan önce hizmetin duraklatılması önerilir. Bu yükleyici dosyalarını kopyalama veya genel derleme önbelleğinde derlemeleri koyma sırada hizmet yürütmez sağlar. Aşağıdaki Ngen.exe komut satırı hizmet duraklatır:  
  
```  
ngen queue pause  
```  
  
 Tüm ertelenmiş işlemler sıraya olduğunda, aşağıdaki komutu sürdürmek hizmet sağlar:  
  
```  
ngen queue continue  
```  
  
 Yerel görüntü oluşturma yeni bir uygulama yüklerken veya paylaşılan bir bileşen güncelleştirirken ertelemek için kullanmak `/queue` seçeneğini `install` veya `update` eylemler. Aşağıdaki Ngen.exe komut satırlarını paylaşılan bir bileşen için yerel bir görüntü yüklemek ve etkilenmiş tüm kökleri güncelleştirmesi gerçekleştirin:  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 `update` Eylem yeniden oluşturur, geçersiz kılındı, tüm yerel görüntüler yalnızca kullananlar `MyComponent`.  
  
 Uygulamanız birçok kökleri oluşuyorsa, ertelenmiş Eylemler önceliğini kontrol edebilirsiniz. Aşağıdaki komutları üç kökleri yükleme sırası. `Assembly1`boşta kalma süresini beklemeden önce yüklenir. `Assembly2`bekleme boşta kalma süresi, ancak tüm öncelik 1 eylemleri tamamladıktan sonra olmadan da yüklenir. `Assembly3`Hizmet bilgisayar boştayken algıladığında yüklenir.  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 Zaman uyumlu olarak kullanarak gerçekleşmesi için kuyruğa alınan eylemleri zorlayabilirsiniz `executeQueuedItems` eylem. İsteğe bağlı öncelik sağlarsanız, bu eylem eşit veya daha düşük önceliğe sahip kuyruğa alınan eylemleri etkiler. Aşağıdaki Ngen.exe komutu tüm kuyruğa alınan eylemleri hemen işler ve bitene kadar döndürmüyor varsayılan öncelik 3, olduğundan:  
  
```  
ngen executeQueuedItems  
```  
  
 Zaman uyumlu komutlar Ngen.exe tarafından yürütülen ve yerel görüntü hizmeti kullanmayın. Yerel görüntü hizmet çalışırken Ngen.exe kullanarak eylemleri yürütebilir.  
  
### <a name="service-shutdown"></a>Hizmet kapatma  
 İçeren bir Ngen.exe komutu yürütme tarafından başlatılan sonra `/queue` seçeneği, hizmet arka planda çalışır tüm eylemleri tamamlanana kadar. Hizmet durumunu kaydeder, böylece birden çok yeniden başlatma gerekirse sürdürebilirsiniz. Hizmet olduğunu algıladığında başka eylem sıraya, böylece bilgisayar önyüklendiğinde sonraki zaman başlatılmaz durumunu sıfırlar ve ardından kendisini kapatır.  
  
### <a name="service-interaction-with-clients"></a>İstemcilerle hizmet etkileşimi  
 .NET Framework sürüm 2. 0'da, yerel görüntü hizmet tek etkileşim komut satırı Ngen.exe aracıdır. Yerel görüntü hizmeti ve hizmetiyle etkileşim kurmak için sıra eylemler için yükleme komut komut satırı aracını kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel görüntü hizmeti](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309)  
 [Yerel görüntü görevi](http://msdn.microsoft.com/en-us/9b1f7590-4e0d-4737-90ef-eaf696932afb)  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Yönetilen Yürütme İşlemi](../../../docs/standard/managed-execution-process.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

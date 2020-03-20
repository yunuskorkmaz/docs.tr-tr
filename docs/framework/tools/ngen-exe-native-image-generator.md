---
title: Ngen.exe (Yerel Görüntü Oluşturucu)
ms.date: 03/30/2017
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
ms.openlocfilehash: 297bc3f9182e76523eda4d4be3112f4d1d7e3fee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75741798"
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (Yerel Görüntü Oluşturucu)

Yerel Görüntü Oluşturucusu (Ngen.exe), yönetilen uygulamaların performansını artıran bir araçtır. Ngen.exe, işlemciye özel derlenmiş makine kodu içeren dosyalar olan yerel görüntüler oluşturur ve bunları yerel bilgisayarın yerel görüntü önbelleğine yükler. Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.

> [!NOTE]
> Ngen.exe, yalnızca .NET Framework'u hedefleyen derlemeler için yerel görüntüleri derler. .NET Core için eşdeğer yerli görüntü üreteci [CrossGen](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md)olduğunu.

.NET Framework 4'te Ngen.exe'de yapılan değişiklikler:

- Ngen.exe artık derlemeleri tam güven ile derler ve kod erişimi güvenliği (CAS) ilkesi artık değerlendirilmez.

- Ngen.exe ile oluşturulan yerel görüntüler artık kısmi güvende çalışan uygulamaların içine yüklenemez.

Ngen.exe'ye .NET Framework 2.0 içinde yapılan değişiklikler:

- Bir derlemeyi yüklemek ayrıca bağımlılıklarını da yükleyerek Ngen.exe'nin sözdizimini basitleştirir.

- Yerel görüntüler artık uygulama etki alanları arasında paylaşılabilir.

- Yeni bir `update`eylem, geçersiz kılınmış görüntüleri yeniden oluşturur.

- Eylemler, görüntüleri oluşturmak ve yüklemek için bilgisayardaki boşta kalma süresini kullanan bir servis tarafından ertelenebilir.

- Görüntü geçersiz kılmanın bazı nedenleri kaldırıldı.

Windows 8'de [Yerel Resim Görevi'ne](#native-image-task)bakın.

Ngen.exe ve yerel görüntü hizmetini kullanma hakkında daha fazla bilgi için [Yerel Resim Hizmeti'ne](#native-image-service)bakın.

> [!NOTE]
> .NET Framework'ün 1.0 ve 1.1 sürümleri için Ngen.exe sözdizimi [Yerel Görüntü Üreteci (Ngen.exe) Eski Sözdizimi'nde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100))bulunabilir.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a>Eylemler

Aşağıdaki tabloda her `action`biri sözdizimini gösterir. `action`Bir , [Bağımsız Değişkenler,](#ArgumentTable)Öncelik [Düzeyleri,](#PriorityTable) [Senaryolar](#ScenarioTable)ve [Config](#ConfigTable) tablolarına bakın tek tek bölümlerinin açıklamaları için. [Seçenekler](#OptionTable) tablosu ve `options` yardım anahtarları açıklar.

|Eylem|Açıklama|
|------------|-----------------|
|`install`[`assemblyName` `assemblyPath`&#124; ] [`scenarios`]`config`[`/queue``:`[`1` `2` [ `3`{ {&#124;&#124;}]]|Bir derleme ve bağımlılıkları için yerel görüntüler oluştur ve görüntüleri yerel görüntü önbelleğine yükle.<br /><br /> `/queue` Belirtilirse, eylem yerel görüntü hizmeti için sıraya alınır. Varsayılan öncelik 3'tür. Öncelik [Düzeyleri](#PriorityTable) tablosuna bakın.|
|`uninstall`[`assemblyName` `assemblyPath`&#124; ] [`scenarios`] [`config`]|Bir derleme ve bağımlılıklarının yerel görüntülerini yerel görüntü önbelleğinden sil.<br /><br /> Tek bir görüntüyü ve bağımlılıklarını kaldırmak için, görüntüyü yüklemek için kullanılan aynı komut satırı bağımsız değişkenlerini kullanın. **Not:**  .NET Framework 4'ten başlayarak, eylem `uninstall` * artık desteklenmez.|
|`update` [`/queue`]|Geçersiz olan yerel görüntüleri güncelleştir.<br /><br /> `/queue` Belirtilirse, güncelleştirmeler yerel görüntü hizmeti için sıraya alınır. Güncelleştirmeler her zaman 3 önceliğindedir ve bilgisayar boşta olduğunda çalışır.|
|`display`[`assemblyName` `assemblyPath`&#124; ]|Bir derleme ve bağımlılıkları için yerel görüntülerin durumunu görüntüle.<br /><br /> Eğer bağımsız değişken sağlanmazsa, yerel görüntü önbelleğindeki her şey görüntülenir.|
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> -veya-<br /><br /> `eqi`[1&#124;2&#124;3]|Sıraya alınan derleme işlerini yürüt.<br /><br /> Eğer bir öncelik belirtilirse, ona eşit veya daha büyük önceliğe sahip derleme işleri yürütülür. Eğer öncelik belirtilmezse, sıraya alınan tüm derleme işleri yürütülür.|
|`queue`{`pause` `continue` &#124; `status`&#124; }|Yerel görüntü hizmetini duraklat, duraklatılan hizmetin devam etmesine izin ver veya hizmetin durumunu sorgula.|

<a name="ArgumentTable"></a>

## <a name="arguments"></a>Bağımsız Değişkenler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`assemblyName`|Derlemenin tam görünen adı. Örneğin, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Not:**  Kısmi bir derleme adı sağlayabilirsiniz, `myAssembly`örneğin `display` `uninstall` , eylemler için. <br /><br /> Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.|
|`assemblyPath`|Derlemenin açık yolu. Tam veya göreli bir yol belirtebilirsiniz.<br /><br /> Eğer bir yol belirtmeden dosya adı belirtilseniz, derleme geçerli dizinde bulunmalıdır.<br /><br /> Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a>Öncelik Düzeyleri

|Öncelik|Açıklama|
|--------------|-----------------|
|`1`|Yerel görüntüler, boşta kalma süresi beklenmeden hemen oluşturulur ve yüklenir.|
|`2`|Yerel görüntüler boşta kalma süresi beklenmeden, ancak tüm 1 öncelikli eylemler (ve bağımlılıkları) tamamlandıktan sonra yüklenir.|
|`3`|Yerel görüntüler, yerel görüntü hizmeti bilgisayarın boşta olduğunu algıladığında yüklenir. [Bkz. Yerel Resim Hizmeti.](#native-image-service)|

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
|`/ExeConfig:` `exePath`|Belirtilen çalıştırılabilir derlemesinin yapılandırmasını kullan.<br /><br /> Ngen.exe, bağımlılıklara bağlarken yükleyici ile aynı kararları almalıdır. Paylaşılan bir bileşen <xref:System.Reflection.Assembly.Load%2A> çalışma zamanında, yöntemi kullanarak yüklendiğinde, uygulamanın yapılandırma dosyası paylaşılan bileşen için yüklenen bağımlılıkları (örneğin, yüklenen bir bağımlılık sürümü) belirler. Anahtar, `/ExeConfig` çalışma zamanında hangi bağımlılıkların yükleneceği konusunda Ngen.exe kılavuzu verir.|
|`/AppBase:` `directoryPath`|Bağımlılıkları bulurken, uygulama tabanı olarak belirtilen dizini kullan.|

<a name="OptionTable"></a>

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/nologo`|Microsoft başlangıç başlığını bastır.|
|`/silent`|Başarı iletilerinin görüntülenmesini bastır.|
|`/verbose`|Hata ayıklama için ayrıntılı bilgi görüntüle. **Not:**  İşletim sistemi sınırlamaları nedeniyle, bu seçenek Windows 98 ve Windows Millennium Edition'da çok fazla ek bilgi görüntülemez.|
|`/help`, `/?`|Geçerli yayın için komut sözdizimi ve seçenekleri görüntüle.|

## <a name="remarks"></a>Açıklamalar

Ngen.exe'yi çalıştırabilmek için yönetici ayrıcalıklarınızın olması gerekir.

> [!CAUTION]
> Ngen.exe'yi tam güvenilir olmayan derlemeler üzerinde çalıştırmayın. .NET Framework 4'ten başlayarak, Ngen.exe derlemeleri tam güvenle derler ve kod erişim güvenliği (CAS) ilkesi artık değerlendirilmez.

.NET Framework 4'ten başlayarak, Ngen.exe ile oluşturulan yerel görüntüler artık kısmi güven le çalışan uygulamalara yüklenebilir. Bunun yerine anlık (JIT) derleyici çağrılır.

Ngen.exe `install` eylem ve tüm bağımlılıkları `assemblyname` için bağımsız değişken tarafından belirtilen derleme için yerel görüntüler oluşturur. Bağlılıklar derleme bildirisindeki referanslar ile belirlenir. Bir bağımlılığı ayrı olarak yüklemeniz gereken tek senaryo, uygulamanın yansımayı kullanarak yüklediği <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> dir, örneğin yöntemi çağırarak.

> [!IMPORTANT]
> <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> Yöntemi yerel görüntülerle kullanmayın. Bu metotla yüklenen bir görüntü, yürütme bağlamındaki diğer derlemeler tarafından kullanılamaz.

Ngen.exe bağımlılıklar için bir sayaç tutar. Örneğin, `MyAssembly.exe` varsayalım `YourAssembly.exe` ve her ikisi de yerel görüntü önbelleğinde `OurDependency.dll`yüklü ve her ikisi de için başvurular var. `MyAssembly.exe` Kaldırılırsa, `OurDependency.dll` kaldırılmamıştır. Yalnızca kaldırıldığında `YourAssembly.exe` kaldırılır.

Eğer genel derleme önbelleğindeki bir derleme için doğal görüntü üretiyorsanız, onun görünür ismini belirtiniz. Bkz. <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.

Ngen.exe'nin ürettiği doğal görüntüler uygulama alanı içerisinde paylaşılabilir. Bu, Ngen.exe'yi derlemelerin uygulama etki alanları arasında paylaşılması gerektiği senaryolarda kullanabileceğiniz anlamına gelir. Alan bağımsızlığını belirtmek için:

- <xref:System.LoaderOptimizationAttribute> Özniteliği uygulamanız için uygulayın.

- Yeni <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> bir uygulama etki alanı için kurulum bilgileri oluştururken özelliği ayarlayın.

Birden çok uygulama alanına aynı derleme yüklediğiniz zaman mutlaka alan-bağımsız kod kullanın. Eğer bir doğal görüntü paylaşılmış alana yüklendikten sonra paylaşılmamış alana yüklenirse, görüntü kullanılamaz.

> [!NOTE]
> Alan-bağımsız kod yüklemesi geri alınamaz (geri döndürülemez) ve performans, özellikle statik elemanlara erişildiği zaman, çok az daha yavaş olabilir.

Bu Açıklamalar bölümünde:

- [Farklı senaryolar için görüntü oluşturma](#Scenarios)

- [Yerel görüntülerin ne zaman kullanılacağını belirleme](#WhenToUse)

  - [Geliştirilmiş bellek kullanımı](#Memory)

  - [Daha hızlı uygulama başlatma](#Startup)

  - [Kullanım la ilgili hususların özeti](#UsageSummary)

- [Montaj temel adreslerinin önemi](#BaseAddresses)

- [Sert bağlama](#HardBinding)

  - [Bağımlılık için bağlayıcı bir ipucu belirtme](#DependencyHint)

  - [Derleme için varsayılan bağlama ipucu belirtme](#AssemblyHint)

- [Ertelenmiş işleme](#Deferred)

- [Yerel görüntüler ve JIT derlemesi](#JITCompilation)

  - [Geçersiz görüntüler](#InvalidImages)

- [Sorun giderme](#Troubleshooting)

  - [Derleme Bağlaması Günlük Görüntüleyici](#Fusion)

  - [JITCompilationStart hata ayıklama asistanı yönetilen](#MDA)

  - [Yerel görüntü oluşturma yı devre dışı bırakma](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a>Farklı senaryolar için görüntü oluşturma

Bir derleme için yerel bir görüntü oluşturduktan sonra, çalışma zamanı bu yerel görüntüyü her derlemeyi çalıştırınca otomatik olarak bulmaya ve kullanmaya çalışır. Kullanım senaryolarına göre, birden fazla görüntüler oluşturulabilir.

Örneğin, hata ayıklama veya profil oluşturma senaryosunda bir derleme çalıştırıyorsanız, çalışma zamanı veya `/Debug` `/Profile` seçenekleriyle oluşturulan yerel bir görüntüyü arar. Eğer eşleşen bir doğal görüntü bulamazsa, çalışma zamanı standart JIT derlemesine geri döner. Yerel görüntüleri ayıklamanın tek `/Debug` yolu, seçeneği olan yerel bir görüntü oluşturmaktır.

Eylem `uninstall` senaryoları da tanır, böylece tüm senaryoları veya yalnızca seçili senaryoları kaldırabilirsiniz.

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a>Yerel görüntülerin ne zaman kullanılacağını belirleme

Yerel görüntüler iki alanda performans iyileştirmesi sağlayabilir: daha iyi bellek kullanımı ve daha az başlangıç zamanı.

> [!NOTE]
> Yerel görüntülerin performansı; kod ve veri erişim desenleri, modül sınırları dışına yapılan çağrı sayısı ve diğer uygulamalar tarafından şimdiye kadar yüklenmiş olan bağımlılık sayısı gibi analizi zorlaştıran çeşitli etkenlere bağlıdır. Yerel görüntülerin uygulamanıza yararlı olup olmadığını belirlemenin tek yolu, anahtar dağıtım senaryolarınızda yapacağını dikkatli performans ölçümleridir.

<a name="Memory"></a>

### <a name="improved-memory-use"></a>Geliştirilmiş bellek kullanımı

Yerel görüntüler kod işlemler arasında paylaşıldığında bellek kullanımını önemli ölçüde iyileştirebilirler. Yerel görüntüler Windows PE dosyalarıdır, yani bir .dll dosyasının tek kopyası birden çok işlem tarafından paylaşılabilir; buna karşılık, JIT derleyicisi tarafından üretilen yerel kod özel bellekte tutulur ve paylaşılamaz.

Terminal hizmetleri altında çalışan uygulamalar da paylaşılan kod sayfalarından yararlanabilir.

Ek olarak, JIT derleyicisini yüklememek her uygulama örneği için sabit bir miktarda bellek kazandırır.

<a name="Startup"></a>

### <a name="faster-application-startup"></a>Daha hızlı uygulama başlatma

Derlemeleri Ngen.exe ile ön derlemek bazı uygulamalar için başlangıç süresini iyileştirebilir. Genel olarak, uygulamalar bileşen derlemelerini paylaştığında kazanç olabilir, çünkü ilk uygulama başladıktan sonra paylaşılan bileşenler sonraki uygulamalar için zaten yüklü olur. Uygulamadaki tüm derlemelerin sabit diskten yüklenmesini gerektiren soğuk başlangıç yerel görüntülerden pek fayda kazanmaz, çünkü sabit disk erişim süresi baskın olur.

Sabit bağlama başlatma süresini etkileyebilir, çünkü ana uygulama derlemesine sabit bağlı olan tüm resimler aynı anda yüklenmelidirler.

> [!NOTE]
> .NET Framework 3.5 Service Pack 1'den önce, genel montaj önbelleğine paylaşılan, güçlü adlandırılmış bileşenleri koymalısınız, çünkü yükleyici, genel montaj önbelleğinde olmayan güçlü adlandırılmış derlemeler üzerinde ekstra doğrulama yapar ve etkin bir şekilde ortadan kaldırmalısınız yerel görüntüler kullanılarak kazanılan başlangıç süresi herhangi bir iyileşme. .NET Framework 3.5 SP1'de tanıtılan optimizasyonlar ek doğrulamayı kaldırdı.

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a>Kullanım la ilgili hususların özeti

Aşağıdaki genel önemli noktalar ve uygulama önemli noktaları uygulamanız için yerel görüntüleri değerlendirmek üzere çaba harcayıp harcamamaya karar vermenize yardımcı olabilir:

- Yerel görüntüler MSIL'den daha hızlı yüklenir çünkü JIT derlemesi ve tür güvenliği doğrulaması gibi pek çok başlangıç aktivitesine gereksinimi ortadan kaldırırlar.

- Yerel görüntüler daha küçük ilk çalışma kümesi gerektirirler çünkü JIT derleyicisine gerek yoktur.

- Yerel görüntüler işlemler arasında kod paylaşımını etkinleştirir.

- Yerel görüntüler MSIL derlemelerinden daha fazla sabit disk alanı gerektirir ve üretmek için büyük miktarda zaman gerektirebilir.

- Yerel görüntüler bakılmalıdır.

  - Orijinal derleme veya bağımlılıklarından biri değiştiğinde görüntüler yeniden oluşturulmalıdır.

  - Tek bir derleme farklı uygulamalarda ya da farklı senaryolarda kullanılması için birden çok yerel görüntüye ihtiyaç duyabilir. Örneğin, iki uygulamadaki yapılandırma bilgileri aynı bağımlı derleme için farklı bağlama kararlarına neden olabilir.

  - Yerel görüntüler bir yönetici, yani Yöneticiler grubu içindeki bir Windows hesabı, tarafından üretilmelidir.

Bu genel önemli noktalara ek olarak, yerel görüntülerin bir performans kazancı sağlayıp sağlamayacağını belirlerken uygulamanızın doğası da göz önüne alınmalıdır:

- Eğer uygulamanız pek çok paylaşılan bileşen kullanan bir ortamda çalışıyorsa, yerel görüntüler bileşenlerin birden çok işlem tarafından paylaşılmasını sağlar.

- Eğer uygulamanız birden çok uygulama alanı kullanıyorsa, yerel görüntüler alanlar arasında kod sayfalarının paylaşılmasını sağlar.

    > [!NOTE]
    > .NET Framework 1.0 ve 1.1 sürümlerinde, yerel görüntüler uygulama etki alanları arasında paylaşılamaz. Bu, sürüm 2.0 ve sonrasında geçerli değildir.

- Eğer uygulamanız Terminal Server altında çalışacaksa, yerel görüntüler kod sayfalarının paylaşılmasını sağlar.

- Büyük uygulamalar yerel görüntülere derlemekten genellikle yarar görür. Küçük uygulamalar genellikle yarar görmez.

- Uzun süre çalışan uygulamalarda, çalışma zamanı JIT derlemesi yerel görüntülerden biraz daha iyi çalışır. (Sabit bağlama bu performans farkını belirli bir ölçüde azaltabilir.)

<a name="BaseAddresses"></a>

## <a name="importance-of-assembly-base-addresses"></a>Montaj temel adreslerinin önemi

Yerel görüntüler Windows PE dosyaları olduğu için, diğer çalıştırılabilir dosyalardaki aynı yeniden temellendirme sorunlarıyla karşılaşırlar. Eğer sıkı bağlama kullanılırsa, yeniden konumlandırmanın performans maliyeti daha da belirgin olur.

Bir yerel görüntü için temel adresi ayarlamak için, derlemenin temel adresini ayarlama amacıyla derleyicinizin uygun seçeneğini kullanın. Ngen.exe yerel görüntü için bu temel adresi kullanır.

> [!NOTE]
> Yerel görüntüler, oluşturuldukları yönetilen derlemelerden daha büyüktür. Bu daha büyük boyutlara izin vermek için temel adresler hesaplanmalıdır.

Bir yerel görüntünün tercih edilen temel adresini görüntülemek için dumpbin.exe gibi bir araç kullanabilirsiniz.

<a name="HardBinding"></a>

## <a name="hard-binding"></a>Sert bağlama

Sıkı bağlama doğal görüntüler için birim zamanda yapılan işi artırır ve çalışma seti alanını azaltır. Sıkı bağlamanın dezavantajı, bir derleme yüklendiğinde o derlemeye sıkı bağlı olan tüm görüntülerin de yüklenmesinin gerekmesidir. Bu büyük bir uygulama için başlatma zamanını önemli derecede artırabilir.

Sıkı bağlama, uygulamanızın performansının kritik olduğu senaryolarda yüklenen bağımlılıklar için uygundur. Herhangi bir doğal görüntü kullanımında, sıkı bağlanmanın uygulamanızın performansını arttırıp arttırmadığını öğrenmenin tek yolu dikkatli(hassas) performans ölçümleridir.

Ve <xref:System.Runtime.CompilerServices.DependencyAttribute> <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> öznitelikleri Ngen.exe için sert bağlama ipuçları sağlamak için izin verir.

> [!NOTE]
> Bu değerler Ngen.exe'ye teknik/tavsiyelerdir, komutlar değillerdir. Bunları kullanmak sıkı bağlamayı garanti etmez. Bu değerlerin anlamları ileri yayınlarda değişebilir.

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a>Bağımlılık için bağlayıcı bir ipucu belirtme

Belirli <xref:System.Runtime.CompilerServices.DependencyAttribute> bir bağımlılığın yüklenme olasılığını belirtmek için derlemeye uygulayın. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>sabit bağlamanın uygun <xref:System.Runtime.CompilerServices.LoadHint.Default> olduğunu gösterir, bağımlılık için varsayılan ın <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> kullanılması gerektiğini gösterir ve sabit bağlamanın uygun olmadığını gösterir.

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

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a>Derleme için varsayılan bağlama ipucu belirtme

Varsayılan bağlama ipuçları, yalnızca onlara bağlılığı olan herhangi bir uygulama tarafından anında ve sıkça kullanılacak olan derlemeler için gereklidir. Sert <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> bağlama <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> nın kullanılması gerektiğini belirtmek için bu tür derlemelere birlikte uygulayın.

> [!NOTE]
> .dll derlemelerine <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> başvurmak için bir neden yoktur, çünkü özniteliği hiç uygulamamak gibi başka <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> bir değerle uygulamak aynı etkiye sahiptir.

Microsoft, <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> .NET Framework'de mscorlib.dll gibi çok az sayıda derleme için sabit bağlamanın varsayılan olduğunu belirtmek için kullanır.

<a name="Deferred"></a>

## <a name="deferred-processing"></a>Ertelenmiş işleme

Çok büyük bir uygulama için yerel görüntü oluşturmak uzun bir süre alabilir. Benzer şekilde, paylaşılan bir bileşene veya bilgisayar seçeneklerine yapılan değişiklikler pek çok yerel görüntünün güncellenmesini gerektirebilir. Ve `install` `update` eylemler, `/queue` yerel görüntü hizmeti tarafından ertelenmiş yürütme için işlemi sıraya belirten bir seçenek vardır. Buna ek olarak, Ngen.exe vardır `queue` ve `executeQueuedItems` hizmet üzerinde bazı kontrol sağlayan eylemler. Daha fazla bilgi için [Bkz. Yerel Resim Hizmeti.](#native-image-service)

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a>Yerel görüntüler ve JIT derlemesi

Eğer Ngen.exe assembly içerisinde oluşturamayacağı herhangi bir metotla karşılaşırsa, onları doğal görüntü (özgün görüntü) içerisine dahil etmez. Çalışma zamanı bu derlemeyi çalıştırdığı zaman, doğal görüntünün içerisine dahil edilmeyen metotlar için JIT derleme işlemine döner

Ek olarak, derleme yükseltildiyse veya görüntü herhangi bir sebeple geçersiz kılındıysa yerel görüntüler kullanılmaz.

<a name="InvalidImages"></a>

### <a name="invalid-images"></a>Geçersiz görüntüler

Ngen.exe'yi bir derlemenin yerel görüntüsünü oluşturmak için kullandığınızda; çıktı, belirlediğin komut satırı seçeneklerine ve bilgisayarınızdaki belirli ayarlara bağlıdır. Bu ayarlar aşağıdakileri içerir:

- .NET Framework sürümü.

- Değişiklik Windows 9x ailesinden Windows NT ailesine ise işletim sisteminin sürümü.

- Derlemenin tam kimliği (yeniden derleme kimliği değiştirir).

- Derlemenin başvurduğu tüm derlemelerin tam kimliği (yeniden derleme kimliği değiştirir).

- Güvenlik etkenleri.

Ngen.exe bir doğal görüntü oluşturduğu zaman bu bilgiyi kaydeder. Bir derlemeyi çalıştırdığınız zaman, çalışma zamanı bilgisayarın o anki çevresine uyan seçenekler ve ayarlarla oluşturulmuş olan doğal görüntüyü arar. Çalışma zamanı eğer eşleşen bir doğal görüntü bulamazsa, derlemeyi JIT ile derleme yoluna gider. Bilgisayarın ayarlarına ve çevresine uygulanan aşağıdaki değişiklikler doğal görüntünün geçersiz olmasına sebep olur:

- .NET Framework sürümü.

     Eğer .NET framework'e güncelleme uygularsanız, Ngen.exe kullanarak oluşturduğunuz bütün imajlar geçersiz sayılır. Bu nedenle, .NET Framework'ün tüm `Ngen Update` güncelleştirmeleri, tüm yerel görüntülerin yeniden oluşturulduğundan emin olmak için komutu çalıştırın. .NET framework kuracağı .Net framework kütüphaneleri için yeni görüntüleri otomatik olarak oluşturur.

- Değişiklik Windows 9x ailesinden Windows NT ailesine ise işletim sisteminin sürümü.

     Örneğin, bilgisayarda çalışan işletim sisteminin sürümü Windows 98'den Windows XP'ye değişirse, yerel görüntü önbelleğinde depolanan tüm yerel görüntüler geçersiz olur. Ancak, işletim sistemi Windows 2000'den Windows XP'ye değişirse, görüntüler geçersiz kılınır.

- Derlemenin kesin kimliği.

     Eğer derlemeyi yeniden derlerseniz, derlemeye karşılık gelen doğal görüntü geçersiz olur.

- Derlemenin referans ettiği bütün derlemelerin tam kimliği.

     Eğer yönetilmiş bir derlemeyi güncellerseniz, o derlemeye direk ya da dolaylı yoldan bağlı olan bütün doğal görüntüler geçersiz olur ve yeniden oluşturulması gerekir. Bu hem normal tercihleri/ayarları hem de sıkı-bağlama bağlılıklarını içerir. Bir yazılım güncelleştirmesi uygulandığında, yükleme `Ngen Update` programı tüm bağımlı yerel görüntülerin yeniden oluşturulduğundan emin olmak için bir komut yürütmelidir.

- Güvenlik etkenleri.

     Önceden yetkilendirilmiş bir derlemenin izinlerini kısıtlamak için makina güvenlik politikasında değişiklik yapmak, o derleme için önceden derlenmiş olan doğal imajın geçersiz olmasına sebep olabilir

     Ortak dil çalışma zamanının kod erişim güvenliğini nasıl yönettiği ve izinlerin nasıl kullanılacağı hakkında ayrıntılı bilgi için [Kod Erişim Güvenliği'ne](../misc/code-access-security.md)bakın.

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki sorun giderme konuları, JIT derleyicisinin bir yöntem derlemeye ne zaman başlayacağını belirlemek için hangi yerel görüntülerin kullanıldığını ve uygulamanız tarafından kullanılamayacağını görmenizi sağlar ve belirtilen yerel görüntü derlemesini nasıl devre dışı kakabileceğinizi gösterir Yöntemler.

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a>Derleme Bağlaması Günlük Görüntüleyici

Yerel görüntülerin uygulamanız tarafından kullanıldığını doğrulamak için [Fuslogvw.exe (Derleme Bağlama Günlüğü Görüntüleyici)](fuslogvw-exe-assembly-binding-log-viewer.md)kullanabilirsiniz. Bağlama günlüğü görüntüleyici penceresinde, **Günlük Kategorileri** kutusunda **Yerel Görseller'i** seçin. Fuslogvw.exe bir doğal imajın neden reddedildiği hakkında bilgi sağlar.

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>JITCompilationStart hata ayıklama asistanı yönetilen

JIT derleyicisinin bir işlevi derlemeye ne zaman başlayacağını belirlemek için [jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) yönetilen hata ayıklama yardımcısını (MDA) kullanabilirsiniz.

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a>Yerel görüntü oluşturma yı devre dışı bırakma

Bazı durumlarda, NGen.exe belirli bir yöntem için yerel bir görüntü oluşturmakta güçlük çekebilir veya yöntemin daha sonra yerel bir görüntüye derlenmiş jit olmasını tercih edebilirsiniz. Bu durumda, NGen.exe'nin `System.Runtime.BypassNGenAttribute` belirli bir yöntem için yerel bir görüntü oluşturmasını önlemek için özniteliği kullanabilirsiniz. Öznitelik, kodunu yerel görüntüye eklemek istemediğiniz her yönteme ayrı ayrı uygulanmalıdır. NGen.exe özniteliği tanır ve ilgili yöntem için yerel görüntüde kod oluşturmaz.

Ancak, `BypassNGenAttribute` .NET Framework Class Kitaplığı'nda bir tür olarak tanımlanmamıştır. Kodunuzdaki özniteliği tüketmek için önce aşağıdaki gibi tanımlamanız gerekir:

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

Daha sonra özniteliği yöntem başına uygulayabilirsiniz. Aşağıdaki örnek, Yerel Görüntü Oluşturucusu'na `ExampleClass.ToJITCompile` yöntem için yerel bir görüntü oluşturmaması gerektiğini bildirir.

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a>Örnekler

Aşağıdaki `ClientApp.exe`komut, geçerli dizinde bulunan için yerel bir görüntü oluşturur ve görüntüyü yerel görüntü önbelleğine yükler. Derleme için bir yapılandırma dosyası varsa, onu Ngen.exe kullanır. Buna ek olarak, başvuruyapan `ClientApp.exe` tüm .dll dosyaları için yerel görüntüler oluşturulur.

```console
ngen install ClientApp.exe
```

Ngen.exe ile yüklenmiş bir resim, bir kök olarak da adlandırılır. Kök, bir uygulama veya paylaşılan bir bileşen olabilir.

Aşağıdaki komut, belirtilen yol `MyAssembly.exe` ile yerel bir görüntü oluşturur.

```console
ngen install c:\myfiles\MyAssembly.exe
```

Derlemeler ve bağımlılıklarını belirlerken Ngen.exe ortak dil çalışma zamanı tarafından kullanılan aynı algılama mantığını kullanır. Varsayılan olarak, içeren `ClientApp.exe` dizin uygulama temel dizini olarak kullanılır ve tüm derleme sondalama bu dizinde başlar. `/AppBase` Bu davranışı seçeneği kullanarak geçersiz kılabilirsiniz.

> [!NOTE]
> Bu, uygulama temel dizininin geçerli dizin olarak ayarlandığı .NET Framework 1.0 ve 1.1 sürümlerindeki Ngen.exe davranışından farklıdır.

Bir derleme, örneğin <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi kullanarak bir .dll dosyası yüklerse, başvuru olmadan bir bağımlılık olabilir. Uygulama derlemesi `/ExeConfig` için yapılandırma bilgilerini kullanarak, bu tür bir .dll dosyası için yerel bir görüntü oluşturabilirsiniz. Aşağıdaki komut, `MyLib.dll,` `MyApp.exe`yapılandırma bilgilerini kullanmak için yerel bir görüntü oluşturur.

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Uygulamayı kaldırdığınızda, bu şekilde yüklenen derlemeler kaldırılmaz.

Bir bağımlılık kaldırmak için yüklemek için kullanılan aynı komut satırı seçeneklerini kullanın. Aşağıdaki komut önceki `MyLib.dll` örnekten kaldırını yükler.

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Genel bütünleştirilmiş kod önbelleğindeki bir derleme için yerel görüntü oluşturmak için, derlemenin görünen adını kullanın. Örnek:

```console
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

NGen.exe yüklediğiniz her senaryo için ayrı bir görüntü kümesi oluşturur. Örneğin, aşağıdaki komutlar normal işlemler için tamamen yerel görüntü kümesi, hata ayıklama için farklı bir küme ve belirleme için üçüncüyü yükler:

```console
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a>Yerel Görüntü Önbelleğini Görüntüleme

Yerel görüntüler önbelleğe yüklendikten sonra, Ngen.exe kullanılarak görüntülenebilirler. Aşağıdaki komut yerel görüntü belleğindeki tüm yerel görüntüleri görüntüler.

```console
ngen display
```

Eylem, `display` önce tüm kök derlemelerini listeler ve ardından bilgisayardaki tüm yerel görüntülerin bir listesini listeler.

Yalnızca bir derlemenin bilgilerini görüntülemek için o derlemenin basit adını kullanın. Aşağıdaki komut, yerel görüntü önbelleğinde kısmi ad, `MyAssembly`bağımlılıkları ve bağımlılığı olan tüm kökleri `MyAssembly`eşleşen tüm yerel görüntüleri görüntüler:

```console
ngen display MyAssembly
```

Hangi köklerin paylaşılan bileşen derlemeye bağlı olduğunu bilmek, `update` paylaşılan bileşen yükseltildikten sonra eylemin etkisini ölçmede yararlıdır.

Eğer bir derlemenin dosya uzantısını belirtirseniz, ya yolu belirtmeniz ya da Ngen.exe'yi derlemeyi içeren dizinden yürütmeniz gerekir:

```console
ngen display c:\myApps\MyAssembly.exe
```

Aşağıdaki komut, yerel görüntü önbelleğinde adı `MyAssembly` ve sürüm 1.0.0.0.0 ile tüm yerel görüntüleri görüntüler.

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a>Görüntüleri Güncelleştirme

Görüntüler genellikle paylaşılan bir bileşen yükseltildikten sonra güncelleştirilir. Değiştirilen veya bağımlılıkları değişen tüm yerel görüntüleri güncelleştirmek `update` için, eylemi bağımsız değişken olmadan kullanın.

```console
ngen update
```

Tüm görüntüleri güncelleştirmek uzun süren bir işlem olabilir. Güncelleştirmeleri yerel görüntü hizmeti tarafından yürütme için `/queue` seçeneği kullanarak sıraya alabilirsiniz. `/queue` Seçenek ve yükleme öncelikleri hakkında daha fazla bilgi için Yerel Resim [Hizmeti'ne](#native-image-service)bakın.

```console
ngen update /queue
```

### <a name="uninstalling-images"></a>Görüntüleri Kaldırma

Ngen.exe bağımlılıkların bir listesini tutar, yani paylaşılan bileşenler yalnızca onlara bağlı olan tüm derlemeler kaldırıldığında kaldırılır. Ek olarak kök olarak yüklenmiş ortak bileşenler silinmez.

Aşağıdaki komut kök `ClientApp.exe`için tüm senaryoları yükler:

```console
ngen uninstall ClientApp
```

Eylem `uninstall` belirli senaryoları kaldırmak için kullanılabilir. Aşağıdaki komut, aşağıdakiler için `ClientApp.exe`tüm hata ayıklama senaryolarını kaldırıyor:

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> Senaryoları `/debug` kaldırmak, hem de `/profile``/debug.`

Aşağıdaki komut, aşağıdakilerin belirli bir sürümü `ClientApp.exe`için tüm senaryoları kaldırz:

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

Aşağıdaki komutlar, bu derleme `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` için tüm senaryoları kaldırın veya bu derleme için hata ayıklama senaryosu:

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

`install` Eylemde olduğu gibi, uzantı sağlamak için de Ngen.exe'nin derlemeyi içeren dizinden yürütülmesi veya tam bir yol belirtilmesi gerekiyor.

Yerel görüntü hizmetiyle ilgili örnekler [için](#native-image-service)bkz.

## <a name="native-image-task"></a>Yerel Görüntü Görevi

Yerel görüntü görevi, yerel görüntüleri oluşturan ve koruyan bir Windows görevidir. Yerel görüntü görevi, desteklenen senaryolar için otomatik olarak yerel görüntüleri oluşturur ve geri alır. Ayrıca, yükleyicilerin ertelenmiş bir zamanda yerel görüntüler oluşturmak ve güncellemek için [Ngen.exe (Yerel Görüntü Oluşturucusu)](ngen-exe-native-image-generator.md) kullanmalarını sağlar.

Yerel görüntü görevi, her mimariyi hedefleyen uygulamalar için derlemeye izin vermek için, bilgisayarda desteklenen her CPU mimarisi için bir kez kaydedilir:

|Görev adı|32 bit bilgisayar|64 bit bilgisayar|
|---------------|----------------------|----------------------|
|NET Çerçeve NGEN v4.0.30319|Evet|Evet|
|NET Çerçeve NGEN v4.0.30319 64|Hayır|Evet|

Yerel görüntü görevi,.NET Framework 4.5 ve sonraki sürümlerde, Windows 8 veya sonraki sürümlerde kullanılabilir. Windows'un önceki sürümlerinde ,.NET Framework [Yerel Görüntü Hizmeti'ni](#native-image-service)kullanır.

### <a name="task-lifetime"></a>Görev Ömrü

Genel olarak, Windows Görev Zamanlayıcısı, bilgisayar boşta yken her gece yerel görüntü görevini başlatır. Görev, uygulama yükleyicileri tarafından sıralanan ertelenmiş çalışmayı, ertelenmiş yerel görüntü güncelleştirme isteklerini ve otomatik görüntü oluşturmayı denetler. Görev bekleyen iş öğelerini tamamlar ve sonra kapanır. Görev çalışırken bilgisayar boşta kalmayı durdurursa, görev durur.

Ayrıca, görev zamanlayıcısı UI aracılığıyla veya NGen.exe'ye manuel aramalar yoluyla yerel resim görevini el ile başlatabilirsiniz. Görev bu yöntemlerden biri aracılığıyla başlatılırsa, bilgisayar artık boşta olmadığında çalışmaya devam edecektir. NGen.exe kullanılarak el ile oluşturulan görüntüler, uygulama yükleyicileri için öngörülebilir davranışı etkinleştirmek için öncelike göre belirlenir.

## <a name="native-image-service"></a>Yerel Görüntü Hizmeti

Yerel görüntü hizmeti, yerel görüntüleri oluşturan ve koruyan bir Windows hizmetidir. Yerel görüntü hizmeti, geliştiricinin yerel görüntülerin yüklenmesini ve güncellenmesini bilgisayarın boşta olduğu dönemlere ertelemesine olanak tanır.

Normalde, yerel görüntü hizmeti yükleme programı (yükleyici) tarafından bir uygulama veya güncelleştirme için başlatılır. Öncelik 3 eylemleri için, hizmet bilgisayarda boşta kalma süresi sırasında yürütür. Hizmet durumunu kaydeder ve gerekirse birden çok yeniden başlatma yoluyla devam edebilir. Birden çok görüntü derlemesi sıraya eklenebilir.

Hizmet ayrıca manuel Ngen.exe komutu ile etkileşime girsin. El ile komutlar arka plan etkinliğine göre önceliklidir.

> [!NOTE]
> Windows Vista'da, yerel görüntü hizmeti için görüntülenen ad "Microsoft.NET Framework NGEN v2.0.50727_X86" veya "Microsoft.NET Framework NGEN v2.0.50727_X64" dir. Microsoft Windows'un önceki tüm sürümlerinde adı ".NET Runtime Optimizasyon Hizmeti v2.0.50727_X86" veya ".NET Runtime Optimizasyon Hizmeti v2.0.50727_X64" olarak adlandırılır.

### <a name="launching-deferred-operations"></a>Ertelenmiş İşlemleri başlatma

Yükleme ye veya yükseltmeye başlamadan önce, hizmeti duraklatma önerilir. Bu, yükleyici dosyaları kopyalarken veya derlemeleri genel derleme önbelleğine koyarken hizmetin yürütmemesini sağlar. Aşağıdaki Ngen.exe komut satırı hizmeti duraklatabilir:

```console
ngen queue pause
```

Ertelenen tüm işlemler sıraya girdiğinde, aşağıdaki komut hizmetin devam etmesine izin verir:

```console
ngen queue continue
```

Yeni bir uygulama yüklerken veya paylaşılan bir bileşeni güncellerken `/queue` yerel görüntü `install` `update` oluşturmayı ertelemek için, seçeneği veya eylemleri kullanın. Aşağıdaki Ngen.exe komut satırları paylaşılan bir bileşen için yerel bir görüntü yükler ve etkilenmiş olabilecek tüm köklerin güncelleştirmesini gerçekleştirir:

```console
ngen install MyComponent /queue
ngen update /queue
```

Eylem, `update` yalnızca kullananlar `MyComponent`değil, geçersiz kılınan tüm yerel görüntüleri yeniden oluşturur.

Uygulamanız birçok kökten oluşuyorsa, ertelenen eylemlerin önceliğini denetleyebilirsiniz. Aşağıdaki komutlar üç kök yükleme sıraya. `Assembly1`boşta kalma süresini beklemeden önce yüklenir. `Assembly2`boşta kalma süresini beklemeden de yüklenir, ancak tüm öncelik 1 eylemleri tamamlandıktan sonra. `Assembly3`hizmet bilgisayarın boşta olduğunu algıladığında yüklenir.

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

Kuyruğa giren eylemleri `executeQueuedItems` eylemi kullanarak eşzamanlı olarak oluşmaya zorlayabilirsiniz. İsteğe bağlı önceliği sağlıyorsanız, bu eylem yalnızca eşit veya daha düşük önceliğe sahip sıralanmış eylemleri etkiler. Varsayılan öncelik 3'tür, bu nedenle aşağıdaki Ngen.exe komutu sıralı tüm eylemleri hemen işler ve tamamlanana kadar dönmez:

```console
ngen executeQueuedItems
```

Senkron komutlar Ngen.exe tarafından yürütülür ve yerel görüntü hizmetini kullanmaz. Yerel görüntü hizmeti çalışırken Ngen.exe kullanarak eylemleri gerçekleştirebilirsiniz.

### <a name="service-shutdown"></a>Hizmet Kapatma

`/queue` Seçeneği içeren bir Ngen.exe komutunun yürütülmesi yle başlatıldıktan sonra, tüm eylemler tamamlanana kadar hizmet arka planda çalışır. Hizmet, gerektiğinde birden çok yeniden başlatma yoluyla devam edebilmek için durumunu kaydeder. Hizmet, başka eylem sırası olmadığını algıladığında, bilgisayarın bir sonraki önyüklemesini yeniden başlatmaması için durumunu sıfırlar ve ardından kendini kapatır.

### <a name="service-interaction-with-clients"></a>Müşterilerle Hizmet Etkileşimi

.NET Framework sürüm 2.0'da, yerel görüntü hizmetiyle tek etkileşim komut satırı aracı Ngen.exe'dir. Yükleme komut dosyalarındaki komut satırı aracını, yerel görüntü hizmeti için eylemleri sıraya koymak ve hizmetle etkileşimde bulunmak için kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Yönetilen Yürütme İşlemi](../../standard/managed-execution-process.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)

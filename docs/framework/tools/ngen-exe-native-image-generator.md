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
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741798"
---
# <a name="ngenexe-native-image-generator"></a>Ngen.exe (Yerel Görüntü Oluşturucu)

Yerel Görüntü Oluşturucusu (Ngen.exe), yönetilen uygulamaların performansını artıran bir araçtır. Ngen.exe, işlemciye özel derlenmiş makine kodu içeren dosyalar olan yerel görüntüler oluşturur ve bunları yerel bilgisayarın yerel görüntü önbelleğine yükler. Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.

> [!NOTE]
> Ngen. exe yalnızca .NET Framework hedefleyen derlemeler için yerel görüntüleri derler. .NET Core için eşdeğer yerel görüntü Oluşturucu, [çapraz genel](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md)' tir.

.NET Framework 4 ' te Ngen. exe ' ye yapılan değişiklikler:

- Ngen.exe artık derlemeleri tam güven ile derler ve kod erişimi güvenliği (CAS) ilkesi artık değerlendirilmez.

- Ngen.exe ile oluşturulan yerel görüntüler artık kısmi güvende çalışan uygulamaların içine yüklenemez.

Ngen.exe'ye .NET Framework 2.0 içinde yapılan değişiklikler:

- Bir derlemeyi yüklemek ayrıca bağımlılıklarını da yükleyerek Ngen.exe'nin sözdizimini basitleştirir.

- Yerel görüntüler artık uygulama etki alanları arasında paylaşılabilir.

- Yeni bir eylem `update`, geçersiz kılınan görüntüleri yeniden oluşturur.

- Eylemler, görüntüleri oluşturmak ve yüklemek için bilgisayardaki boşta kalma süresini kullanan bir servis tarafından ertelenebilir.

- Görüntü geçersiz kılmanın bazı nedenleri kaldırıldı.

Windows 8 ' de, [yerel görüntü görevi](#native-image-task)' ne bakın.

Ngen. exe ve yerel görüntü hizmetini kullanma hakkında daha fazla bilgi için bkz. [Native Image Service](#native-image-service).

> [!NOTE]
> .NET Framework 1,0 ve 1,1 sürümleri için Ngen. exe sözdizimi [Yerel Görüntü Oluşturucu (Ngen. exe) eski sözdiziminde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100))bulunabilir.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a>Eylemler

Aşağıdaki tabloda her `action`söz dizimi gösterilmektedir. Bir `action`bireysel bölümlerinin açıklamaları için bkz. [bağımsız değişkenler](#ArgumentTable), [Öncelik düzeyleri](#PriorityTable), [senaryolar](#ScenarioTable)ve [yapılandırma](#ConfigTable) tabloları. [Seçenekler](#OptionTable) tablosu `options` ve yardım anahtarlarını açıklar.

|Eylem|Açıklama|
|------------|-----------------|
|`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]|Bir derleme ve bağımlılıkları için yerel görüntüler oluştur ve görüntüleri yerel görüntü önbelleğine yükle.<br /><br /> `/queue` belirtilirse, eylem yerel görüntü hizmeti için sıraya alınır. Varsayılan öncelik 3'tür. [Öncelik düzeyleri](#PriorityTable) tablosuna bakın.|
|`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]|Bir derleme ve bağımlılıklarının yerel görüntülerini yerel görüntü önbelleğinden sil.<br /><br /> Tek bir görüntüyü ve bağımlılıklarını kaldırmak için, görüntüyü yüklemek için kullanılan aynı komut satırı bağımsız değişkenlerini kullanın. **Note:**  .NET Framework 4 ' te başlayarak, `uninstall` * eylemi artık desteklenmiyor.|
|`update` [`/queue`]|Geçersiz olan yerel görüntüleri güncelleştir.<br /><br /> `/queue` belirtilirse, güncelleştirmeler yerel görüntü hizmeti için sıraya alınır. Güncelleştirmeler her zaman 3 önceliğindedir ve bilgisayar boşta olduğunda çalışır.|
|`display` [`assemblyName` &#124; `assemblyPath`]|Bir derleme ve bağımlılıkları için yerel görüntülerin durumunu görüntüle.<br /><br /> Eğer bağımsız değişken sağlanmazsa, yerel görüntü önbelleğindeki her şey görüntülenir.|
|`executeQueuedItems` [<code>1&#124;2&#124;3</code>]<br /><br /> veya<br /><br /> `eqi` [1&#124;2&#124;3]|Sıraya alınan derleme işlerini yürüt.<br /><br /> Eğer bir öncelik belirtilirse, ona eşit veya daha büyük önceliğe sahip derleme işleri yürütülür. Eğer öncelik belirtilmezse, sıraya alınan tüm derleme işleri yürütülür.|
|`queue` {`pause` &#124; `continue` &#124; `status`}|Yerel görüntü hizmetini duraklat, duraklatılan hizmetin devam etmesine izin ver veya hizmetin durumunu sorgula.|

<a name="ArgumentTable"></a>

## <a name="arguments"></a>Arguments

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`assemblyName`|Derlemenin tam görünen adı. Örneğin: `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`. **Note:**  `display` ve `uninstall` eylemleri için `myAssembly`gibi kısmi bir derleme adı sağlayabilirsiniz. <br /><br /> Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.|
|`assemblyPath`|Derlemenin açık yolu. Tam veya göreli bir yol belirtebilirsiniz.<br /><br /> Eğer bir yol belirtmeden dosya adı belirtilseniz, derleme geçerli dizinde bulunmalıdır.<br /><br /> Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a>Öncelik Düzeyleri

|Öncelik|Açıklama|
|--------------|-----------------|
|`1`|Yerel görüntüler, boşta kalma süresi beklenmeden hemen oluşturulur ve yüklenir.|
|`2`|Yerel görüntüler boşta kalma süresi beklenmeden, ancak tüm 1 öncelikli eylemler (ve bağımlılıkları) tamamlandıktan sonra yüklenir.|
|`3`|Yerel görüntüler, yerel görüntü hizmeti bilgisayarın boşta olduğunu algıladığında yüklenir. Bkz. [yerel görüntü hizmeti](#native-image-service).|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a>Senaryolar

|Senaryo|Açıklama|
|--------------|-----------------|
|`/Debug`|Bir hata ayıklayıcı altında kullanılabilen yerel görüntüler oluştur.|
|`/Profile`|Bir profil oluşturucu altında kullanılabilen yerel görüntüler oluştur.|
|`/NoDependencies`|Belirli senaryo seçeneklerinin gerektirdiği en az sayıda yerel görüntü oluştur.|

<a name="ConfigTable"></a>

## <a name="config"></a>Yapılandırma

|Yapılandırma|Açıklama|
|-------------------|-----------------|
|`/ExeConfig:` `exePath`|Belirtilen çalıştırılabilir derlemesinin yapılandırmasını kullan.<br /><br /> Ngen.exe, bağımlılıklara bağlarken yükleyici ile aynı kararları almalıdır. Çalışma zamanında paylaşılan bir bileşen yüklendiğinde <xref:System.Reflection.Assembly.Load%2A> yöntemi kullanılarak, uygulamanın yapılandırma dosyası paylaşılan bileşen için yüklenen bağımlılıkları belirler — örneğin, yüklenen bir bağımlılığın sürümü. `/ExeConfig` anahtarı, çalışma zamanında hangi bağımlılıkların yüklenebileceğine ilişkin Ngen. exe kılavuzu sağlar.|
|`/AppBase:` `directoryPath`|Bağımlılıkları bulurken, uygulama tabanı olarak belirtilen dizini kullan.|

<a name="OptionTable"></a>

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/nologo`|Microsoft başlangıç başlığını bastır.|
|`/silent`|Başarı iletilerinin görüntülenmesini bastır.|
|`/verbose`|Hata ayıklama için ayrıntılı bilgi görüntüle. **Note:**  İşletim sistemi sınırlamaları nedeniyle, bu seçenek Windows 98 ve Windows Millennium Edition hakkında daha fazla bilgi göstermez.|
|`/help`, `/?`|Geçerli yayın için komut sözdizimi ve seçenekleri görüntüle.|

## <a name="remarks"></a>Açıklamalar

Ngen.exe'yi çalıştırabilmek için yönetici ayrıcalıklarınızın olması gerekir.

> [!CAUTION]
> Ngen.exe'yi tam güvenilir olmayan derlemeler üzerinde çalıştırmayın. .NET Framework 4 ' te başlayarak, Ngen. exe derlemeleri tam güvenle derler ve kod erişim güvenliği (CAS) ilkesi artık değerlendirilmez.

.NET Framework 4 ' te başlayarak, Ngen. exe ile oluşturulan yerel görüntüler artık kısmi güvende çalışan uygulamalara yüklenemez. Bunun yerine anlık (JIT) derleyici çağrılır.

Ngen. exe, `install` eylemi ve tüm bağımlılıkları için `assemblyname` bağımsız değişkeni tarafından belirtilen derleme için yerel görüntüler oluşturur. Bağlılıklar derleme bildirisindeki referanslar ile belirlenir. Bir bağımlılığı ayrı olarak yüklemeniz gereken tek senaryo, örneğin <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemini çağırarak, uygulamanın yansıma kullanarak yüklediğinde.

> [!IMPORTANT]
> <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemini yerel görüntülerle kullanmayın. Bu metotla yüklenen bir görüntü, yürütme bağlamındaki diğer derlemeler tarafından kullanılamaz.

Ngen.exe bağımlılıklar için bir sayaç tutar. Örneğin, `MyAssembly.exe` ve `YourAssembly.exe` her ikisinin de yerel görüntü önbelleğinde yüklü olduğunu ve her ikisinin de `OurDependency.dll`başvurularına sahip olduğunu varsayalım. `MyAssembly.exe` kaldırılırsa, `OurDependency.dll` kaldırılmaz. Yalnızca `YourAssembly.exe` de kaldırıldığında kaldırılır.

Eğer genel derleme önbelleğindeki bir derleme için doğal görüntü üretiyorsanız, onun görünür ismini belirtiniz. Bkz. <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.

Ngen.exe'nin ürettiği doğal görüntüler uygulama alanı içerisinde paylaşılabilir. Bu, Ngen.exe'yi derlemelerin uygulama etki alanları arasında paylaşılması gerektiği senaryolarda kullanabileceğiniz anlamına gelir. Alan bağımsızlığını belirtmek için:

- Uygulamanıza <xref:System.LoaderOptimizationAttribute> özniteliğini uygulayın.

- Yeni bir uygulama etki alanı için kurulum bilgilerini oluştururken <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> özelliğini ayarlayın.

Birden çok uygulama alanına aynı derleme yüklediğiniz zaman mutlaka alan-bağımsız kod kullanın. Eğer bir doğal görüntü paylaşılmış alana yüklendikten sonra paylaşılmamış alana yüklenirse, görüntü kullanılamaz.

> [!NOTE]
> Alan-bağımsız kod yüklemesi geri alınamaz (geri döndürülemez) ve performans, özellikle statik elemanlara erişildiği zaman, çok az daha yavaş olabilir.

Bu açıklamalar bölümünde:

- [Farklı senaryolar için görüntü oluşturma](#Scenarios)

- [Yerel görüntülerin ne zaman kullanılacağını belirleme](#WhenToUse)

  - [İyileştirilmiş bellek kullanımı](#Memory)

  - [Daha hızlı uygulama başlatma](#Startup)

  - [Kullanım konularının Özeti](#UsageSummary)

- [Derleme temel adreslerinin önemi](#BaseAddresses)

- [Sabit bağlama](#HardBinding)

  - [Bağımlılık için bağlama ipucu belirtme](#DependencyHint)

  - [Derleme için varsayılan bağlama ipucu belirtme](#AssemblyHint)

- [Ertelenmiş işleme](#Deferred)

- [Yerel görüntüler ve JıT derlemesi](#JITCompilation)

  - [Geçersiz görüntüler](#InvalidImages)

- [Sorun giderme](#Troubleshooting)

  - [Bütünleştirilmiş kod bağlama günlük Görüntüleyici](#Fusion)

  - [Jıtcompilationstart yönetilen hata ayıklama Yardımcısı](#MDA)

  - [Yerel görüntü oluşturmayı geri alma](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a>Farklı senaryolar için görüntü oluşturma

Bir derleme için yerel görüntü oluşturduktan sonra, çalışma zamanı derlemeyi her çalıştırdığında otomatik olarak bu yerel görüntüyü bulmayı ve kullanmayı dener. Kullanım senaryolarına göre, birden fazla görüntüler oluşturulabilir.

Örneğin, bir derlemeyi hata ayıklama veya profil oluşturma senaryosunda çalıştırırsanız, çalışma zamanı `/Debug` veya `/Profile` seçenekleriyle oluşturulan yerel bir görüntüyü arar. Eğer eşleşen bir doğal görüntü bulamazsa, çalışma zamanı standart JIT derlemesine geri döner. Yerel görüntülerde hata ayıklamanın tek yolu, `/Debug` seçeneği ile yerel görüntü oluşturmaktır.

`uninstall` eylemi senaryoları da tanır, böylece tüm senaryoları veya yalnızca seçili senaryoları kaldırabilirsiniz.

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a>Yerel görüntülerin ne zaman kullanılacağını belirleme

Yerel görüntüler iki alanda performans iyileştirmesi sağlayabilir: daha iyi bellek kullanımı ve daha az başlangıç zamanı.

> [!NOTE]
> Yerel görüntülerin performansı; kod ve veri erişim desenleri, modül sınırları dışına yapılan çağrı sayısı ve diğer uygulamalar tarafından şimdiye kadar yüklenmiş olan bağımlılık sayısı gibi analizi zorlaştıran çeşitli etkenlere bağlıdır. Yerel görüntülerin uygulamanıza yararlı olup olmadığını belirlemenin tek yolu, anahtar dağıtım senaryolarınızda yapacağını dikkatli performans ölçümleridir.

<a name="Memory"></a>

### <a name="improved-memory-use"></a>İyileştirilmiş bellek kullanımı

Yerel görüntüler kod işlemler arasında paylaşıldığında bellek kullanımını önemli ölçüde iyileştirebilirler. Yerel görüntüler Windows PE dosyalarıdır, yani bir .dll dosyasının tek kopyası birden çok işlem tarafından paylaşılabilir; buna karşılık, JIT derleyicisi tarafından üretilen yerel kod özel bellekte tutulur ve paylaşılamaz.

Terminal hizmetleri altında çalışan uygulamalar da paylaşılan kod sayfalarından yararlanabilir.

Ek olarak, JIT derleyicisini yüklememek her uygulama örneği için sabit bir miktarda bellek kazandırır.

<a name="Startup"></a>

### <a name="faster-application-startup"></a>Daha hızlı uygulama başlatma

Derlemeleri Ngen.exe ile ön derlemek bazı uygulamalar için başlangıç süresini iyileştirebilir. Genel olarak, uygulamalar bileşen derlemelerini paylaştığında kazanç olabilir, çünkü ilk uygulama başladıktan sonra paylaşılan bileşenler sonraki uygulamalar için zaten yüklü olur. Uygulamadaki tüm derlemelerin sabit diskten yüklenmesini gerektiren soğuk başlangıç yerel görüntülerden pek fayda kazanmaz, çünkü sabit disk erişim süresi baskın olur.

Sabit bağlama başlatma süresini etkileyebilir, çünkü ana uygulama derlemesine sabit bağlı olan tüm resimler aynı anda yüklenmelidirler.

> [!NOTE]
> .NET Framework 3,5 hizmet paketi 1 ' den önce, yükleyici, genel derleme önbelleğinde olmayan, güçlü adlandırılmış derlemelerde ek doğrulama gerçekleştirdiğinden, paylaşılan ve tanımlayıcı adlandırılmış bileşenleri genel derleme önbelleğine yerleştirmeniz gerekir. Yerel görüntüler kullanılarak elde edilen başlatma sırasında tüm geliştirme. .NET Framework 3,5 SP1'DE tanıtılan iyileştirmeler, ek doğrulamayı kaldırdı.

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a>Kullanım konularının Özeti

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

## <a name="importance-of-assembly-base-addresses"></a>Derleme temel adreslerinin önemi

Yerel görüntüler Windows PE dosyaları olduğu için, diğer çalıştırılabilir dosyalardaki aynı yeniden temellendirme sorunlarıyla karşılaşırlar. Eğer sıkı bağlama kullanılırsa, yeniden konumlandırmanın performans maliyeti daha da belirgin olur.

Bir yerel görüntü için temel adresi ayarlamak için, derlemenin temel adresini ayarlama amacıyla derleyicinizin uygun seçeneğini kullanın. Ngen.exe yerel görüntü için bu temel adresi kullanır.

> [!NOTE]
> Yerel görüntüler, oluşturuldukları yönetilen derlemelerden daha büyüktür. Bu daha büyük boyutlara izin vermek için temel adresler hesaplanmalıdır.

Bir yerel görüntünün tercih edilen temel adresini görüntülemek için dumpbin.exe gibi bir araç kullanabilirsiniz.

<a name="HardBinding"></a>

## <a name="hard-binding"></a>Sabit bağlama

Sıkı bağlama doğal görüntüler için birim zamanda yapılan işi artırır ve çalışma seti alanını azaltır. Sıkı bağlamanın dezavantajı, bir derleme yüklendiğinde o derlemeye sıkı bağlı olan tüm görüntülerin de yüklenmesinin gerekmesidir. Bu büyük bir uygulama için başlatma zamanını önemli derecede artırabilir.

Sıkı bağlama, uygulamanızın performansının kritik olduğu senaryolarda yüklenen bağımlılıklar için uygundur. Herhangi bir doğal görüntü kullanımında, sıkı bağlanmanın uygulamanızın performansını arttırıp arttırmadığını öğrenmenin tek yolu dikkatli(hassas) performans ölçümleridir.

<xref:System.Runtime.CompilerServices.DependencyAttribute> ve <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> öznitelikleri, Ngen. exe ' ye sabit bağlama ipuçları sağlamanıza olanak tanır.

> [!NOTE]
> Bu değerler Ngen.exe'ye teknik/tavsiyelerdir, komutlar değillerdir. Bunları kullanmak sıkı bağlamayı garanti etmez. Bu değerlerin anlamları ileri yayınlarda değişebilir.

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a>Bağımlılık için bağlama ipucu belirtme

Belirtilen bağımlılığın yükleneolasılığını göstermek için <xref:System.Runtime.CompilerServices.DependencyAttribute> bir derlemeye uygulayın. <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>, sabit bağlamanın uygun olduğunu gösterir <xref:System.Runtime.CompilerServices.LoadHint.Default>, bağımlılığın varsayılan olarak kullanılması gerektiğini belirtir ve <xref:System.Runtime.CompilerServices.LoadHint.Sometimes>, sabit bağlamanın uygun olmadığını gösterir.

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

Varsayılan bağlama ipuçları, yalnızca onlara bağlılığı olan herhangi bir uygulama tarafından anında ve sıkça kullanılacak olan derlemeler için gereklidir. Sabit bağlamanın kullanılması gerektiğini belirtmek için bu tür derlemelere <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> uygulayın.

> [!NOTE]
> Bu kategoriye uymayan. dll derlemelerine <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> uygulamak için bir neden yoktur, çünkü özniteliği <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> dışındaki herhangi bir değerle uygulamak, özniteliği hiçbir şekilde uygulamakla aynı etkiye sahiptir.

Microsoft <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute>, .NET Framework (mscorlib. dll gibi) çok az sayıda derlemede, sabit bağlamanın varsayılan olduğunu belirtmek için kullanır.

<a name="Deferred"></a>

## <a name="deferred-processing"></a>Ertelenmiş işleme

Çok büyük bir uygulama için yerel görüntü oluşturmak uzun bir süre alabilir. Benzer şekilde, paylaşılan bir bileşene veya bilgisayar seçeneklerine yapılan değişiklikler pek çok yerel görüntünün güncellenmesini gerektirebilir. `install` ve `update` eylemleri, yerel görüntü hizmeti tarafından ertelenmiş yürütme işlemini sıraya alan bir `/queue` seçeneği vardır. Ayrıca, Ngen. exe ' nin, hizmet üzerinde bazı denetimler sağlayan `queue` ve `executeQueuedItems` eylemleri vardır. Daha fazla bilgi için bkz. [yerel görüntü hizmeti](#native-image-service).

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a>Yerel görüntüler ve JıT derlemesi

Eğer Ngen.exe assembly içerisinde oluşturamayacağı herhangi bir metotla karşılaşırsa, onları doğal görüntü (özgün görüntü) içerisine dahil etmez. Çalışma zamanı bu derlemeyi çalıştırdığı zaman, doğal görüntünün içerisine dahil edilmeyen metotlar için JIT derleme işlemine döner

Ek olarak, derleme yükseltildiyse veya görüntü herhangi bir sebeple geçersiz kılındıysa yerel görüntüler kullanılmaz.

<a name="InvalidImages"></a>

### <a name="invalid-images"></a>Geçersiz görüntüler

Ngen.exe'yi bir derlemenin yerel görüntüsünü oluşturmak için kullandığınızda; çıktı, belirlediğin komut satırı seçeneklerine ve bilgisayarınızdaki belirli ayarlara bağlıdır. Bu ayarlar aşağıdakileri içerir:

- .NET Framework sürümü.

- Değişiklik, Windows 9x ailesinden Windows NT ailesine ise işletim sisteminin sürümü.

- Derlemenin tam kimliği (yeniden derleme kimliği değiştirir).

- Derlemenin başvurduğu tüm derlemelerin tam kimliği (yeniden derleme kimliği değiştirir).

- Güvenlik etkenleri.

Ngen.exe bir doğal görüntü oluşturduğu zaman bu bilgiyi kaydeder. Bir derlemeyi çalıştırdığınız zaman, çalışma zamanı bilgisayarın o anki çevresine uyan seçenekler ve ayarlarla oluşturulmuş olan doğal görüntüyü arar. Çalışma zamanı eğer eşleşen bir doğal görüntü bulamazsa, derlemeyi JIT ile derleme yoluna gider. Bilgisayarın ayarlarına ve çevresine uygulanan aşağıdaki değişiklikler doğal görüntünün geçersiz olmasına sebep olur:

- .NET Framework sürümü.

     Eğer .NET framework'e güncelleme uygularsanız, Ngen.exe kullanarak oluşturduğunuz bütün imajlar geçersiz sayılır. Bu nedenle, tüm yerel görüntülerin yeniden üretildiğinden emin olmak için .NET Framework tüm güncelleştirmeleri `Ngen Update` komutunu yürütür. .NET framework kuracağı .Net framework kütüphaneleri için yeni görüntüleri otomatik olarak oluşturur.

- Değişiklik, Windows 9x ailesinden Windows NT ailesine ise işletim sisteminin sürümü.

     Örneğin, bir bilgisayarda çalışan işletim sisteminin sürümü Windows 98 ' den Windows XP 'ye değişirse, yerel görüntü önbelleğinde depolanan tüm yerel görüntüler geçersiz olur. Ancak, işletim sistemi Windows 2000 ' den Windows XP 'ye değişirse, görüntüler geçersiz kılınmaz.

- Derlemenin kesin kimliği.

     Eğer derlemeyi yeniden derlerseniz, derlemeye karşılık gelen doğal görüntü geçersiz olur.

- Derlemenin referans ettiği bütün derlemelerin tam kimliği.

     Eğer yönetilmiş bir derlemeyi güncellerseniz, o derlemeye direk ya da dolaylı yoldan bağlı olan bütün doğal görüntüler geçersiz olur ve yeniden oluşturulması gerekir. Bu hem normal tercihleri/ayarları hem de sıkı-bağlama bağlılıklarını içerir. Her bir yazılım güncelleştirmesi uygulandığında, yükleme programının tüm bağımlı yerel görüntülerin yeniden oluşturulmasını sağlamak için bir `Ngen Update` komutu yürütmesi gerekir.

- Güvenlik etkenleri.

     Önceden yetkilendirilmiş bir derlemenin izinlerini kısıtlamak için makina güvenlik politikasında değişiklik yapmak, o derleme için önceden derlenmiş olan doğal imajın geçersiz olmasına sebep olabilir

     Ortak dil çalışma zamanının kod erişim güvenliğini nasıl yönettiği ve izinlerin nasıl kullanılacağı hakkında ayrıntılı bilgi için bkz. [kod erişim güvenliği](../misc/code-access-security.md).

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki sorun giderme konuları, hangi yerel görüntülerin kullanıldığını ve uygulamanız tarafından kullanılamayacağını görmenizi, JıT derleyicisinin bir yöntemi derlemeye başladığı zaman belirlenmesini ve belirtilen yerel görüntü derlemesini nasıl devre dışı yapılacağını belirlemenizi sağlar Yöntem.

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a>Derleme Bağlaması Günlük Görüntüleyici

Yerel görüntülerin uygulamanız tarafından kullanıldığını onaylamak için, [Fuslogvw. exe (bütünleştirilmiş kod bağlama günlük Görüntüleyici)](fuslogvw-exe-assembly-binding-log-viewer.md)kullanabilirsiniz. Bağlama günlüğü Görüntüleyicisi penceresindeki **günlük kategorileri** kutusunda **Yerel görüntüler** ' i seçin. Fuslogvw.exe bir doğal imajın neden reddedildiği hakkında bilgi sağlar.

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a>Jıtcompilationstart yönetilen hata ayıklama Yardımcısı

JıT derleyicisinin bir işlevi derlemeye ne zaman başlayacağını anlamak için, [Jıtcompilationstart](../debug-trace-profile/jitcompilationstart-mda.md) Managed hata ayıklama Yardımcısı 'Nı (MDA) kullanabilirsiniz.

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a>Yerel görüntü oluşturmayı geri alma

Bazı durumlarda, NGen. exe belirli bir yöntem için yerel görüntü üretmekte zorluk gösterebilir veya metodun yerel bir görüntüye derlenmek yerine JıT derlenmesini tercih edebilirsiniz. Bu durumda, NGen. exe ' nin belirli bir yöntem için yerel görüntü oluşturmasını engellemek üzere `System.Runtime.BypassNGenAttribute` özniteliğini kullanabilirsiniz. Özniteliği, kodu yerel görüntüye eklemek istemediğiniz her bir yönteme ayrı ayrı uygulanmalıdır. NGen. exe, özniteliğini tanır ve ilgili yöntem için yerel görüntüde kod oluşturmaz.

Ancak, `BypassNGenAttribute` .NET Framework sınıf kitaplığındaki bir tür olarak tanımlanmadığını unutmayın. Kodunuzda özniteliği tüketmek için, önce bunu aşağıdaki gibi tanımlamanız gerekir:

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

Sonra özniteliği yöntem başına temelinde uygulayabilirsiniz. Aşağıdaki örnek yerel görüntü oluşturucuya `ExampleClass.ToJITCompile` yöntemi için yerel görüntü oluşturmaması gerektiğini söyler.

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a>Örnekler

Aşağıdaki komut, geçerli dizinde bulunan `ClientApp.exe`için yerel görüntü oluşturur ve görüntüyü yerel görüntü önbelleğine yüklenir. Derleme için bir yapılandırma dosyası varsa, onu Ngen.exe kullanır. Bunlara ek olarak, `ClientApp.exe` başvuran tüm. dll dosyaları için yerel görüntüler oluşturulur.

```console
ngen install ClientApp.exe
```

Ngen.exe ile yüklenmiş bir resim, bir kök olarak da adlandırılır. Kök, bir uygulama veya paylaşılan bir bileşen olabilir.

Aşağıdaki komut, `MyAssembly.exe` için belirtilen yola sahip bir yerel görüntü oluşturur.

```console
ngen install c:\myfiles\MyAssembly.exe
```

Derlemeler ve bağımlılıklarını belirlerken Ngen.exe ortak dil çalışma zamanı tarafından kullanılan aynı algılama mantığını kullanır. Varsayılan olarak, `ClientApp.exe` içeren dizin, uygulama temel dizini olarak kullanılır ve tüm derleme yoklama bu dizinde başlar. `/AppBase` seçeneğini kullanarak bu davranışı geçersiz kılabilirsiniz.

> [!NOTE]
> Bu, uygulama temel dizininin geçerli dizin olarak ayarlandığı .NET Framework 1.0 ve 1.1 sürümlerindeki Ngen.exe davranışından farklıdır.

Bir derlemenin başvuru olmadan bağımlılığı olabilir, örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemini kullanarak bir. dll dosyası yüklerse. Bu tür bir. dll dosyası için, `/ExeConfig` seçeneği ile uygulama derlemesinin yapılandırma bilgilerini kullanarak yerel görüntü oluşturabilirsiniz. Aşağıdaki komut, `MyApp.exe`yapılandırma bilgilerini kullanarak `MyLib.dll,` için yerel görüntü oluşturur.

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Uygulamayı kaldırdığınızda, bu şekilde yüklenen derlemeler kaldırılmaz.

Bir bağımlılık kaldırmak için yüklemek için kullanılan aynı komut satırı seçeneklerini kullanın. Aşağıdaki komut, önceki örnekteki `MyLib.dll` kaldırır.

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

Genel bütünleştirilmiş kod önbelleğindeki bir derleme için yerel görüntü oluşturmak için, derlemenin görünen adını kullanın. Örneğin:

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

`display` eylem, önce tüm kök derlemeleri, ardından bilgisayardaki tüm yerel görüntülerin listesini listeler.

Yalnızca bir derlemenin bilgilerini görüntülemek için o derlemenin basit adını kullanın. Aşağıdaki komut, yerel görüntü önbelleğindeki tüm yerel görüntüleri, Kısmi ad `MyAssembly`, bağımlılıklarıyla ve `MyAssembly`bağımlılığı olan tüm köklerle aynı şekilde görüntüler:

```console
ngen display MyAssembly
```

Paylaşılan bir bileşen derlemesine hangi köklerin bağımlı olduğunu bilmek, paylaşılan bileşen yükseltildikten sonra `update` eyleminin etkisini ölçmek içinde yararlı olur.

Eğer bir derlemenin dosya uzantısını belirtirseniz, ya yolu belirtmeniz ya da Ngen.exe'yi derlemeyi içeren dizinden yürütmeniz gerekir:

```console
ngen display c:\myApps\MyAssembly.exe
```

Aşağıdaki komut yerel görüntü önbelleğindeki tüm yerel görüntüleri ad `MyAssembly` ve 1.0.0.0 sürümüyle birlikte görüntüler.

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a>Görüntüleri Güncelleştirme

Görüntüler genellikle paylaşılan bir bileşen yükseltildikten sonra güncelleştirilir. Değiştirilen veya bağımlılıkları değişmiş olan tüm yerel görüntüleri güncelleştirmek için `update` eylemini bağımsız değişken olmadan kullanın.

```console
ngen update
```

Tüm görüntüleri güncelleştirmek uzun süren bir işlem olabilir. `/queue` seçeneğini kullanarak yerel görüntü hizmeti tarafından yürütme için güncelleştirmeleri sıraya alabilirsiniz. `/queue` seçeneği ve yükleme öncelikleri hakkında daha fazla bilgi için bkz. [Native Image Service](#native-image-service).

```console
ngen update /queue
```

### <a name="uninstalling-images"></a>Görüntüleri Kaldırma

Ngen.exe bağımlılıkların bir listesini tutar, yani paylaşılan bileşenler yalnızca onlara bağlı olan tüm derlemeler kaldırıldığında kaldırılır. Ek olarak kök olarak yüklenmiş ortak bileşenler silinmez.

Aşağıdaki komut, kök `ClientApp.exe`tüm senaryoları kaldırır:

```console
ngen uninstall ClientApp
```

`uninstall` eylemi belirli senaryoları kaldırmak için kullanılabilir. Aşağıdaki komut `ClientApp.exe`için tüm hata ayıklama senaryolarını kaldırır:

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> `/debug` senaryolarını kaldırmak, hem `/profile` hem de içeren bir senaryoyu kaldırmaz `/debug.`

Aşağıdaki komut `ClientApp.exe`belirli bir sürümü için tüm senaryoları kaldırır:

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

Aşağıdaki komutlar, `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` için tüm senaryoları veya yalnızca ilgili bütünleştirilmiş kod hata ayıklama senaryosunu kaldırır:

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

`install` eyleminde olduğu gibi, bir uzantı sağlamak, derlemeyi içeren dizinden Ngen. exe ' nin yürütülmesini veya tam yol belirtilmesini gerektirir.

Yerel görüntü hizmetiyle ilgili örnekler için bkz. [Native Image Service](#native-image-service).

## <a name="native-image-task"></a>Yerel Görüntü Görevi

Yerel görüntü görevi, yerel görüntüler üreten ve tutan bir Windows görevidir. Yerel görüntü görevi, desteklenen senaryolar için otomatik olarak yerel görüntüler oluşturur ve geri kazanır. Ayrıca, yükleyicilerin [Ngen. exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md) kullanarak yerel görüntüleri ertelenmiş bir sürede oluşturmasını ve güncelleştirmesini de sağlar.

Yerel görüntü görevi, her bir mimariyi hedefleyen uygulamalar için derlemeye izin vermek üzere bir bilgisayarda desteklenen her CPU mimarisi için bir kez kaydedilir:

|Görev adı|32 bit bilgisayar|64 bit bilgisayar|
|---------------|----------------------|----------------------|
|NET Framework NGEN v 4.0.30319|Evet|Evet|
|NET Framework NGEN v 4.0.30319 64|Hayır|Evet|

Yerel görüntü görevi, Windows 8 veya sonraki sürümlerde çalışırken .NET Framework 4,5 ve sonraki sürümlerinde kullanılabilir. Windows 'un önceki sürümlerinde, .NET Framework [yerel görüntü hizmetini](#native-image-service)kullanır.

### <a name="task-lifetime"></a>Görev ömrü

Genellikle, Windows Görev Zamanlayıcı bilgisayar boştayken her gece yerel görüntü görevini başlatır. Görev, uygulama yükleyicileri tarafından kuyruğa alınan ertelenmiş işleri, ertelenmiş yerel görüntü güncelleştirme isteklerini ve herhangi bir otomatik görüntü oluşturmayı denetler. Görev, bekleyen iş öğelerini tamamlar ve sonra kapatır. Görev çalışırken bilgisayar boşta çalışmayı durduktan sonra görev durmaktadır.

Yerel görüntü görevini Görev Zamanlayıcı kullanıcı arabiriminden el ile veya NGen. exe ' ye elle yapılan çağrılar aracılığıyla da başlatabilirsiniz. Görev bu yöntemlerden birini kullanarak başlatılırsa, bilgisayar artık boşta olmadığında çalışmaya devam eder. NGen. exe kullanılarak elle oluşturulan görüntüler, uygulama yükleyicilerine yönelik öngörülebilir davranışı etkinleştirmek için önceliklendirilir.

## <a name="native-image-service"></a>Yerel Görüntü Hizmeti

Yerel görüntü hizmeti, yerel görüntüleri üreten ve tutan bir Windows hizmetidir. Yerel görüntü hizmeti, geliştiricinin yerel görüntülerin yükleme ve güncelleştirme işlemini bilgisayar boştayken dönemlere erteetmesine olanak tanır.

Normal olarak, yerel görüntü hizmeti bir uygulama veya güncelleştirme için yükleme programı (Yükleyici) tarafından başlatılır. Öncelik 3 işlemleri için, hizmet bilgisayarda boşta kalma süresi boyunca yürütülür. Hizmet, durumunu kaydeder ve gerekirse birden çok yeniden başlatma işlemi için devam etme yeteneğine sahiptir. Birden çok görüntü derlemesi kuyruğa alınabilir.

Hizmet el ile Ngen. exe komutuyla da etkileşime girer. El ile gerçekleştirilen komutların arka plan etkinliğine göre önceliği vardır.

> [!NOTE]
> Windows Vista 'da, yerel görüntü hizmeti için görünen ad "Microsoft.NET Framework NGEN v 2.0.50727_X86" veya "Microsoft.NET Framework NGEN v 2.0.50727_X64" olur. Microsoft Windows 'un önceki tüm sürümlerinde, ad ".NET Runtime Optimization Service v 2.0.50727_X86" veya ".NET Runtime Optimizasyon hizmeti v 2.0.50727_X64" olur.

### <a name="launching-deferred-operations"></a>Ertelenmiş Işlemler başlatılıyor

Yükleme veya yükseltmeye başlamadan önce, hizmeti duraklatma önerilir. Bu, yükleyici dosyaları kopyalarken veya derlemeleri genel bütünleştirilmiş kod önbelleğine yerleştirirken hizmetin yürütülmemesini sağlar. Aşağıdaki Ngen. exe komut satırı Hizmeti duraklatır:

```console
ngen queue pause
```

Tüm ertelenmiş işlemler sıraya alınmışsa aşağıdaki komut hizmetin sürdürülmesine izin verir:

```console
ngen queue continue
```

Yeni bir uygulama yüklerken veya paylaşılan bir bileşeni güncelleştirirken yerel görüntü üretimini ertelemek için `install` veya `update` eylemleriyle `/queue` seçeneğini kullanın. Aşağıdaki Ngen. exe komut satırları paylaşılan bir bileşen için yerel bir görüntü yükler ve etkilenen tüm köklerin güncelleştirilmesini gerçekleştirir:

```console
ngen install MyComponent /queue
ngen update /queue
```

`update` eylemi, yalnızca `MyComponent`kullanan olanları değil, geçersiz kılınan tüm yerel görüntüleri yeniden oluşturur.

Uygulamanız birçok kökten oluşuyorsa, ertelenmiş eylemlerin önceliğini kontrol edebilirsiniz. Aşağıdaki komutlar, üç kök yüklemeyi sıraya alma. `Assembly1`, boşta kalma süresi beklememeden önce yüklenir. `Assembly2`, boşta kalma süresi beklememeden da yüklenir, ancak tüm öncelik 1 eylemleri tamamlandıktan sonra. `Assembly3`, hizmet bilgisayarın boşta olduğunu algıladığında yüklenir.

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

Sıraya alınmış eylemleri `executeQueuedItems` eylemini kullanarak zaman uyumlu olarak gerçekleşecek şekilde zorlayabilirsiniz. İsteğe bağlı öncelik sağlarsanız, bu eylem yalnızca eşit veya daha düşük önceliğe sahip olan sıraya alınmış eylemleri etkiler. Varsayılan öncelik 3 ' dir, bu nedenle aşağıdaki Ngen. exe komutu sıraya alınan tüm eylemleri hemen işler ve tamamlanana kadar döndürmez:

```console
ngen executeQueuedItems
```

Zaman uyumlu komutlar Ngen. exe tarafından yürütülür ve yerel görüntü hizmetini kullanmaz. Yerel görüntü hizmeti çalışırken Ngen. exe ' yi kullanarak eylemleri çalıştırabilirsiniz.

### <a name="service-shutdown"></a>Hizmet kapatılıyor

`/queue` seçeneğini içeren bir Ngen. exe komutunun yürütülmesi tarafından başlatıldıktan sonra, tüm eylemler tamamlanana kadar hizmet arka planda çalışır. Hizmet, gerektiğinde birden çok yeniden başlatma işleminin devam edebilmesi için durumunu kaydeder. Hizmet sıraya alınmış daha fazla eylem olmadığını algıladığında, bilgisayarın bir sonraki önyüklenilişinde yeniden başlatmaması için durumunu sıfırlar ve sonra kendisini kapatır.

### <a name="service-interaction-with-clients"></a>Istemcilerle hizmet etkileşimi

.NET Framework sürüm 2,0 ' de, yerel görüntü hizmeti ile tek etkileşim, Ngen. exe komut satırı aracıdır. Yerel görüntü hizmeti için eylemleri sıraya almak ve hizmetle etkileşimde bulunmak için yükleme betiklerinde komut satırı aracını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Yönetilen Yürütme İşlemi](../../standard/managed-execution-process.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)

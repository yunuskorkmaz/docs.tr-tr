---
description: Gelişmiş C# derleyici seçenekleri. Bu seçenekler Gelişmiş senaryolarda kullanılır.
title: C# derleyici seçenekleri-Gelişmiş senaryolar
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- BaseAddress compiler option [C#]
- ChecksumAlgorithm compiler option [C#]
- CodePage compiler option [C#]
- Utf8Output compiler option [C#]
- MainEntryPoint compiler option [C#]
- GenerateFullPaths compiler option [C#]
- FileAlignment compiler option [C#]
- PathMap compiler option [C#]
- PdbFile compiler option [C#]
- ErrorEndLocation compiler option [C#]
- NoStandardLib compiler option [C#]
- PreferredUILang compiler option [C#]
- SubsystemVersion compiler option [C#]
- AdditionalLibPaths compiler option [C#]
- ErrorReport compiler option [C#]
- ApplicationConfiguration compiler option [C#]
- ModuleAssemblyName compiler option [C#]
ms.openlocfilehash: fd65cea6a5524425de5061a2d930181fcd081090
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482957"
---
# <a name="advanced-c-compiler-options"></a>Gelişmiş C# derleyici seçenekleri

Aşağıdaki seçenekler gelişmiş senaryoları destekler. Yeni MSBuild sözdizimi **kalın** olarak gösterilir. Eski `csc.exe` sözdizimi içinde gösterilir `code style` .

- **MainEntryPoint**, **StartupObject**  /  `-main` : giriş noktasını içeren türü belirtin.
- **Pdbdosya**  /  `-pdb` : hata ayıklama bilgi dosyası adını belirtin.
- **Pathmap**  /  `-pathmap` : derleyici tarafından çıkış kaynak yolu adları için bir eşleme belirtin.
- **Errorreport**  /  `-errorreport` : iç derleyici hatalarının nasıl işleneceğini belirtin.
- **ApplicationConfiguration**  /  `-appconfig` : derleme bağlama ayarlarını içeren bir uygulama yapılandırma dosyası belirtin.
- **Adtionalyobpaths**  /  `-lib` : başvuruların içinde aranacağı ek dizinleri belirtin.
- **GenerateFullPaths**  /  `-fullpath` : Derleyici tam nitelikli yollar oluşturur.
- **PreferredUILang**  /  `-preferreduilang` : tercih edilen çıkış dili adını belirtin.
- **BaseAddress**  /  `-baseaddress` : oluşturulacak kitaplığın temel adresini belirtin.
- **Checksumalgorithm**  /  `-checksumalgorithm` : PDB 'de depolanan kaynak dosyası sağlama toplamını hesaplamak için algoritmayı belirtin.
- **Kod sayfası**  /  `-codepage` : kaynak dosyalar açılırken kullanılacak kod sayfasını belirtin.
- **Utf8output**  /  `-utf8output` : Derleyici iletilerini UTF-8 kodlamasında çıktı.
- Dosya **hizalaması**  /  `-filealign` : çıkış dosyası bölümleri için kullanılan hizalamayı belirtin.
- **Errorendlocation**  /  `-errorendlocation` : her hatanın bitiş konumunun çıkış satırı ve sütunu.
- **NoStandardLib**  /  `-nostdlib` : standart kitaplık *mscorlib.dll* başvurulmayın.
- **Subsystemversion**  /  `-subsystemversion` : Bu derlemenin alt sistem sürümünü belirtin.
- **Moduleassemblyname**  /  `-moduleassemblyname` : Bu modülün bir parçası olacağı derlemenin adı.

## <a name="mainentrypoint-or-startupobject"></a>MainEntryPoint veya StartupObject

Bu seçenek, birden fazla sınıf bir yöntemi içeriyorsa programa giriş noktasını içeren sınıfı belirtir `Main` .

```xml
<StartupObject>MyNamespace.Program</StartupObject>
```

veya

```xml
<MainEntryPoint>MyNamespace.Program</MainEntryPoint>
```

, `Program` Yöntemini içeren türdür `Main` . Belirtilen sınıf adı tam olarak nitelenmiş olmalıdır; sınıfını içeren tam ad alanını ve ardından sınıf adını içermelidir. Örneğin, `Main` yöntemi `Program` `MyApplication.Core` ad alanındaki sınıfının içindeyse, derleyici seçeneğinin olması gerekir `-main:MyApplication.Core.Program` . Derlemeniz bir yöntemi olan birden çok tür içeriyorsa [`Main`](../../programming-guide/main-and-command-args/index.md) , hangi türün yöntemi içerdiğini belirtebilirsiniz `Main` .

> [!NOTE]
> Bu seçenek, bu proje bir veya daha fazla yöntem içerse bile, [en üst düzey deyimler](../../programming-guide/main-and-command-args/top-level-statements.md)içeren bir proje için kullanılamaz `Main` .

## <a name="pdbfile"></a>Pdbdosya

**Pdbdosya** derleyici seçeneği, hata ayıklama sembolleri dosyasının adını ve konumunu belirtir.  `filename`Değer, hata ayıklama sembolleri dosyasının adını ve konumunu belirtir.  

```xml
<PdbFile>filename</PdbFile>
```

[**DEBUGTYPE**](code-generation.md#debugtype)belirttiğinizde, derleyici aynı dizinde bir *. pdb* dosyası oluşturur ve bu dosya derleyicinin çıkış dosyasını (. exe veya. dll) oluşturacaktır. *. Pdb* dosyası, çıkış dosyasının adı ile aynı temel dosya adına sahiptir. **Pdbdosya** ,. pdb dosyası için varsayılan olmayan bir dosya adı ve konum belirtmenize olanak tanır. Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.  

## <a name="pathmap"></a>PathMap

**Pathmap** derleyici seçeneği, fiziksel yolların derleyicinin çıkış kaynak yol adlarına nasıl eşlendiğini belirtir. Bu seçenek, derleyicinin çalıştığı makinedeki her fiziksel yolu, çıktı dosyalarında yazılması gereken karşılık gelen bir yola eşler. Aşağıdaki örnekte, `path1` geçerli ortamdaki kaynak dosyalarının tam yoludur ve `sourcePath1` `path1` herhangi bir çıkış dosyasında yerine kaynak yol kullanılır. Birden çok eşlenmiş kaynak yolunu belirtmek için, her biri noktalı virgülle ayırın.

```xml
<PathMap>path1=sourcePath1;path2=sourcePath2</PathMap>
```

Derleyici, kaynak yolunu aşağıdaki nedenlerden dolayı çıktısına yazar:

1. İsteğe bağlı bir parametreye uygulandığında kaynak yolu bir bağımsız değişken için değiştirilir <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> .
1. Kaynak yolu bir PDB dosyasına katıştırılır.
1. PDB dosyasının yolu bir PE (taşınabilir yürütülebilir) dosyasına katıştırılır.

## <a name="errorreport"></a>ErrorReport

Bu seçenek, C# iç derleyici hatasını Microsoft 'a bildirmenin kolay bir yolunu sağlar.

> [!NOTE]
> Windows Vista ve Windows Server 2008 ' de, Visual Studio için yaptığınız hata raporlama ayarları Windows Hata Bildirimi (WER) ile yapılan ayarları geçersiz kılmaz. WER ayarları her zaman Visual Studio hata raporlama ayarlarından önceliklidir.

```xml
<ErrorReport>setting</ErrorReport>
```

Bağımsız değişkeni şunlardan biri olmalıdır:

- **hiçbiri**: iç derleyici hataları hakkında raporlar toplanmayacak veya Microsoft 'a gönderilmez.
- **istem**: iç derleyici hatası aldığınızda rapor göndermenizi ister. geliştirme ortamında bir uygulama derlerken varsayılan değer, **istem** varsayılandır.
- **kuyruk**: hata raporunu sıralar. Yönetici kimlik bilgileriyle oturum açtığınızda, son oturum açtığınız zamandan bu yana tüm sorunları bildirebilirsiniz. Her üç günde birden çok kez rapor göndermeniz istenmez. komut satırında bir uygulama derlerken varsayılan **kuyruk** varsayılandır.
- **Send**: iç derleyici hatalarının raporlarını otomatik olarak Microsoft 'a gönderir. Bu seçeneği etkinleştirmek için öncelikle Microsoft veri toplama ilkesini kabul etmelisiniz. Bir bilgisayarda ilk kez belirttiğinizde `<ErrorReport>send</ErrorReport>` , bir derleyici iletisi sizi Microsoft veri toplama ilkesini içeren bir Web sitesine başvuracaktır.

Derleyici bir kaynak kodu dosyasını işleyeişce bir iç derleyici hatası (ıCE) oluşur. Bir buz gerçekleştiğinde, derleyici bir çıkış dosyası ya da kodunuzu onarmak için kullanabileceğiniz yararlı bir tanılama üretmez.

**Errorreport**'U kullanarak C# EKIBINE Ice bilgileri sağlayabilirsiniz. Hata raporlarınız, gelecekteki derleyici sürümlerinin artırılmasına yardımcı olabilir. Kullanıcının raporları gönderebilme özelliği bilgisayar ve Kullanıcı ilkesi izinlerine bağlıdır.

## <a name="applicationconfiguration"></a>ApplicationConfiguration

**ApplicationConfiguration** derleyici seçeneği, bir C# uygulamasının derleme bağlama süresinde ortak dil çalışma zamanına (CLR) bir derlemenin uygulama yapılandırma (app.config) dosyasının konumunu belirtmesini sağlar.

```xml
<ApplicationConfiguration>file</ApplicationConfiguration>
```

`file`, Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasıdır. **ApplicationConfiguration** 'ın bir kullanımı, bir derlemenin hem .NET Framework sürümüne hem de aynı anda belirli bir başvuru derlemesinin Silverlight sürümüne .NET Framework başvurması gereken gelişmiş senaryolardır. Örneğin, Windows Presentation Foundation (WPF) içinde yazılmış bir XAML tasarımcısının, tasarımcı 'nın Kullanıcı arabirimi için hem WPF masaüstüne hem de Silverlight 'ın içerdiği WPF 'nin alt kümesine başvurması gerekebilir. Aynı tasarımcı derlemesinin her iki derlemeye de erişimi vardır. Varsayılan olarak, derleme bağlaması iki derlemeyi eşdeğer olarak gördüğü için ayrı başvurular bir derleyici hatasına neden olur. **ApplicationConfiguration** derleyici seçeneği `<supportPortability>` , aşağıdaki örnekte gösterildiği gibi bir etiketi kullanarak varsayılan davranışı devre dışı bırakan bir app.config dosyasının konumunu belirtmenize olanak sağlar.

```xml
<supportPortability PKT="7cec85d7bea7798e" enable="false"/>
```

Derleyici, dosyanın konumunu CLR 'nin derleme bağlama mantığına geçirir.

> [!NOTE]
> Projede zaten ayarlanmış olan app.config dosyasını kullanmak için, `<UseAppConfigForCompiler>` *. csproj* dosyasına özellik etiketi ekleyin ve değerini olarak ayarlayın `true` . Farklı bir app.config dosyası belirtmek için, özellik etiketi ekleyin `<AppConfigForCompiler>` ve değerini dosyanın konumuna ayarlayın.

Aşağıdaki örnek, bir uygulamanın hem .NET Framework .NET Framework uygulamasına hem de her iki uygulamada bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına yönelik başvurularına sahip olmasını sağlayan bir app.config dosyası gösterir. **ApplicationConfiguration** derleyici seçeneği bu app.config dosyasının konumunu belirtir.

```xml
<configuration>
  <runtime>
    <assemblyBinding>
      <supportPortability PKT="7cec85d7bea7798e" enable="false"/>
      <supportPortability PKT="31bf3856ad364e35" enable="false"/>
    </assemblyBinding>
  </runtime>
</configuration>
```

## <a name="additionallibpaths"></a>Adtiontalbpaths

**Additionalbıpaths** seçeneği, [**Başvurular**](inputs.md#references) seçeneğiyle başvurulan derlemelerin konumunu belirtir.

```xml
<AdditionalLibPaths>dir1[,dir2]</AdditionalLibPaths>
```

, `dir1` Başvurulan bir derlemenin geçerli çalışma dizininde (derleyicisini çağırmakta olduğunuz dizin) veya ortak dil çalışma zamanının sistem dizininde bulunamaması durumunda, derleyicinin bakacağı bir dizindir. `dir2` , derleme başvuruları için içinde arama yapılacak bir veya daha fazla dizin. Dizin adlarını virgülle ve aralarında boşluk olmadan ayırın. Derleyici, aşağıdaki sırayla tam olmayan derleme başvurularını arar:  

1. Geçerli çalışma dizini.
1. Ortak dil çalışma zamanı sistem dizini.
1. **Additionalbpaths** tarafından belirtilen dizinler.
1. LıB ortam değişkeni tarafından belirtilen dizinler.

Derleme başvurusunu belirtmek için **başvuruyu** kullanın. **Adtiontalbpaths** eklenebilir. Bir defadan fazla belirtmek önceki değerlere ekler. Bağımlı derlemenin yolu derleme bildiriminde belirtilmediğinden, uygulama derlemeyi genel derleme önbelleğinde bulur ve kullanır. Derlemeye başvuran derleyici, ortak dil çalışma zamanının derlemeyi çalışma zamanında bulabileceği ve yükleyemediğini göstermez. Çalışma zamanının başvurulmuş derlemeleri nasıl arayacağını görmek için bkz. [çalışma zamanının derlemeleri nasıl konumlandırır](../../../framework/deployment/how-the-runtime-locates-assemblies.md) .  

## <a name="generatefullpaths"></a>GenerateFullPaths

**GenerateFullPaths** seçeneği derleyicinin derleme hatalarını ve uyarılarını listelerken dosyanın tam yolunu belirtmesini sağlar.
  
```Xml
<GenerateFullPaths>true</GenerateFullPaths>
```

Varsayılan olarak, derlemeden kaynaklanan hatalar ve uyarılar, bir hatanın bulunduğu dosyanın adını belirtir. **GenerateFullPaths** seçeneği derleyicinin dosyanın tam yolunu belirtmesini sağlar. Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.

## <a name="preferreduilang"></a>PreferredUILang

**PreferredUILang** derleyici seçeneğini kullanarak, C# derleyicisinin hata iletileri gibi çıktıyı görüntülediği dili belirtebilirsiniz.

```xml
<PreferredUILang>language</PreferredUILang>
```

Burada `language` , Derleyici çıktısı için kullanılacak dilin [dil adıdır](/windows/desktop/Intl/language-names) . C# derleyicisinin hata iletileri ve diğer komut satırı çıktıları için kullanmasını istediğiniz dili belirtmek için **PreferredUILang** derleyici seçeneğini kullanabilirsiniz. Dile ait dil paketi yüklü değilse, bunun yerine işletim sisteminin dil ayarı kullanılır.

## <a name="baseaddress"></a>BaseAddress

**BaseAddress** SEÇENEĞI, dll 'nin yükleneceği tercih edilen temel adresi belirtmenizi sağlar. Bu seçeneğin ne zaman ve neden kullanıldığı hakkında daha fazla bilgi için bkz. [Larry Osterman 'ın Web günlüğü](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).

```xml
<BaseAddress>address</BaseAddress>
```

`address`, Dll 'nin temel adresidir. Bu adres ondalık, onaltılık veya sekizlik sayı olarak belirtilebilir. Bir DLL için varsayılan temel adres, .NET ortak dil çalışma zamanı tarafından ayarlanır. Bu adresteki alt sıralama sözcüğü yuvarlanır. Örneğin, öğesini belirtirseniz `0x11110001` , ' ye yuvarlanacaktır `0x11110000` . DLL imzalama işlemini gerçekleştirmek için,-R seçeneğiyle SN.EXE kullanın.

## <a name="checksumalgorithm"></a>ChecksumAlgorithm

Bu seçenek, PDB 'deki kaynak dosyalarını kodlamak için kullandığımız sağlama toplamı algoritmasını denetler.

```xml
<ChecksumAlgorithm>algorithm</ChecksumAlgorithm>
```

`algorithm` `SHA1` (Varsayılan) ya da olmalıdır `SHA256` .

## <a name="codepage"></a>Sayfasının

Bu seçenek, gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse, derleme sırasında kullanılacak kod sayfasını belirtir.
  
```xml
<CodePage>id</CodePage>
```

, `id` Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasının kimliğidir. Derleyici önce tüm kaynak dosyalarını UTF-8 olarak yorumlamaya çalışacaktır. Kaynak kodu dosyalarınız UTF-8 dışındaki bir kodlamadeyse ve 7 bit ASCII karakterlerden farklı karakterler kullanıyorsa, hangi kod sayfasının kullanılacağını belirtmek için **kod** sayfası seçeneğini kullanın. **Kod sayfası** , derinizdeki tüm kaynak kodu dosyaları için geçerlidir. Sisteminizde hangi kod sayfalarının desteklendiğini bulma hakkında bilgi için bkz. [Getcpınfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) .

## <a name="utf8output"></a>Utf8Output

**Utf8output** seçeneği, DERLEYICI çıkışını utf-8 kodlaması kullanarak görüntüler.

```xml
<Utf8Output>true</Utf8Output>
```

Bazı uluslararası yapılandırmalarda, Derleyici çıktısı konsolunda doğru şekilde görüntülenemez. **Utf8output** kullanın ve derleyici çıkışını bir dosyaya yeniden yönlendirin.

## <a name="filealignment"></a>Dosya hizalaması

**Filehizalaması** seçeneği, çıkış dosyanızdaki bölümlerin boyutunu belirtmenizi sağlar. Geçerli değerler 512, 1024, 2048, 4096 ve 8192. Bu değerler baytlardır.

```xml
<FileAlignment>number</FileAlignment>
```

Visual Studio 'da projeniz için **derleme** özelliklerinin **Gelişmiş** sayfasından **filehizalaması** seçeneğini ayarlarsınız. Her bölüm, **Filehizalaması** değerinin katı olan bir sınıra göre hizalanacaktır. Sabit bir varsayılan yoktur. **Dosya hizalama** belirtilmezse, ortak dil çalışma zamanı derleme zamanında bir varsayılan değer seçer. Bölüm boyutunu belirterek, çıkış dosyasının boyutunu etkilersiniz. Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir. Çıkış dosyanızdaki bölümler hakkındaki bilgileri görmek için [dumpbin](/cpp/build/reference/dumpbin-options) ' i kullanın.

## <a name="errorendlocation"></a>ErrorEndLocation

Derleyiciye her hatanın bitiş konumunun satırını ve sütununu çıktı olarak bildirir.

```xml
<ErrorEndLocation>filename</ErrorEndLocation>
```

Varsayılan olarak, derleyici tüm hatalar ve uyarılar için kaynaktaki başlangıç konumunu yazar. Bu seçenek true olarak ayarlandığında, derleyici her bir hata ve uyarı için hem başlangıç hem de bitiş konumunu yazar.

## <a name="nostandardlib"></a>NoStandardLib

**NoStandardLib** , tüm sistem ad alanını tanımlayan mscorlib.dll içeri aktarmayı engeller.

```xml
<NoStandardLib>true</NoStandardLib>
```

Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu seçeneği kullanın. **NoStandardLib** belirtmezseniz, mscorlib.dll programınıza içeri aktarılır (belirtirken aynı `<NoStandardLib>false</NoStandardLib>` ).

## <a name="subsystemversion"></a>SubsystemVersion

Yürütülebilir dosyanın çalıştığı alt sistemin en düşük sürümünü belirtir. En yaygın olarak, bu seçenek yürütülebilir dosyanın eski Windows sürümleriyle kullanılamayan güvenlik özelliklerini kullanmasını sağlar.

> [!NOTE]
> Alt sistemi belirtmek için, [**TargetType**](./output.md#targettype) derleyici seçeneğini kullanın.

```xml
<SubsystemVersion>major.minor</SubsystemVersion>
```

`major.minor`Alt sistemin gerekli en düşük sürümünü, birincil ve ikincil sürümlerin nokta gösteriminde gösterildiği gibi belirtin. Örneğin, bir uygulamanın Windows 7 ' den eski bir işletim sisteminde çalışacağını belirtebilirsiniz. Bu seçeneğin değerini, bu makalede daha sonra açıklanan tabloda açıklanan şekilde 6,01 olarak ayarlayın. `major`Ve değerlerini `minor` tamsayılar olarak belirtirsiniz. Sürümdeki öndeki sıfırlar `minor` sürümü değiştirmez, ancak sonunda sıfır yapılır. Örneğin, 6,1 ve 6,01 aynı sürüme başvurun, ancak 6,10 farklı bir sürüme başvurur. Karışıklığın önüne geçmek için küçük sürümü iki basamakla ifade etmenizi öneririz.

Aşağıdaki tabloda, Windows 'un ortak alt sistem sürümleri listelenmektedir.

|Windows sürümü|Alt sistem sürümü|
|---------------------|-----------------------|
|Windows 2000|5.00|
|Windows XP|5,01|
|Windows Server 2003|5,02|
|Windows Vista|6,00|
|Windows 7|6,01|
|Windows Server 2008|6,01|
|Windows 8|6,02|

**Alt Systemversion** derleyici seçeneğinin varsayılan değeri aşağıdaki listede yer alan koşullara bağlıdır:

- Aşağıdaki listede herhangi bir derleyici seçeneğinin ayarlanmış olması halinde varsayılan değer 6,02 ' dir:
  - [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)
  - [-target:winmdobj](./target-winmdobj-compiler-option.md)
  - [-Platform: ARM](./platform-compiler-option.md)
- MSBuild kullanıyorsanız varsayılan değer 6,00 ' dir. .NET Framework 4,5 ' i hedefliyorsanız ve bu listede daha önce belirtilen derleyici seçeneklerinden hiçbirini belirlemediniz.
- Önceki koşullardan hiçbiri doğru değilse varsayılan değer 4,00 ' dir.

## <a name="moduleassemblyname"></a>ModuleAssemblyName

Genel olmayan türleri *. netmodule* 'nin erişebileceği bir derlemenin adını belirtir.

```xml
<ModuleAssemblyName>assembly_name</ModuleAssemblyName>
```

**Moduleassemblyname** bir *. netmodule* oluştururken ve aşağıdaki koşulların doğru olduğu durumlarda kullanılmalıdır:

- *. Netmodule* , mevcut bir derlemede ortak olmayan türlere erişim gerektirir.
- . Netmodule 'nin derolacağı derlemenin adını bilirsiniz.
- Mevcut bütünleştirilmiş kod, öğesine arkadaş bütünleştirilmiş kodu erişimi verdi. *netmodule* oluşturulacak.

. Netmodule oluşturma hakkında daha fazla bilgi için, bkz. **modülün** [**TargetType**](output.md#targettype) seçeneği. Friend derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).

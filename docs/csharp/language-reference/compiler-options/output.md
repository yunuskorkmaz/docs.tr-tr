---
description: Derleyici çıkışını denetleyen C# derleyici seçenekleri. Bu seçenekler bir derlemeden derleme oluşturmayı denetler.
title: C# derleyici seçenekleri-çıkış seçenekleri
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- DocumentationFile compiler option [C#]
- OutputAssembly compiler option [C#]
- PlatformTarget compiler option [C#]
- ProduceReferenceAssembly compiler option [C#]
- TargetType compiler option [C#]
ms.openlocfilehash: 9caa290a7c9b5fea1b0f896e9443075b4b470f7b
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636850"
---
# <a name="c-compiler-options-that-control-compiler-output"></a>Derleyici çıkışını denetleyen C# derleyici seçenekleri

Aşağıdaki seçenekler derleyici çıkış oluşturmayı denetler. Yeni MSBuild sözdizimi **kalın** olarak gösterilir. Eski *csc.exe* sözdizimi içinde gösterilir `code style` .

- **Belgedosyası**  /  `-doc` : açıklamalardan XML belgesi oluştur `///` .
- **OutputAssembly**  /  `-out` : çıkış derleme dosyasını belirtin.
- **PlatformTarget**  /  `-platform` : hedef platform CPU 'sunu belirtin.
- **ProduceReferenceAssembly**  /  `-refout` : bir başvuru bütünleştirilmiş kodu oluşturun.
- **TargetType** `-target` : çıkış derlemesinin türünü belirtin.

## <a name="documentationfile"></a>Belgetationfile

**Belgelerimdosyası** seçeneği, belge AÇıKLAMALARıNı bir XML dosyasına eklemenizi sağlar. Kodunuzu Belgeleme hakkında daha fazla bilgi edinmek için bkz. [belge açıklamaları Için önerilen Etiketler](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md). Değer, çıkış XML dosyasının yolunu belirtir. XML dosyası, derlemenin kaynak kodu dosyalarındaki açıklamaları içerir.

```xml
<DocumentationFile>path/to/file.xml</DocumentationFile>
```

Ana veya üst düzey deyimler içeren kaynak kodu dosyası ilk olarak XML 'e çıktıdır. Genellikle oluşturulan. xml dosyasını [IntelliSense](/visualstudio/ide/using-intellisense)ile kullanmak isteyeceksiniz. *. Xml* dosya adı, derleme adı ile aynı olmalıdır. *. Xml* dosyası, derlemeyle aynı dizinde olmalıdır. Visual Studio projesinde derlemeye başvuruluyorsa *. xml* dosyası da bulunur. Kod açıklamaları oluşturma hakkında daha fazla bilgi için bkz. [kod açıklamaları sağlama](/visualstudio/ide/reference/generate-xml-documentation-comments). İle derleme yapmadığınız takdirde [`<TargetType:Module>`](#targettype) , `file` `<assembly>` ve `</assembly>` Çıkış dosyası için derleme bildirimini içeren dosyanın adını belirten etiketler içerecektir. Örnekler için bkz. [XML belgeleri özelliklerini kullanma](../../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).

> [!NOTE]
> **Belgetadosyası** seçeneği projedeki tüm dosyalar için geçerlidir. Belirli bir dosyanın veya kod bölümünün belge açıklamalarıyla ilgili uyarıları devre dışı bırakmak için [#pragma uyarı](../preprocessor-directives.md#pragma-warning)kullanın.

## <a name="outputassembly"></a>OutputAssembly

**OutputAssembly** seçeneği, çıktı dosyasının adını belirtir. Çıkış yolu, derleyici çıktısının yerleştirildiği klasörü belirtir.

```xml
<OutputAssembly>folder</OutputAssembly>
```

Oluşturmak istediğiniz dosyanın tam adını ve uzantısını belirtin. Çıkış dosyasının adını belirtmezseniz, MSBuild, çıkış derlemesinin adını belirtmek için projenin adını kullanır. Eski stil projeleri aşağıdaki kuralları kullanır:

- Bir. exe, `Main` yöntemini veya en üst düzey deyimlerini içeren kaynak kodu dosyasından adını alır.  
- Bir. dll veya. netmodule adı ilk kaynak kodu dosyasından alır.

Bir derlemenin parçası olarak üretilen tüm modüller, derlemede oluşturulan herhangi bir derlemeyle ilişkili dosyalar olur. İlişkili dosyaları görmek üzere derleme bildirimini görüntülemek için [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) kullanın.

Bir exe 'nin bir [friend derlemesinin](../../../standard/assembly/friend.md)hedefi olması için **OutputAssembly** derleyici seçeneği gereklidir.

## <a name="platformtarget"></a>PlatformTarget

Hangi CLR sürümünün derlemeyi çalıştırabileceği belirtir.

```xml
<PlatformTarget>anycpu</PlatformTarget>
```

- **anycpu** (varsayılan), derlemenizi herhangi bir platformda çalışacak şekilde derler. Uygulamanız mümkün olduğunda 64 bitlik bir işlem olarak çalışır ve yalnızca bu mod kullanılabilir olduğunda 32 bit 'e geri döner.
- **anycpu32bitpreferred** , derlemenizi herhangi bir platformda çalışacak şekilde derler. Uygulamanız, hem 64 bit hem de 32 bit uygulamaları destekleyen sistemlerde 32 bitlik modda çalışır. Bu seçeneği yalnızca .NET Framework 4,5 veya üstünü hedefleyen projeler için belirtebilirsiniz.
- **ARM** , derlemenizi GELIŞMIŞ bir RISC MAKINESI (ARM) işlemcisi olan bir bilgisayarda çalışacak şekilde derler.
- **ARM64** , derlemenizi, A64 yönerge kümesini destekleyen GELIŞMIŞ bir RISC MAKINESI (ARM) işlemcisi olan bir bilgisayarda 64 bitlik CLR tarafından çalışacak şekilde derler.
- **x64** , derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.
- **x86** , derlemenizi 32 bit, x86 uyumlu CLR tarafından çalıştırılacak şekilde derler.
- **Itanium** , derlemenizi Itanium işlemcisi olan bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.

64 bitlik bir Windows işletim sisteminde:

- **X86** ile derlenen derlemeler, WOW64 altında çalışan 32 bitlik clr üzerinde çalıştırılır.
- **Anycpu** ile derlenen bir dll, yüklendiği IŞLEMLE aynı CLR üzerinde yürütülür.
- **Anycpu** ile derlenen yürütülebilir dosyalar 64 bitlik clr üzerinde yürütülür.
- **Anycpu32bitpreferred** ile derlenen yürütülebilir dosyalar 32 bitlik clr üzerinde yürütülür.

**Anycpu32bitpreferred** ayarı yalnızca yürütülebilir dosya için geçerlidir (. EXE) dosyalarını ve .NET Framework 4,5 veya üzeri bir sürümü gerektirir. Windows 64 bit işletim sisteminde çalışacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).

Visual Studio 'daki projeniz için **Platform hedefi** seçeneğini **derleme** Özellikleri sayfasından ayarlarsınız.

**Anycpu** 'un davranışı, .NET Core ve .NET 5 ve sonraki sürümlerde bazı ek nuslarla aynıdır. **Anycpu**'u ayarladıktan sonra uygulamanızı yayımlayın ve x86 ya da x64 ile yürütün `dotnet.exe` `dotnet.exe` . Kendi içinde bulunan uygulamalar için adım, `dotnet publish` RID yapılandırma için yürütülebilir dosyayı paketler.

## <a name="producereferenceassembly"></a>ProduceReferenceAssembly

**ProduceReferenceAssembly** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir. Bu `metadataPeStream` , yayma API 'sinde öğesine dönüştürür. , `filepath` Başvuru derlemesinin yolunu belirtir. Genellikle birincil derlemenin ile eşleşmelidir. Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir.

```xml
<ProduceReferenceAssembly>filepath</ProduceReferenceAssembly>
```

Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en az meta veri miktarını içeren özel bir derleme türüdür. Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm üyelerin bildirimlerini içerirler. Başvuru derlemeleri tüm üye uygulamalarını ve özel üyelerin bildirimlerini hariç tutar. Bu üyelerin API sözleşmeleri üzerinde herhangi bir observable etkisi yoktur. Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .

**ProduceReferenceAssembly** ve [**ProduceOnlyReferenceAssembly**](./code-generation.md#produceonlyreferenceassembly) seçenekleri birbirini dışlıyor.

## <a name="targettype"></a>Öğesi

**TargetType** derleyici seçeneği aşağıdaki biçimlerden birinde belirtilebilir:  
  
- **kitaplık**: bir kod kitaplığı oluşturmak için. **kitaplık** varsayılan değerdir.
- **exe**: bir. exe dosyası oluşturmak için.  
- modül oluşturma **modülü** .  
- bir Windows programı oluşturmak için **winexe** .
- Ara *. winmdobj* dosyası oluşturmak için **winmdobj** .
- Windows 8. x Mağazası uygulamaları için. exe dosyası oluşturmak için **appcontainerexe** .
  
> [!NOTE]
> .NET Framework hedefler için, **Modül** belirtmediğiniz takdirde, bu seçenek bir .NET Framework derleme bildiriminin bir çıkış dosyasına yerleştirilmesine neden olur. Daha fazla bilgi için bkz. .NET ve [ortak özniteliklerde](../attributes/global.md) [derlemeler](../../../standard/assembly/index.md) .

```xml
<TargetType>library</TargetType>
```

Derleyici, derleme başına yalnızca bir derleme bildirimi oluşturur. Bir derlemedeki tüm dosyalar hakkındaki bilgiler, derleme bildirimine yerleştirilir. Komut satırında birden çok çıkış dosyası üretilirken, yalnızca bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıkış dosyasına gitmelidir.

Bir derleme oluşturursanız, kodunuzun tümünün veya bir kısmının özniteliğiyle CLS uyumlu olduğunu belirtebilirsiniz <xref:System.CLSCompliantAttribute> .

### <a name="library"></a>kitaplık

**Kitaplık** seçeneği, derleyicinin yürütülebilir dosya (exe) yerine bir dinamik bağlantı KITAPLıĞı (dll) oluşturmasına neden olur. DLL, *. dll* uzantısıyla oluşturulacaktır. Aksi belirtilmedikçe, [**OutputAssembly**](#outputassembly) seçeneğiyle belirtilmedikçe, çıkış dosyası adı ilk giriş dosyasının adını alır. Bir *. dll* dosyası oluştururken bir [`Main`](../../programming-guide/main-and-command-args/index.md) Yöntem gerekli değildir.

### <a name="exe"></a>exe

**Exe** seçeneği derleyicinin YÜRÜTÜLEBILIR (exe), konsol uygulaması oluşturmasına neden olur. Yürütülebilir dosya,. exe uzantısıyla oluşturulacaktır. Bir Windows program yürütülebilir dosyası oluşturmak için **winexe** kullanın. Aksi takdirde, [**OutputAssembly**](#outputassembly) seçeneğiyle belirtilmediği takdirde, çıkış dosyası adı giriş noktasını içeren giriş dosyasının adını alır ([Main](../../programming-guide/main-and-command-args/index.md) yöntemi veya üst düzey deyimler). Bir. exe dosyasına derlenen kaynak kodu dosyalarında tek bir giriş noktası gereklidir. [**StartupObject**](./advanced.md#mainentrypoint-or-startupobject) derleyici seçeneği `Main` , kodunuzun bir yöntemi olan birden fazla sınıfa sahip olduğu durumlarda yöntemi hangi sınıfın içerdiğini belirtmenizi sağlar `Main` .  

### <a name="module"></a>modül

Bu seçenek derleyicinin bir derleme bildirimi üretmesine neden olur. Varsayılan olarak, bu seçenekle derleme tarafından oluşturulan çıkış dosyası *. netmodule* uzantısına sahip olacaktır. Derleme bildirimine sahip olmayan bir dosya .NET çalışma zamanı tarafından yüklenemez. Ancak, bu tür bir dosya [**AddModules**](inputs.md#addmodules)içeren bir derlemenin derleme bildirimine eklenebilir. Tek bir derlemede birden fazla modül oluşturulduysa, bir modüldeki [iç](../keywords/internal.md) türler derlemedeki diğer modüller için kullanılabilir olacaktır. Bir modüldeki kod `internal` , başka bir modüldeki türlere başvurduğunda, her iki modülün da [**AddModules**](inputs.md#addmodules)ile birlikte bir derleme bildirimine dahil olması gerekir. Modül oluşturma, Visual Studio geliştirme ortamında desteklenmez.

### <a name="winexe"></a>winexe

**Winexe** seçeneği derleyicinin YÜRÜTÜLEBILIR (exe), Windows programı oluşturmasına neden olur. Yürütülebilir dosya,. exe uzantısıyla oluşturulacaktır. Bir Windows programı, .NET kitaplığından veya Windows API 'Leriyle bir kullanıcı arabirimi sağlayan bir programdır. Konsol uygulaması oluşturmak için **exe** kullanın. Aksi takdirde, [**OutputAssembly**](#outputassembly) seçeneğiyle belirtilmediği takdirde, çıkış dosyası adı yöntemi içeren giriş dosyasının adını alır [`Main`](../../programming-guide/main-and-command-args/index.md) . Bir `Main` . exe dosyasına derlenen kaynak kodu dosyalarında bir ve yalnızca bir yöntem gereklidir. [**StartupObject**](./advanced.md#mainentrypoint-or-startupobject) seçeneği `Main` , kodunuzun bir yöntemi olan birden fazla sınıfa sahip olduğu durumlarda yöntemi hangi sınıfın içerdiğini belirtmenizi sağlar `Main` .

### <a name="winmdobj"></a>winmdobj

**Winmdobj** seçeneğini kullanırsanız, derleyici Windows çalışma zamanı ikili (*. winmd*) dosyasına dönüştürebileceğiniz bir ara *. winmdobj* dosyası oluşturur. *. Winmd* dosyası daha sonra JavaScript ve C++ programları tarafından, yönetilen dil programlarına ek olarak tüketilebilir.

**Winmdobj** ayarı derleyiciye bir ara modülün gerekli olduğunu bildirir. *. Winmdobj* dosyası daha sonra <xref:Microsoft.Build.Tasks.WinMDExp> bir Windows meta veri (*. winmd*) dosyası oluşturmak için dışarı aktarma aracından beslenebilir. *. Winmd* dosyası, özgün kitaplıktan kodu ve JavaScript ya da C++ tarafından kullanılan winmd meta verilerini ve Windows çalışma zamanı içerir. **Winmdobj** derleyici seçeneği kullanılarak derlenen bir dosyanın çıktısı yalnızca Wımmdexp Export aracı için giriş olarak kullanılır. *. Winmdobj* dosyasının kendisine doğrudan başvurulmuyor. [**OutputAssembly**](#outputassembly) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır. Bir [`Main`](../../programming-guide/main-and-command-args/index.md) Yöntem gerekli değildir.

### <a name="appcontainerexe"></a>appcontainerexe

**Appcontainerexe** derleyici seçeneğini kullanırsanız, derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows çalıştırılabilir (*. exe*) dosyası oluşturur. Bu seçenek [-target: winexe](output.md) ile eşdeğerdir, ancak Windows 8. x Mağazası uygulamaları için tasarlanmıştır.

Uygulamanın bir uygulama kapsayıcısında çalışmasını gerektirmek için, bu seçenek [taşınabilir yürütülebilir](/windows/desktop/Debug/pe-format) (PE) dosyasında bir bit ayarlar. Bu bit ayarlandığında, CreateProcess yöntemi bir uygulama kapsayıcısının dışında yürütülebilir dosyayı başlatmaya çalışırsa bir hata oluşur. [**OutputAssembly**](#outputassembly) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı yöntemi içeren giriş dosyasının adını alır [`Main`](../../programming-guide/main-and-command-args/index.md) .

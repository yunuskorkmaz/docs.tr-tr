---
title: F# Etkileşimli Seçenekleri
description: Etkileşimli, fsi. exe tarafından F# desteklenen komut satırı seçenekleri hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: c9cd5c2e73a6e2f6ce0a9b2f2a631b6a2658423c
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083113"
---
# <a name="f-interactive-options"></a>F# Etkileşimli Seçenekleri

> [!NOTE]
> Bu makalede şu anda yalnızca Windows deneyimi açıklanmaktadır.  Yeniden yazılır.

Bu konu, F# `fsi.exe`etkileşimli tarafından desteklenen komut satırı seçeneklerini açıklar. F#Etkileşimli, F# derleyici ile aynı komut satırı seçeneklerinin birçoğunu kabul eder, ancak aynı zamanda bazı ek seçenekleri de kabul eder.

## <a name="using-f-interactive-for-scripting"></a>Betik F# için etkileşimli kullanma
F#Etkileşimli, `fsi.exe`, etkileşimli olarak başlatılabilir veya bir betiği çalıştırmak için komut satırından başlatılabilir. Komut satırı söz dizimi

```console
> fsi.exe [options] [ script-file [arguments] ]
```

Betik dosyaları F# `.fsx`için dosya uzantısı.

## <a name="table-of-f-interactive-options"></a>F# Etkileşimli seçenekler tablosu
Aşağıdaki tabloda etkileşimli tarafından F# desteklenen seçenekler özetlenmektedir. Bu seçenekleri komut satırında veya Visual Studio IDE aracılığıyla ayarlayabilirsiniz. Bu seçenekleri Visual Studio IDE 'de ayarlamak için, **Araçlar** menüsünü açın, **Seçenekler...** ' i seçin, sonra  **F# araçlar** düğümünü genişletin ve  **F# etkileşimli**' i seçin.

F# Etkileşimli seçenek bağımsız değişkenlerinde listelerin göründüğü, liste öğeleri noktalı virgülle (`;`) ayrılır.

|Seçenek|Açıklama|
|------|-----------|
|**--**|F# Etkileşimli olarak kalan bağımsız değişkenleri F# program veya betiğe komut satırı bağımsız değişkenleri olarak değerlendirmek için kullanılır. Bu, **fsi. Commandbir**listesini kullanarak koda erişebilirsiniz.|
|**--checked**[ **+** &#124; **-** ]|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--CodePage:&lt;int&gt;**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--consolecolors** [ **+** &#124; **-** ]|Uyarı ve hata iletilerini renkli olarak verir.|
|**--çapraz iyileştirme** [ **+** &#124; **-** ]|Modüller arası iyileştirmeleri etkinleştirin veya devre dışı bırakın.|
|**--debug**[ **+** &#124; **-** ]<br /><br />**--Hata Ayıkla:** [**tam**&#124;**pdbportable**&#124;&#124;**Embedded**]<br /><br />**-g**[ **+** &#124; **-** ]<br /><br />**-g:** [**tam**&#124;**pdbportable**&#124;&#124;**Embedded**]|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--tanımla:&lt;dize&gt;**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--deterministic**[ **+** &#124; **-** ]|Belirleyici derleme üretir (Modül sürümü GUID 'i ve zaman damgası dahil).|
|**--Exec**|Dosyaları F# yükledikten veya komut satırında verilen betik dosyasını çalıştırdıktan sonra etkileşimli olarak çıkış ister.|
|**--fullpaths**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--GUI** [ **+** &#124; **-** ]|Windows Forms olay döngüsünü etkinleştirilir veya devre dışı bırakır. Varsayılan değer etkindir.|
|**--yardım**<br /><br />**-?**|Komut satırı söz dizimini ve her seçeneğin kısa bir açıklamasını göstermek için kullanılır.|
|**--lib:&lt;Klasör-Listele&gt;**<br /><br />**-I:&lt;klasör-liste&gt;**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--Yükle:&lt;dosya adı&gt;**|Başlangıçta verilen kaynak kodu derler ve derlenen F# yapıları oturuma yükler. Hedef kaynak **#use** veya **#load**gibi komut dosyası yönergeleri içeriyorsa,-- **Load** veya **#load**yerine **--Use** veya **#use** kullanmanız gerekir.|
|**--mlcompatibility**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--noframework**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md)|
|**--nologo**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--nowarn:&lt;uyarı-liste&gt;**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--optimize** et [ **+** &#124; **-** ]|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--preferreduilang:&lt;lang&gt;**| Tercih edilen çıkış dili kültür adını belirtir (örneğin, ES-ES, ja-JP). |
|**--quiet**|Etkileşimli F# çıktıyı **stdout** akışına karşı gizleyin.|
|**--alıntılar-hata ayıkla**|Ek hata ayıklama bilgilerinin, alıntı sabit değerleri ve yansıtılan tanımlardan F# türetilmiş ifadeler için yayınlanmasının gerektiğini belirtir. Hata ayıklama bilgileri, bir F# ifade ağacı düğümünün özel özniteliklerine eklenir. Bkz. [kod teklifleri](code-quotations.md) ve [Expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--ReadLine** [ **+** &#124; **-** ]|Etkileşimli modda sekme tamamlamayı etkinleştirin veya devre dışı bırakın.|
|**--Başvuru:&lt;dosya adı&gt;**<br /><br />**-r:&lt;dosya adı&gt;**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--shadowcopyreferences** [ **+** &#124; **-** ]|, Başvuruların F# etkileşimli işlem tarafından kilitlenmesini engeller.|
|**--simpleresolution**|MSBuild çözümlemesi yerine dizin tabanlı kurallar kullanarak derleme başvurularını çözümler.|
|**--edilecek çağrılar** [ **+** &#124; **-** ]|Tail Özyinelemeli işlevler için yığın çerçevesinin yeniden kullanılmasını sağlayan tail Il yönergesinin kullanımını etkinleştirin veya devre dışı bırakın. Bu seçenek varsayılan olarak etkindir.|
|**--targetprofile:&lt;dize&gt;**|Bu derlemenin hedef çerçeve profilini belirtir. Geçerli değerler mscorlib, netcore veya Netstandard ' dır.  Varsayılan olarak mscorlib 'dir.|
|**--şunu kullanın&lt;: dosya adı&gt;**|Yorumlayıcıya ilk girdi olarak başlangıçta verilen dosyayı kullanmasını söyler.|
|**--utf8output**|FSC. exe derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--warn:&lt;uyarı düzeyi&gt;**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]: **&lt;int-list&gt;**|**FSC. exe** derleyici seçeneğiyle aynı. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).|

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[Derleyici Seçenekleri](compiler-options.md)|, F# **FSC. exe**derleyicisi için kullanılabilen komut satırı seçeneklerini açıklar.|

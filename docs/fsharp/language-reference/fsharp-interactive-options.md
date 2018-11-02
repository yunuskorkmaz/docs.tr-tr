---
title: F# Etkileşimli Seçenekleri
description: Tarafından desteklenen komut satırı seçenekleri hakkında F# etkileşimli, fsi.exe.
ms.date: 05/16/2016
ms.openlocfilehash: a461dd0eeff2de3d15e557ba37138fbd62ca43ba
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "33565811"
---
# <a name="f-interactive-options"></a>F# Etkileşimli Seçenekleri

> [!NOTE]
Bu makalede, şu anda Windows deneyimi yalnızca açıklanmıştır.  Yazılacak.

Bu konu tarafından desteklenen komut satırı seçeneklerini açıklar F# Interactive `fsi.exe`. F#Etkileşimli aynı komut satırı seçeneklerinin çoğunu kabul F# derleyici, ancak ayrıca bazı ek seçenekleri de kabul eder.

## <a name="using-f-interactive-for-scripting"></a>Kullanarak F# etkileşimli betik oluşturma
F#Etkileşimli `fsi.exe`, etkileşimli olarak başlatılabilir veya betik çalıştırmak için komut satırından başlatılabilir. Komut satırı sözdizimi

```
> fsi.exe [options] [ script-file [arguments] ]
```

Dosya uzantısı F# betik dosyaları `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tablonun F# etkileşimli seçenekleri
Aşağıdaki tablo tarafından desteklenen seçenekleri özetler F# etkileşimli. Bu seçenekler, komut satırında veya Visual Studio IDE ile ayarlayabilirsiniz. Visual Studio IDE'de bu seçenekleri ayarlamak için açın **Araçları** menüsünde **seçenekleri...** , ardından  **F# Araçları** düğümünü seçip alt  **F# etkileşimli**.

Listeleri göründüğü F# etkileşimli seçenek bağımsız değişkeni, liste öğeleri noktalı virgülle ayrılmış (`;`).

|Seçenek|Açıklama|
|------|-----------|
|**--**|Söyleyin için kullanılan F# kalan bağımsız değişkenleri komut satırı bağımsız değişkenleri olarak değerlendirilecek etkileşimli F# program veya komut dosyası kodu listesini kullanarak erişebileceğiniz **fsi.CommandLineArgs**.|
|**--checked**[**+**&#124;**-**]|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--codepage:&lt;int&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--consolecolors**[**+**&#124;**-**]|Çıkış, uyarı ve hata iletilerini renkte çıkarma.|
|**--crossoptimize**[**+**&#124;**-**]|Etkinleştirin veya zakazuje optimalizaci mezi moduly.|
|**--debug**[**+**&#124;**-**]<br /><br />**--hata ayıklama:**[**tam**&#124;**pdbonly**&#124;**taşınabilir**&#124;**katıştırılmış**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**tam**&#124;**pdbonly**&#124;**taşınabilir**&#124;**katıştırılmış**]|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--tanımlayın:&lt;dize&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--deterministic**[**+**&#124;**-**]|(Modülü sürüm GUID'si ve zaman damgası dahil) belirlenimci bir derleme oluşturur.|
|**--Yönet**|Bildirir F# dosyaları yükledikten veya verilen komut satırı üzerinde betiği çalıştırdıktan sonra çıkmak için etkileşimli.|
|**--fullpaths**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--GUI**[**+**&#124;**-**]|Etkinleştirir veya Windows Forms olay döngüsünü devre dışı bırakır. Varsayılan durumda etkindir.|
|**--Yardım**<br /><br />**-?**|Komut satırı sözdizimi ve her seçeneğin kısa bir açıklamasını görüntülemek için kullanılır.|
|**--lib:&lt;klasör listesi&gt;**<br /><br />**-I:&lt;klasör listesi&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--Yük:&lt;dosya adı&gt;**|Başlangıçta verilen kaynak kodu derler ve derlenmiş yükler F# oturuma oluşturur. Hedef kaynak gibi komut dosyası yönergeleri içeriyorsa **#use** veya **#load**, kullanmanız gereken **--kullanın** veya **#use** yerine **--yük** veya **#load**.|
|**--mlcompatibility**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--noframework**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md)|
|**--nologo**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--nowarn:&lt;uyarı listesi&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--en iyi duruma getirme**[**+**&#124;**-**]|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--preferreduilang:&lt;dil&gt;**| Tercih edilen çıkış dilini kültür adı (örneğin, es-ES, ja-JP) belirtir. |
|**--quiet**|Bastır F# etkileşimli derleyicisinin çıktısının **stdout** akış.|
|**--Teklif hata ayıklama**|Ek hata ayıklama bilgilerinin türetilmiştir ifadeler yayınlaması gerektiğini belirtir F# değişmez ve yansıtılan tanımlar. Hata ayıklama bilgileri için özel özniteliklerine eklenir bir F# ifadesi Ağaç düğümünün. Bkz: [kod tırnak işaretleri](code-quotations.md) ve [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124;**-**]|Etkinleştirmek veya etkileşimli modda sekme tamamlama devre dışı bırakın.|
|**--başvuru:&lt;dosya adı&gt;**<br /><br />**-r:&lt;dosya adı&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--shadowcopyreferences**[**+**&#124;**-**]|Tarafından kilitlenmiş gelen başvuruları engeller F# etkileşimli işlem.|
|**--simpleresolution**|Derleme başvurularının MSBuild çözünürlük yerine dizin tabanlı kuralları kullanarak çözer.|
|**--tailcalls**[**+**&#124;**-**]|Etkinleştirin veya tail özyinelemeli işlevler için kullanılabilmeleri yığın çerçevesinin tail IL yönergesinin kullanımını devre dışı. Bu seçenek varsayılan olarak etkindir.|
|**--targetprofile:&lt;dize&gt;**|Bu derlemenin hedef çerçeve profilini belirtir. Mscorlib veya netcore netstandard değerler geçerlidir.  Mscorlib varsayılandır.|
|**--kullanın:&lt;dosya adı&gt;**|Yorumlayıcıya verilen dosyanın başlangıçta ilk giriş olarak kullanılmasını bildirir.|
|**--utf8output**|Fsc.exe derleme seçeneği ile aynıdır. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--uyar:&lt;uyarı düzeyi&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için [derleyici seçenekleri](compiler-options.md).|

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[Derleyici Seçenekleri](compiler-options.md)|Kullanılabilir komut satırı seçeneklerini açıklar F# derleyicisi **fsc.exe**.|

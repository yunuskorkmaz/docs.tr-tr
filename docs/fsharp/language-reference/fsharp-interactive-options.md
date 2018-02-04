---
title: "F# Etkileşimli Seçenekleri"
description: "F # Etkileşimli tarafından desteklenen komut satırı seçenekleri hakkında bilgi edinin fsi.exe."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9f3e39b-ce6c-41ff-991f-0625f46441ae
ms.openlocfilehash: 0fc369993b3ee4c8a9139e4a365330197fe66946
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="f-interactive-options"></a>F# Etkileşimli Seçenekleri

> [!NOTE]
Bu makalede Windows deneyimi yalnızca şu anda açıklanmıştır.  Yazılacak.

Bu konu F # Etkileşimli tarafından desteklenen komut satırı seçeneklerini açıklar `fsi.exe`. F # Etkileşimli F # derleyici aynı komut satırı seçenekleri çoğunu kabul eder, ancak bazı ek seçenekleri de kabul eder.

## <a name="using-f-interactive-for-scripting"></a>F # etkileşimli komut dosyası için kullanarak
F # Etkileşimli, `fsi.exe`, etkileşimli olarak başlatılabilir veya bir komut dosyasını çalıştırmak için komut satırından başlatılabilir. Komut satırı sözdizimi

```
> fsi.exe [options] [ script-file [arguments] ]
```

F # komut dosyaları için dosya uzantısı `.fsx`.

## <a name="table-of-f-interactive-options"></a>F # Etkileşimli Seçenekleri Tablosu
F # Etkileşimli tarafından desteklenen seçenekleri aşağıdaki tabloda özetlenmiştir. Bu seçenekler, komut satırında veya Visual Studio IDE üzerinden ayarlayabilirsiniz. Visual Studio IDE içinde bu seçenekleri ayarlamak için açık **Araçları** menüsünde, select **seçenekleri...** , ardından **F # Araçları** düğümü ve select **F # Etkileşimli**.

F # Etkileşimli seçenek bağımsız değişkenlerinde listeler görünür burada liste öğeleri noktalı virgülle ayrılmış (`;`).

|Seçenek|Açıklama|
|------|-----------|
|**--**|F # kalan bağımsız değişkenleri, F # program veya listesini kullanarak kod içinde erişmek için komut dosyası komut satırı bağımsız değişkenleri işlemek için etkileşimli istemek üzere kullanılan **fsi.CommandLineArgs**.|
|**--checked**[**+**&#124;**-**]|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--codepage:&lt;int&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--crossoptimize**[**+**&#124;**-**]|Etkinleştirmek veya devre dışı çapraz modülü en iyi duruma getirme.|
|**--debug**[**+**&#124;**-**]<br /><br />**--debug:**[**full**&#124;**pdbonly**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**full**&#124;**pdbonly**]|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--tanımlayın:&lt;dize&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--Yönet**|F dosyaları yükleme veya komut satırında belirtilen betiği çalıştırdıktan sonra çıkmak için # etkileşimli bildirir.|
|**--fullpaths**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--gui**[**+**&#124;**-**]|Etkinleştirir veya Windows Forms olay döngüsünü devre dışı bırakır. Varsayılan etkindir.|
|**--Yardım**<br /><br />**-?**|Komut satırı sözdizimi ve her seçeneğin kısa bir açıklamasını görüntülemek için kullanılır.|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;folder-list&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--Yük:&lt;dosya adı&gt;**|Başlatma sırasında verilen kaynak kodu derler ve derlenen F # yapılarını oturuma yükler. Hedef kaynak komut dosyası yönergeleri gibi içeriyorsa **#use** veya **#load**, kullanmalısınız sonra **--kullanmak** veya **#use** yerine**--yük** veya **#load**.|
|**--mlcompatibility**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--noframework**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md)|
|**--nologo**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--nowarn:&lt;uyarı listesi&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--optimize**[**+**&#124;**-**]|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--preferreduilang:&lt;lang&gt;**| Tercih edilen çıkış dil kültür adı (örneğin, es-ES, ja-JP) belirtir. |
|**--Sessiz**|F # Etkileşimli çıktısını bastırmak **stdout** akış.|
|**--quotations-debug**|Ek hata ayıklama bilgileri, F # tırnak değişmez değerleri türetilmiş ve tanımları yansıtılan ifadeler yayınlaması gerektiğini belirtir. Hata ayıklama bilgileri bir F # ifade Ağaç düğümünün özel öznitelikleri eklenir. Bkz: [kod tırnak işaretleri](code-quotations.md) ve [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124;**-**]|Etkinleştirmek veya etkileşimli modda sekme tamamlama devre dışı.|
|**--başvuru:&lt;dosya adı&gt;**<br /><br />**-r:&lt;dosya adı&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--tailcalls**[**+**&#124;**-**]|Etkinleştirmek veya tail özyinelemeli işlevler için yeniden yığın çerçevesi neden olan kuyruk IL yönerge kullanımını devre dışı bırakın. Bu seçenek varsayılan olarak etkindir.|
|**--kullanın:&lt;dosya adı&gt;**|Verilen dosyanın başlangıçta ilk giriş olarak kullanılacak yorumlayıcı söyler.|
|**--utf8output**|Fsc.exe derleyici seçeneği ile aynıdır. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--uyar:&lt;uyarı düzeyi&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|Aynı **fsc.exe** derleyici seçeneği. Daha fazla bilgi için bkz: [derleyici seçenekleri](compiler-options.md).|

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[Derleyici Seçenekleri](compiler-options.md)|F # derleyici, için kullanılabilen komut satırı seçeneklerini açıklar **fsc.exe**.|

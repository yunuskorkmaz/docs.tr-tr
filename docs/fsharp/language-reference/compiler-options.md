---
title: Derleyici Seçenekleri
description: Kullanım F# derlemesini denetlemek için derleyici komut satırı seçenekleri, F# uygulamalar ve kitaplıklar.
ms.date: 12/10/2018
ms.openlocfilehash: d8e4331bcacd7082d7560ddc6fcadb4ce2b61cf8
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614499"
---
# <a name="compiler-options"></a>Derleyici Seçenekleri

Bu konuda, derleyici komut satırı seçeneklerini açıklar F# derleyicisi, fsc.exe. Derleme ortamı proje özelliklerini ayarlayarak da kontrol edilebilir.


## <a name="compiler-options-listed-alphabetically"></a>Alfabetik Listelenmiş Derleyici Seçenekleri
Alfabetik listelenmiş derleyici seçenekleri aşağıdaki tabloda gösterilmektedir. Bazı F# derleyici seçenekleri benzer C# derleyici seçenekleri. Bu durumda, bir bağlantı olup olmadığını C# derleme seçenekleri konusu sağlanır.



|Derleyici seçeneği|Açıklama|
|---------------|-----------|
|`-a filename.fs`|Belirtilen dosyadan bir kitaplığı oluşturur. Bu seçenek öğesinin kısa biçimidir `--target:library filename.fs`.|
|`--baseaddress:address`|Bir DLL yüklemek için tercih edilen temel adresini belirtir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;baseaddress &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|`--codepage:id`|Gerekli sayfa sistemi için geçerli varsayılan kod sayfası yoksa, derleme sırasında kullanılacak kod sayfasını belirtir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;kod sayfaları &#40;C&#35; derleyici seçenekleri&#41;](../../csharp/language-reference/compiler-options/codepage-compiler-option.md).|
|`--consolecolors`|Hataları ve Uyarıları konsolda renk kodlu metni kullandığını belirtir.|
|`--crossoptimize[+|-]`|Etkinleştirir veya zakazuje optimalizaci mezi devre dışı bırakır.|
|<code>--delaysign[+&#124;-]</code>|Gecikmeli imzalar tanımlayıcı ad anahtarının yalnızca ortak kısmını kullanarak derleme.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;delaysign &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|<code>--checked[+&#124;-]</code>|Etkinleştirir veya taşma denetimleri oluşturma devre dışı bırakır.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;kullanıma &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|<code>--debug[+&#124;-]</code><br /><br /><code>-g[+&#124;-]</code><br /><br /><code>--debug:[full&#124;pdbonly]</code><br /><br /><code>-g: [full&#124;pdbonly]</code>|Etkinleştirir veya hata ayıklama bilgisi oluşturmayı devre dışı bırakır veya oluşturulacak hata ayıklama bilgisinin türünü belirtir. Varsayılan, çalışan bir programa eklemeye izin veren tam türdür. Seçin **pdbonly** pdb (program veritabanı) dosyasında depolanan sınırlı hata ayıklama bilgileri alınamıyor.<br /><br />Eşdeğer C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için bkz.<br /><br />[&#47;hata ayıklama &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx).|
|`--define:symbol`<br /><br />`-d:symbol`|Koşullu derlemede kullanılan bir sembolü tanımlar.|
|<code>--deterministic[+&#124;-]</code>|(Modülü sürüm GUID'si ve zaman damgası dahil) belirlenimci bir derleme oluşturur. Bu seçenek, joker karakter sürüm numaraları kullanılamaz ve yalnızca katıştırılmış ve taşınabilir hata ayıklama türlerini destekler|
|`--doc:xmldoc-filename`|Derleyicinin, belirtilen dosyaya XML belgeleri yorumları bildirir. Daha fazla bilgi için [XML belgeleri](xml-documentation.md).<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;doc &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|`--fullpaths`|Derleyicinin tam olarak nitelenmiş yollar oluşturmasını yönlendirir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;fullpaths &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/d315xc66.aspx).|
|`--help`<br /><br />`-?`|Tüm derleyici seçeneklerinin kısa bir açıklama da dahil olmak üzere, kullanım bilgilerini görüntüler.|
|<code>--highentropyva[+&#124;-]</code>|Etkinleştirmek veya yüksek entropili rastgele adres alanı düzenini (ASLR), Gelişmiş bir güvenlik özelliği devre dışı bırakın. İşletim sistemini nerede (örneğin, yığın ve yığın) uygulamalar için altyapının yüklendiği bellek konumlarını rasgele olarak belirler. Bu seçeneği etkinleştirirseniz, işletim sistemlerinin 64 bit bir makineye tam 64 bit adres alanı kullanmak için bu rastgele işlemini kullanabilirsiniz.|
|`--keycontainer:key-container-name`|Tanımlayıcı ad anahtar kapsayıcısı belirtir.|
|`--keyfile:filename`|Oluşturulan derlemeyi imzalamak için bir genel anahtar dosyasının adını belirtir.|
|`--lib:folder-name`<br /><br />`-I:folder-name`|Başvurulan derlemeler için aranacak dizini belirtir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;LIB &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|`--linkresource:resource-info`|Belirtilen bir kaynağı derlemeye bağlar. Kaynak bilgisinin biçimi <code>filename[name[public&#124;private]]</code><br /><br />Bu seçenek ile tek bir kaynağı bağlama, alternatif bir tüm kaynak dosyasını ekleme, `--resource` seçeneği.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;linkresource &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|`--mlcompatibility`|Diğer ML sürümleriyle uyumluluk için tasarlanmış özellikleri kullandığınızda görünen uyarıları yok sayar.|
|`--noframework`|.NET Framework derleyicisinde varsayılan başvuruyu devre dışı bırakır.|
|`--nointerfacedata`|İçeren bir derleme için normalde ekler kaynak atlamak için derleyiciye F#-belirli meta veriler.|
|`--nologo`|Derleyiciyi başlatırken başlık metnini göstermez.|
|`--nooptimizationdata`|Yalnızca satır içi yapıları uygulamak için önemli iyileştirme dahil etmek için derleyicinin sağlar. Çapraz-modül inlining'i engeller ancak ikili uyumluluğu artırır.|
|`--nowin32manifest`|Derleyicinin Varsayılan Win32 bildirimini yok sağlar.|
|`--nowarn:warning-number-list`|Sayılarına göre listelenen belirli uyarıları devre dışı bırakır. Her uyarı numarasını virgülle ayırın. Uyarı numarasını derleme çıktısından herhangi bir uyarının bulabilir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;nowarn &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|<code>--optimize[+&#124;-][optimization-option-list]</code><br /><br /><code>-O[+&#124;-] [optimization-option-list]</code>|Etkinleştirir veya iyileştirmeleri devre dışı bırakır. Bazı iyileştirme seçenekleri devre dışı veya seçmeli olarak listelenerek etkin. Bunlar: `nojitoptimize`, `nojittracking`, `nolocaloptimize`, `nocrossoptimize`, `notailcalls`.|
|`--out:output-filename`<br /><br />`-o:output-filename`|Derlenmiş bütünleştirilmiş kod veya modül adını belirtir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;kullanıma &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|`--pdb:pdb-filename`|Hata ayıklama PDB (program veritabanı) çıktı dosyasını adlandırır. Bu seçenek yalnızca olduğunda geçerlidir `--debug` de etkinleştirilir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;pdb &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/ms228625.aspx).|
|`--platform:platform-name`|Oluşturulan kodun yalnızca belirtilen platformda çalışacağını belirtir. (`x86`, `Itanium`, veya `x64`), veya platform adı `anycpu` seçilir, oluşturulan kodu herhangi bir platformda çalışacağını belirtir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;platform &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|`--preferreduilang:lang`| Tercih edilen çıkış dilini kültür adını belirtir (örneğin, `es-ES`, `ja-JP`). |
|`--quotations-debug`|Ek hata ayıklama bilgilerinin türetilmiştir ifadeler yayınlaması gerektiğini belirtir F# değişmez ve yansıtılan tanımlar. Hata ayıklama bilgileri için özel özniteliklerine eklenir bir F# ifadesi Ağaç düğümünün. Bkz: [kod tırnak işaretleri](code-quotations.md) ve [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|`--reference:assembly-filename`<br /><br />`-r:assembly-filename`|Yapar koddan bir F# veya .NET Framework derlemesinin derlenen kod için kullanılabilir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;başvuru &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|`--resource:resource-filename`|Yönetilen kaynak dosyasını oluşturulan derlemeye gömer.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;kaynak &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|`--sig:signature-filename`|Oluşturulan derleme üzerine dayalı bir imza dosyası oluşturur. İmza dosyaları hakkında daha fazla bilgi için bkz. [imzaları](signatures.md).|
|`--simpleresolution`|Derleme başvurularının MSBuild çözünürlük yerine dizin tabanlı Mono kuralları kullanılarak çözülmesi gerektiğini belirtir. Mono altında çalışması dışında MSBuild çözünürlüğü kullanılır varsayılandır.|
|`--standalone`|Tüm bağımlılıklarını içeren ve böylece tek başına ek derlemelere gerek kalmadan gibi çalıştığı bir derleme üretmeyi belirtir F# kitaplığı.|
|`--staticlink:assembly-name`|Verilen derleme ve bu derlemeye dayanan tüm dll statik olarak bağlar. DLL adını değil derleme adını kullanın.|
|`--subsystemversion`|Oluşturulan yürütülebilir dosya tarafından kullanılan işletim sisteminin alt sürümünü belirtir. Windows 8.1, Windows 7, Windows Vista için 6.00 için 6.01 için 6.02 kullanın. Bu seçenek, yalnızca yürütülebilir dosyaları, DLL'ler değil uygular ve uygulamanızın, yalnızca belirli işletim sistemi sürümlerinde kullanılabilir olan belirli güvenlik özelliklerine bağımlı ise kullanılması. Bu seçenek kullanılır ve kullanıcı uygulamanızı daha düşük bir işletim sistemi sürümünde yürütmeyi denerse bir hata iletisiyle başarısız olur.|
|<code>--tailcalls[+&#124;-]</code>|Etkinleştirir veya tail özyinelemeli işlevler için kullanılabilmeleri yığın çerçevesinin tail IL yönergesinin kullanımını devre dışı bırakır. Bu seçenek varsayılan olarak etkindir.|
|<code>--target:[exe&#124;winexe&#124;library&#124;module] filename</code>|Oluşturulan derlenmiş kodun türünü ve dosya adını belirtir.<ul><li>`exe` bir konsol uygulaması anlamına gelir.<br /></li><li>`winexe` tanımlanmış standart giriş/çıkış akışlarına (stdin, stdout ve stderr) sahip değil konsol uygulamasından farklı olan bir Windows uygulaması anlamına gelir.<br /></li><li>`library` Giriş noktası olmayan bir derlemedir.<br /></li><li>`module` Daha sonra derlemeye diğer modüller ile birleştirilebilir bir .NET Framework modülüdür (.netmodule) var.<br /></li><ul/>Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;hedef &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|`--times`|Derleme için zamanlama bilgilerini görüntüler.|
|`--utf8output`|Derleyici çıkışını UTF-8 kodlaması ile yazdırmayı etkinleştirir.|
|`--warn:warning-level`|Bir uyarı seviyesi (0-5) ayarlar. Varsayılan Düzey 3'tür. Her uyarıya önemine göre bir düzey verilir. Düzey 5 düzey 1'den daha fazla, ancak daha az önemli, uyarılar verir.<br /><br />Düzey 5 uyarıları şunlardır: (çalışma zamanında işaretlenmiş özyinelemeli kullanım) 21, 22 (`let rec` sipariş dışında değerlendirilen), (tam soyutlama) 45 ve (savunma kopyası) 52. Diğer tüm uyarılar Düzey 2'dir.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;uyar &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|`--warnon:warning-number-list`|Varsayılan olarak kapalı olabilir veya başka bir komut satırı seçeneği tarafından devre dışı belirli uyarıları etkinleştirin. İçinde F# 3.0, yalnızca 1182 (kullanılmayan değişkenler) uyarısı varsayılan olarak kapalıdır.|
|<code>--warnaserror[+&#124;-] [warning-number-list]</code>|Etkinleştirir veya rapor uyarıları hata olarak seçeneği devre dışı bırakır. Etkin veya devre dışı bırakılacak uyarılara belirli sayılar sağlayabilir. Daha sonra komut satırı seçenekleri komut satırında daha önceki seçenekleri geçersiz kılar. Örneğin uyarıları hatalar bildirmek istemediğinizi belirtmek için belirtin `--warnaserror+` `--warnaserror-:warning-number-list`.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;warnaserror &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|`--win32manifest:manifest-filename`|Derlemeye Win32 bildirim dosyası ekler. Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;win32manifest &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/bb545961.aspx).|
|`--win32res:resource-filename`|Derlemeye bir Win32 kaynak dosyası ekler.<br /><br />Bu derleyici seçeneğini eşdeğerdir C# derleyici seçeneği aynı ada sahip. Daha fazla bilgi için [ &#47;win32res (&#40;C&#35;) derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-articles"></a>İlgili makaleler

|Başlık|Açıklama|
|-----|-----------|
|[F# Interactive Seçenekleri](fsharp-interactive-options.md)|Tarafından desteklenen komut satırı seçeneklerini açıklar F# Yorumlayıcı, fsi.exe.|
|[Proje Özellikleri Başvurusu](/visualstudio/ide/reference/project-properties-reference)|Yapı seçeneklerini sağlayan proje özellik sayfaları dahil olmak üzere, projeler için kullanıcı arabirimini açıklar.|
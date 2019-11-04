---
title: Derleyici Seçenekleri
description: Uygulama F# ve kitaplıklarınızın F# derlemesini denetlemek için derleyici komut satırı seçeneklerini kullanın.
ms.date: 12/10/2018
ms.openlocfilehash: d0f4d1ca5ae45af25d6c304a2920d5c457700b1a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424754"
---
# <a name="compiler-options"></a>Derleyici Seçenekleri

Bu konu, FSC. exe F# derleyicisi için derleyici komut satırı seçeneklerini açıklar. Derleme ortamı, proje özellikleri ayarlanarak de denetlenebilir.

## <a name="compiler-options-listed-alphabetically"></a>Alfabetik Listelenmiş Derleyici Seçenekleri

Aşağıdaki tabloda alfabetik olarak listelenen derleyici seçenekleri gösterilmektedir. F# Derleyici seçeneklerinin bazıları C# derleyici seçeneklerine benzer. Bu durumda, C# derleyici seçenekleri konusuna bir bağlantı sağlanır.

|Derleyici seçeneği|Açıklama|
|---------------|-----------|
|`-a filename.fs`|Belirtilen dosyadan bir kitaplık oluşturur. Bu seçenek `--target:library filename.fs`kısa bir biçimidir.|
|`--baseaddress:address`|DLL 'nin yükleneceği tercih edilen temel adresi belirtir.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;BaseAddress&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|`--codepage:id`|Gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse, derleme sırasında hangi kod sayfasının kullanılacağını belirtir.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. Code &#40;Pages&#35; C derleyici&#41;seçenekleri](../../csharp/language-reference/compiler-options/codepage-compiler-option.md).|
|`--consolecolors`|Hataların ve uyarıların konsolda renk kodlu metin kullanılacağını belirtir.|
|`--crossoptimize[+|-]`|Modüller arası iyileştirmeleri etkinleştirilir veya devre dışı bırakır.|
|<code>--delaysign[+&#124;-]</code>|Derlemeyi yalnızca tanımlayıcı ad anahtarının ortak kısmını kullanarak imzalar.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;delaysign&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|<code>--checked[+&#124;-]</code>|Taşma denetimlerinin oluşturulmasını etkinleştirilir veya devre dışı bırakır.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;Checked&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|<code>--debug[+&#124;-]</code><br /><br /><code>-g[+&#124;-]</code><br /><br /><code>--debug:[full&#124;pdbonly]</code><br /><br /><code>-g: [full&#124;pdbonly]</code>|Hata ayıklama bilgilerinin oluşturulmasını sağlar veya devre dışı bırakır veya oluşturulacak hata ayıklama bilgilerinin türünü belirtir. Varsayılan değer, çalışan bir programa eklemeye izin veren tam bir programdır. Pdb (program veritabanı) dosyasında depolanan sınırlı hata ayıklama bilgilerini almak için **pdbonly** öğesini seçin.<br /><br />Aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz.<br /><br />[hata ayıklama &#40;&#35; C derleyici seçenekleri&#41; &#47;](https://msdn.microsoft.com/library/8cw0bt21.aspx)|
|`--define:symbol`<br /><br />`-d:symbol`|Koşullu derlemede kullanılmak üzere bir sembol tanımlar.|
|<code>--deterministic[+&#124;-]</code>|Belirleyici derleme üretir (Modül sürümü GUID 'i ve zaman damgası dahil). Bu seçenek joker karakter sürüm numaralarıyla kullanılamaz ve yalnızca gömülü ve taşınabilir hata ayıklama türlerini destekler|
|`--doc:xmldoc-filename`|Derleyiciye XML belge açıklamalarını belirtilen dosyada oluşturmasını söyler. Daha fazla bilgi için bkz. [XML belgeleri](xml-documentation.md).<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;doc&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|`--fullpaths`|Derleyiciye tam nitelikli yollar oluşturmasını söyler.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;fullpaths&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/d315xc66.aspx).|
|`--help`<br /><br />`-?`|Tüm derleyici seçeneklerinin kısa bir açıklaması dahil olmak üzere kullanım bilgilerini görüntüler.|
|<code>--highentropyva[+&#124;-]</code>|Gelişmiş bir güvenlik özelliği olan yüksek entroksiz adres alanı düzeni rastgele seçme (ASLR) özelliğini etkinleştirin veya devre dışı bırakın. İşletim sistemi, uygulamalar için altyapının (yığın ve yığın gibi) yüklendiği bellekteki konumları rasgeleleştirir. Bu seçeneği etkinleştirirseniz, işletim sistemleri 64 bit bir makinede tam 64 bit adres alanı kullanmak için bu rastgele seçimi kullanabilir.|
|`--keycontainer:key-container-name`|Bir tanımlayıcı ad anahtar kapsayıcısı belirtir.|
|`--keyfile:filename`|Oluşturulan derlemeyi imzalamak için ortak anahtar dosyasının adını belirtir.|
|`--lib:folder-name`<br /><br />`-I:folder-name`|Başvurulan derlemeler için aranacak dizini belirtir.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;LIB&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|`--linkresource:resource-info`|Belirtilen bir kaynağı derlemeye bağlar. Kaynak-bilgi biçimi <code>filename[name[public&#124;private]]</code><br /><br />Tek bir kaynağı bu seçenekle bağlamak, bir kaynak dosyasının tamamını `--resource` seçeneğiyle katıştırmaya alternatiftir.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;linkresource&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|`--mlcompatibility`|Diğer ML sürümleriyle uyumluluk için tasarlanan özellikleri kullandığınızda görüntülenen uyarıları yoksayar.|
|`--noframework`|.NET Framework derlemesine varsayılan başvuruyu devre dışı bırakır.|
|`--nointerfacedata`|Derleyiciye, normal olarak belirli meta verileri içeren bir derlemeye F#eklediği kaynağı atmasını söyler.|
|`--nologo`|Derleyiciyi başlatırken başlık metnini göstermez.|
|`--nooptimizationdata`|Derleyiciye yalnızca satır içine alınmış yapıları uygulamak için gereken en iyi duruma getirmeyi sağlar. Çapraz modüllü girişi engeller, ancak ikili uyumluluğu geliştirir.|
|`--nowin32manifest`|Derleyicinin varsayılan Win32 bildirimini yok saymasını söyler.|
|`--nowarn:warning-number-list`|Sayıyla listelenen belirli uyarıları devre dışı bırakır. Her uyarı numarasını virgülle ayırın. Herhangi bir uyarının uyarı numarasını derleme çıktısından bulabilirsiniz.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;nowarn&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|<code>--optimize[+&#124;-][optimization-option-list]</code><br /><br /><code>-O[+&#124;-] [optimization-option-list]</code>|İyileştirmeleri etkinleştirilir veya devre dışı bırakır. Bazı iyileştirme seçenekleri, seçilerek seçilerek devre dışı bırakılabilir veya etkinleştirilebilir. Bunlar şunlardır: `nojitoptimize`, `nojittracking`, `nolocaloptimize`, `nocrossoptimize`, `notailcalls`.|
|`--out:output-filename`<br /><br />`-o:output-filename`|Derlenen derleme veya modülün adını belirtir.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|`--pdb:pdb-filename`|Çıkış hata ayıklama PDB (program veritabanı) dosyasını adlandırır. Bu seçenek yalnızca `--debug` de etkinleştirildiğinde geçerlidir.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;pdb&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/ms228625.aspx).|
|`--platform:platform-name`|Oluşturulan kodun yalnızca belirtilen platformda (`x86`, `Itanium`veya `x64`) çalışacağını veya platform adı `anycpu` seçilirse, oluşturulan kodun herhangi bir platformda çalışacağını belirtir.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;Platform&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|`--preferreduilang:lang`| Tercih edilen çıkış dili kültür adını belirtir (örneğin, `es-ES`, `ja-JP`). |
|`--quotations-debug`|Ek hata ayıklama bilgilerinin, alıntı sabit değerleri ve yansıtılan tanımlardan F# türetilmiş ifadeler için yayınlanmasının gerektiğini belirtir. Hata ayıklama bilgileri, bir F# ifade ağacı düğümünün özel özniteliklerine eklenir. Bkz. [kod teklifleri](code-quotations.md) ve [Expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|`--reference:assembly-filename`<br /><br />`-r:assembly-filename`|F# Veya .NET Framework derlemeden kod, derlenen kod için kullanılabilir hale gelir.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;Reference&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|`--resource:resource-filename`|Yönetilen bir kaynak dosyasını oluşturulan derlemeye gömer.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;Resource&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|`--sig:signature-filename`|Oluşturulan derlemeye dayalı bir imza dosyası oluşturur. İmza dosyaları hakkında daha fazla bilgi için bkz. [imzalar](signature-files.md).|
|`--simpleresolution`|Derleme başvurularının, MSBuild çözümlemesi yerine dizin tabanlı Mono kuralları kullanılarak çözülmesi gerektiğini belirtir. Varsayılan değer, Mono altında çalıştırmanın dışında MSBuild çözümlemesi kullanmaktır.|
|`--standalone`|F# Kitaplık gibi ek derlemeler gerekmeden kendisi tarafından çalışacak şekilde tüm bağımlılıklarını içeren bir derleme oluşturmak için belirtir.|
|`--staticlink:assembly-name`|Verilen derlemeyi ve bu derlemeye bağlı tüm başvurulan DLL 'Leri statik olarak bağlar. DLL adını değil, derleme adını kullanın.|
|`--subsystemversion`|Oluşturulan yürütülebilir dosya tarafından kullanılacak işletim sistemi alt sisteminin sürümünü belirtir. Windows 8.1, Windows 7 için 6,01, Windows Vista için 6,00 6,02 kullanın. Bu seçenek yalnızca yürütülebilir dosyalar için geçerlidir, dll 'Ler için geçerli olur ve yalnızca uygulamanız yalnızca belirli işletim sistemi sürümlerinde kullanılabilir olan belirli güvenlik özelliklerine bağımlıysa kullanılması gerekir. Bu seçenek kullanılırsa ve bir Kullanıcı, uygulamanızı işletim sisteminin daha düşük bir sürümünde yürütmeyi denerse bir hata iletisiyle başarısız olur.|
|<code>--tailcalls[+&#124;-]</code>|Tail Özyinelemeli işlevler için yığın çerçevesinin yeniden kullanılmasını sağlayan tail Il yönergesinin kullanımını sağlar veya devre dışı bırakır. Bu seçenek varsayılan olarak etkindir.|
|<code>--target:[exe&#124;winexe&#124;library&#124;module] filename</code>|Oluşturulan derlenmiş kodun türünü ve dosya adını belirtir.<ul><li>`exe`, bir konsol uygulaması anlamına gelir.<br /></li><li>`winexe`, tanımlı standart giriş/çıkış akışları (stdin, STDOUT ve stderr) bulunmayan konsol uygulamasından farklı olan bir Windows uygulaması anlamına gelir.<br /></li><li>`library`, giriş noktası olmayan bir derlemedir.<br /></li><li>`module`, daha sonra bir derlemede diğer modüllerle birleştirilebilecek bir .NET Framework modülüdür (. netmodule).<br /></li><ul/>Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;Target&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|`--times`|Derleme için zamanlama bilgilerini görüntüler.|
|`--utf8output`|Derleyici çıkışının UTF-8 kodlaması içinde yazdırılmasını mümkün.|
|`--warn:warning-level`|Bir uyarı düzeyi (0-5) ayarlar. Varsayılan düzey 3 ' dir. Her uyarıya önem derecesine göre bir düzey verilir. Düzey 5, düzey 1 ' den daha fazla, ancak daha az ciddi uyarılar sunar.<br /><br />Düzey 5 uyarıları: 21 (çalışma zamanında denetlenen yinelemeli kullanım), 22 (`let rec` sıra dışı), 45 (tam soyutlama) ve 52 (savunmalı kopya). Diğer tüm uyarılar düzey 2 ' dir.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;warn&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|`--warnon:warning-number-list`|Varsayılan olarak kapalı olabilecek veya başka bir komut satırı seçeneği tarafından devre dışı bırakılmış belirli uyarıları etkinleştirin. 3,0 F# ' de, varsayılan olarak yalnızca 1182 (kullanılmayan değişkenler) uyarısı kapalıdır.|
|<code>--warnaserror[+&#124;-] [warning-number-list]</code>|Uyarıları hata olarak bildirme seçeneğini sağlar veya devre dışı bırakır. Devre dışı bırakılacak veya etkinleştirilecek belirli uyarı numaralarını sağlayabilirsiniz. Komut satırında daha sonra bulunan seçenekler, komut satırında daha önce olan seçenekleri geçersiz kılar. Örneğin, hata olarak bildirilmesini istemediğiniz uyarıları belirtmek için `--warnaserror+` `--warnaserror-:warning-number-list`belirtin.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;warnaserror&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|`--win32manifest:manifest-filename`|Derlemeye bir Win32 bildirim dosyası ekler. Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. &#40;win32manifest&#35; C derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/bb545961.aspx).|
|`--win32res:resource-filename`|Derlemeye bir Win32 kaynak dosyası ekler.<br /><br />Bu derleyici seçeneği aynı ada sahip C# derleyici seçeneğine eşdeğerdir. Daha fazla bilgi için bkz [ &#47;. win32res&#40;(&#35;C) derleyici&#41;seçenekleri](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-articles"></a>İlgili makaleler

|Başlık|Açıklama|
|-----|-----------|
|[F# Interactive Seçenekleri](fsharp-interactive-options.md)|, Fsi. exe F# yorumlayıcı tarafından desteklenen komut satırı seçeneklerini açıklar.|
|[Proje Özellikleri Başvurusu](/visualstudio/ide/reference/project-properties-reference)|Yapı seçenekleri sağlayan proje özellik sayfaları dahil olmak üzere projelere yönelik kullanıcı arabirimini açıklar.|

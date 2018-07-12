---
title: Derleyici Seçenekleri (F#)
description: 'F # uygulamalarınızı ve kitaplıkları derlenmesini denetlemek için F # derleyici komut satırı seçenekleri kullanın.'
ms.date: 05/16/2016
ms.openlocfilehash: f4a596d0dede6f66faa34374f7f73a89323f1620
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566450"
---
# <a name="compiler-options"></a>Derleyici Seçenekleri

Bu konu F # derleyici, derleyici komut satırı seçeneklerini açıklar fsc.exe. Derleme ortamı proje özelliklerini ayarlayarak da denetlenebilir.


## <a name="compiler-options-listed-alphabetically"></a>Alfabetik Listelenmiş Derleyici Seçenekleri
Alfabetik olarak listelenen derleyici seçenekleri aşağıdaki tabloda gösterilmektedir. F # derleyici seçenekleri bazıları, C# derleyici seçenekleri benzerdir. Bu durumda, C# derleyici seçenekleri konuya bir bağlantı sağlanır.



|Derleyici seçeneği|Açıklama|
|---------------|-----------|
|**-a ***&lt;çıkış dosyası adı&gt;**|Bir kitaplık oluşturur ve dosya adını belirtir. Bu seçenek kısa biçimidir **--target: library ***&lt;filename&gt;**.|
|**--baseaddress:&lt;dize&gt;**|Oluşturulacak kitaplığın temel adresini belirtir.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;baseaddress &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|**--codepage:&lt;int&gt;**|Kaynak dosyaları okumak için kullanılan kod sayfasını belirtir.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;codepage &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/w0kyekyh.aspx).|
|**--consolecolors**|Hataları ve Uyarıları ren kodlu metin konsolda kullandığını belirtir.|
|**--crossoptimize**[**+**&#124;**-**]|Etkinleştirir veya çapraz modülü iyileştirmeleri devre dışı bırakır.|
|**--delaysign**[**+**&#124;**-**]|Gecikmeli imzalar güçlü ad anahtarı yalnızca ortak kısmını kullanarak derleme.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;delaysign &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|**--checked**[**+**&#124;**-**]|Etkinleştirir ya da taşma denetimleri oluşturmayı devre dışı bırakır.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;işaretli &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|**--debug**[**+**&#124;**-**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**--debug**:[**full**&#124;**pdbonly**]<br /><br />**-g:** [**tam**&#124;**pdbonly**]|Etkinleştirir ya da hata ayıklama bilgileri oluşturma devre dışı bırakır veya oluşturmak için hata ayıklama bilgi türünü belirtir. Çalışan bir program bağlanmasını sağlayan tam, varsayılandır. Seçin **pdbonly** pdb (program veritabanı) dosyasında depolanan sınırlı hata ayıklama bilgilerini almak için.<br /><br />C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz.<br /><br />[&#47;hata ayıklama &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx).|
|**--tanımlayın:&lt;dize&gt;**<br /><br />**-d:&lt;dize&gt;**|Kullanmak için bir simge koşullu derlemede tanımlar.|
|**--deterministic**[**+**&#124;**-**]|(Modül sürümü GUID ve zaman damgası dahil) belirleyici bir derleme üretme.  Bu joker karakter sürüm numaralarıyla kullanılamaz ve yalnızca katıştırılmış ve taşınabilir hata ayıklama türlerini destekler|
|**--Belge:&lt;xmldoc filename&gt;**|XML belgeleri yorumları belirtilen dosyaya oluşturmak için derleyiciye. Daha fazla bilgi için bkz: [XML belgeleri](xml-documentation.md).<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;belge &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|**--fullpaths**|Tam yollar oluşturmak için derleyiciye.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;fullpaths &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/d315xc66.aspx).|
|**--Yardım**<br /><br />**-?**|Derleyici Seçenekleri kısa bir açıklaması da dahil olmak üzere kullanım bilgilerini görüntüler.|
|**--highentropyva**[**+**&#124;**-**]|Etkinleştirmek veya yüksek entropi adres boşluğu düzeni rastgele seçimini (ASLR), Gelişmiş bir güvenlik özelliği devre dışı. İşletim sistemi bellek konumlarda (yığın ve Öbek gibi) uygulamalar için altyapı burada yüklenen randomizes. Bu seçeneği etkinleştirirseniz, işletim sistemlerinin 64-bit makine üzerinde tam 64-bit adres alanı kullanmak için bu rastgele kullanabilirsiniz.|
|**--keycontainer:&lt;dize&gt;**|Güçlü ad anahtar kapsayıcısı belirtir.|
|**--keyfile:&lt;dosya adı&gt;**|Oluşturulan derleme imzalama için ortak anahtar dosya adını belirtir.|
|**--lib:&lt;klasör adı&gt;**<br /><br />**-I:&lt;klasör adı&gt;**|Başvurulan derlemeler için aranacak bir dizini belirtir.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;lib &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|**--linkresource**:**&lt;resource-info&gt;**|Belirtilen kaynak derlemeye bağlar. Kaynak bilgileri biçimi *filename*[,*adı*[,*ortak*&#124;*özel*]]<br /><br />Bu seçenek ile tek bir kaynağı bağlama olduğu tüm kaynak dosyayla katıştırma alternatif **--kaynak** seçeneği.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;linkresource &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|**--mlcompatibility**|Diğer ML sürümleri ile uyumluluk için tasarlanmış özelliklerle kullandığınızda görünen uyarıları göz ardı eder.|
|**--noframework**|.NET Framework derlemesinin varsayılan referansı devre dışı bırakır.|
|**--nointerfacedata**|F # içeren bir derleme normalde ekler kaynak atlamak için derleyiciye-belirli meta veriler.|
|**--nologo**|Başlık metni derleyici başlatılırken göstermez.|
|**--nooptimizationdata**|Yalnızca en iyi duruma getirme içermesinden yapıları uygulamak için temel dahil etmek derleyiciye. Çapraz modülü satır içi kullanım engeller, ancak ikili uyumluluğu artırır.|
|**--nowin32manifest**|Varsayılan Win32 bildirimi atlamak için derleyiciye.|
|**--nowarn:&lt;int listesi&gt;**|Numarasına göre listelenen belirli uyarıları devre dışı bırakır. Her uyarı numarasını virgülle ayırın. Derleme çıktısından herhangi bir uyarı uyarı numarasını bulabilir.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;nowarn &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|**--optimize**[**+**&#124;**-**]**[&lt;string-list&gt;]**<br /><br />**-O [+&#124;-] [&lt;dize listesi&gt;]**|Etkinleştirir veya en iyi duruma getirme devre dışı bırakır. Bazı en iyi duruma getirme seçenekleri devre dışı veya seçmeli olarak listeleniyor tarafından etkinleştirilmiş. Bunlar: **nojitoptimize**, **nojittracking**, **nolocaloptimize**, **nocrossoptimize**, **notailcalls**.|
|**--çıkışı:&lt;çıkış dosyası adı&gt;**<br /><br />**-o:&lt;çıkış dosyası adı&gt;**|Derlenmiş bir derlemeyi ya da modül adını belirtir.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;çıkışı &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|**--pdb:&lt;pdb Dosya adı&gt;**|Çıkış hata ayıklama PDB (program veritabanı) dosyası olarak adlandırır. Bu seçenek yalnızca zaman geçerlidir **--hata ayıklama** de etkinleştirilir.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;pdb &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/ms228625.aspx).|
|**--platform:&lt;platform-name&gt;**|Oluşturulan kodun yalnızca belirtilen platformda Çalıştır belirtir (**x86**, **Itanium**, veya **x64**), veya platform adı **anycpu**seçilir, oluşturulan kod herhangi bir platformda çalışması gerektiğini belirtir.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;platform &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|**--preferreduilang:&lt;lang&gt;**| Tercih edilen çıkış dil kültür adı (örneğin, es-ES, ja-JP) belirtir. |
|**--teklifleri hata ayıklama**|Ek hata ayıklama bilgileri, F # tırnak değişmez değerleri türetilmiş ve tanımları yansıtılan ifadeler yayınlaması gerektiğini belirtir. Hata ayıklama bilgileri bir F # ifade Ağaç düğümünün özel öznitelikleri eklenir. Bkz: [kod tırnak işaretleri](code-quotations.md) ve [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--başvuru:&lt;derleme dosya adı&gt;**<br /><br />**-r** &lt; **derleme dosya adı&gt;**|Kod bir F # veya .NET Framework derlemesindeki derlenmiş kod kullanılabilir hale getirir.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;başvuru &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|**--Kaynak:&lt;kaynak dosya adı&gt;**|Yönetilen kaynak dosyasını oluşturulan derlemeye katıştırır.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;kaynak &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|**--SIG**:&lt;**imza filename&gt;**|Oluşturulan derleme üzerine dayalı bir imza dosyası oluşturur. İmza dosyaları hakkında daha fazla bilgi için bkz: [imzalar](signatures.md).|
|**--simpleresolution**|Derleme başvurularını MSBuild çözünürlük yerine dizin tabanlı Mono kuralları kullanılarak çözülmesi gerektiğini belirtir. Mono altında çalışması dışında MSBuild çözümlemesini kullanmak için varsayılandır.|
|**--tek başına**|Tüm bağımlılıkları içerir ve böylece F # kitaplığı gibi ek derlemeler gerek kalmadan, tek başına çalıştığı bir derleme üretmek için belirtir.|
|**--staticlink:&lt;derleme adı**&gt;|Statik olarak verilen derleme ve bu derlemeye dayanan tüm dll bağlar. DLL adını değil derleme adı kullanın.|
|**--subsystemversion**|Oluşturulan yürütülebilir dosya tarafından kullanılan işletim sistemi alt sistemi sürümünü belirtir. Windows 8.1, Windows 7, Windows Vista için 6,00 6.01 için 6.02 kullanın. Bu seçenek yalnızca yürütülebilir dosyaları, DLL'ler değil uygular ve uygulamanızı belirli güvenlik özellikleri yalnızca belirli işletim sistemi sürümlerinde yapılandırmasanız kullanılması. Bu seçenek kullanılır ve bir kullanıcı daha düşük bir işletim sistemi sürümü, uygulamanızın yürütmeyi denediğinde, bir hata iletisiyle başarısız olur.|
|**--tailcalls**[**+**&#124;**-**]|Etkinleştirir veya tail özyinelemeli işlevler için yeniden yığın çerçevesi neden olan kuyruk IL yönerge kullanımını devre dışı bırakır. Bu seçenek varsayılan olarak etkindir.|
|**--Hedef**: [**exe** &#124; **winexe** &#124; **Kitaplığı** &#124; **Modülü** ]  **&lt;çıkış dosyası adı&gt;**|Oluşturulan derlenmiş kod türü ve dosya adını belirtir.<ul><li>**exe** bir konsol uygulaması anlamına gelir.<br /></li><li>**winexe** tanımlanan standart giriş/çıkış akışları (stdin, stdout ve stderr) yok konsol uygulamasından farklı olan bir Windows uygulaması anlamına gelir.<br /></li><li>**Kitaplık** bir giriş noktası olmadan bir derleme.<br /></li><li>**Modül** daha sonra diğer modüller ile bir derlemeye birleştirilebilir .NET Framework Modülü (.netmodule).<br /></li><ul/>Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;hedef &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|**--saatleri**|Derleme için bilgi zamanlama görüntüler.|
|**--utf8output**|UTF-8 kodlaması Derleyici çıktısı yazdırmayı etkinleştirir.|
|**--uyar:&lt;uyarı düzeyi&gt;**|Uyarı düzeyi (0-5) ayarlar. Varsayılan düzeyi 3'tür. Her uyarı önemine göre bir düzeyi verilir. Düzey 5 düzey 1'den daha fazla, ancak daha az önemli, uyarılar sağlar.<br /><br />Düzey 5 uyarıları şunlardır: (çalışma zamanında işaretli özyinelemeli kullanın) 21, 22 (**let rec** sıralama dışında hesaplanan), 45 (tam soyutlama) ile 52 (savunma kopya). Diğer tüm uyarıları 2 düzeyindedir.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;uyar &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|**--warnon:&lt;int-list&gt;**|Varsayılan olarak kapalı olabilir veya başka bir komut satırı seçeneği tarafından devre dışı bırakılan belirli uyarıları etkinleştirin. F # 3.0 sürümünde, yalnızca 1182 (kullanılmayan değişkenler) uyarı varsayılan olarak kapalıdır.|
|**--warnaserror**[**+**&#124;**-**] [**&lt;int-list&gt;**]|Etkinleştirir veya rapor uyarıları hata olarak seçeneği devre dışı bırakır. Özel uyarı numaraları etkin veya devre dışı bırakılacak sağlayabilir. Daha sonra komut satırı seçenekleri seçenekleri önceki komut satırında geçersiz kılar. Örneğin, hata olarak bildirilen istemediğiniz uyarıları belirtmek için belirtin **--warnaserror +--warnaserror-:&lt;int listesi&gt;**.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;warnaserror &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|**--win32manifest:manifest-filename**|Bir Win32 bildirim dosyası derleme ekler. Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;win32manifest &#40;C&#35; derleyici seçenekleri&#41;](https://msdn.microsoft.com/library/bb545961.aspx).|
|**--win32res:resource-filename**|Win32 kaynak dosyasını derleme ekler.<br /><br />Bu derleyici seçeneği C# derleyici seçeneği aynı ada eşdeğerdir. Daha fazla bilgi için bkz: [ &#47;win32res (&#40;C & #35); Derleyici Seçenekleri&#41;](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-topics"></a>İlgili Konular


|Başlık|Açıklama|
|-----|-----------|
|[F# Interactive Seçenekleri](fsharp-interactive-options.md)|F # yorumlayıcısı tarafından desteklenen komut satırı seçenekleri açıklanmıştır fsi.exe.|
|[Proje Özellikleri Başvurusu](/visualstudio/ide/reference/project-properties-reference)|Yapı seçeneklerini sağlayan proje özellik sayfalarını da dahil olmak üzere projelerde UI açıklar.|

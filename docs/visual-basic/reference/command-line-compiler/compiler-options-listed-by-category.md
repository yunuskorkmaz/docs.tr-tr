---
title: Kategoriye Göre Listelenmiş Visual Basic Derleyici Seçenekleri
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 8f09566585c06531a346b0143a6002c2854a0b01
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182559"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Kategoriye göre listelenmiş Visual Basic derleyici seçenekleri
Visual Basic komut satırı derleyicisi, Visual Studio tümleşik geliştirme ortamı (IDE) içinden program derlemek için alternatif olarak sağlanır. Aşağıda, işlevsel kategoriye göre sıralanan Visual Basic komut satırı derleyici seçeneklerinin bir listesi verilmiştir.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Derleyici çıkışı  
  
|Seçenek|Amaç|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Derleyici başlık bilgilerini gizler.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Derleme sırasında ek bilgi verir.|  
|`-modulename:<string>`|Kaynak modülünün adını belirtin|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Derleyici çıkışı için bir dil belirtin.|
  
## <a name="optimization"></a>İyileştirme  
  
|Seçenek|Amaç|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Çıktı dosyasının bölümlerinin hangi noktada hizalanacağını belirtir.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|İyileştirmeleri etkinleştirilir/devre dışı bırakır.|  
  
## <a name="output-files"></a>Çıkış dosyaları  
  
|Seçenek|Amaç|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Belge açıklamalarını bir XML dosyası ile işleyin.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Girişlerin özdeş olması halinde, derleyicinin ikili içerik özdeş olan bir derlemeyi çıkış yapmasına neden olur.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|.NET Compact Framework hedeflemek için derleyiciyi ayarlar.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Bir çıkış dosyasını belirtir.|  
|[-refonly](refonly-compiler-option.md)|Yalnızca bir başvuru derlemesini verir.|
|[-refout](refout-compiler-option.md)|Bir başvuru derlemesinin çıkış yolunu belirtir.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Çıkışın biçimini belirtir.|  
  
## <a name="net-assemblies"></a>.NET derlemeleri  
  
|Seçenek|Amaç|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Derlemenin tamamen veya kısmen imzalanacağını belirtir.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Belirtilen derlemeden bir ad alanı içeri aktarır.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Bir derlemeye tanımlayıcı ad vermek için bir anahtar çifti için anahtar kapsayıcısı adı belirtir.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Derlemeye tanımlayıcı ad vermek için bir anahtar veya anahtar çifti içeren bir dosya belirtir.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|[-Reference](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneğinin başvurduğu derlemelerin konumunu belirtir.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Meta verileri bir derlemeden içeri aktarır.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Modülün bir parçası olacağı derlemenin adını belirtir.|  
|`-analyzer`|Bu derlemeden çözümleyiciler çalıştırın (kısa biçim:-a)|  
|`-additionalfile`|Kod oluşturmayı doğrudan etkilemeyen, ancak hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilen ek dosyaları adlandırır.|  
  
## <a name="debuggingerror-checking"></a>Hata ayıklama/hata denetimi  
  
|Seçenek|Amaç|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Bir hatayı rapor etmelerini kolaylaştıran bilgiler içeren bir dosya oluşturur.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Hata ayıklama bilgileri üretir.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Derleyicinin uyarı oluşturma yeteneğini engeller.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Derleyicinin sözdizimiyle ilgili hatalar ve uyarılar için kod görüntülemesini engeller.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Tamsayı taşma denetimini devre dışı bırakır.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Hatalara yönelik uyarıları yükseltir.|  
|`-ruleset:<file>`|Belirli tanılamayı devre dışı bırakan bir RuleSet dosyası belirtin.|  
  
## <a name="help"></a>Yardım  
  
|Seçenek|Amaç|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçeneklerini görüntüler. Bu komut, `-help` seçeneğini belirtirken de aynıdır. Hiçbir derleme gerçekleşmez.|  
|[-yardım](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçeneklerini görüntüler. Bu komut, `-?` seçeneğini belirtirken de aynıdır. Hiçbir derleme gerçekleşmez.|  
  
## <a name="language"></a>Dil  
  
|Seçenek|Amaç|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Dil sürümünü belirtin: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Değişkenlerin açık bildirimini uygular.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Katı tür semantiğini zorlar.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Dize karşılaştırmalarının ikili mı yoksa yerel ayara özgü metin semantiğini mi kullanılacağını belirtir.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.|  
  
## <a name="preprocessor"></a>Ön işlemci  
  
|Seçenek|Amaç|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Koşullu derleme için sembolleri tanımlar.|  
  
## <a name="resources"></a>Kaynaklar  
  
|Seçenek|Amaç|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Yönetilen bir kaynağa bir bağlantı oluşturur.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Bir derlemede yönetilen bir kaynak gömer.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Çıkış dosyasına bir. ico dosyası ekler.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Çıktı dosyasına bir Win32 kaynağı ekler.|  
  
## <a name="miscellaneous"></a>Çeşitli  
  
|Seçenek|Amaç|  
|---|---|  
|[@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Bir yanıt dosyası belirtir.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|DLL 'nin temel adresini belirtir.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Visual Basic derleyicisinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Windows çekirdeğine, belirli bir yürütülebilir dosyanın yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini söyler.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Başlangıçta kullanılacak `Sub Main` yordamı içeren sınıfı belirtir.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Vbc. rsp ile derleme|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Derleyicinin standart kitaplıklara Başvurmamasını sağlar.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Derleyicinin hiçbir uygulama bildirimini yürütülebilir dosyaya katıştırmamasını sağlar.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Derleyicinin çıkış dosyası için hedeflediği işlemci platformunu belirtir.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Kaynak dosyaları derlemek için alt dizinleri arar.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Tüm tür bildirimleri için bir ad alanı belirtir.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Mscorlib. dll ve Microsoft. VisualBasic. dll dosyasının konumunu belirtir.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan veya belirli bir çalışma zamanı kitaplığı başvurusuyla derlenmesi gerektiğini belirtir.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Bir projenin taşınabilir yürütülebilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası tanımlar.|  
|`-parallel[+&#124;-]`|Eşzamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|  
|`-checksumalgorithm:<alg>`|PDB 'de depolanan kaynak dosyası sağlama toplamını hesaplamak için algoritmayı belirtin.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256. <br>Microsoft, SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneriyor.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Alfabetik olarak listelenen Visual Basic derleyici seçenekleri](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)

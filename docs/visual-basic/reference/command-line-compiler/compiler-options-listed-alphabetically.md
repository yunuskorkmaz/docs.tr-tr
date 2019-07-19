---
title: Alfabetik Olarak Listelenmiş Visual Basic Derleyici Seçenekleri
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: 3fd07c9f2cdea3987602502cf242893b44aaddba
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331567"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Alfabetik olarak listelenen Visual Basic derleyici seçenekleri
Visual Basic komut satırı derleyicisi, Visual Studio tümleşik geliştirme ortamından (IDE) program derlemek için alternatif olarak sağlanır. Aşağıda alfabetik olarak sıralanan Visual Basic komut satırı derleyici seçeneklerinin bir listesi verilmiştir.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Seçenek|Amaç|  
|------------|-------------|  
|[@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Bir yanıt dosyası belirtir.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçeneklerini görüntüler. Bu komut, `-help` seçeneğini belirtirken de aynıdır. Hiçbir derleme gerçekleşmez.|  
|`-additionalfile`|Kod oluşturmayı doğrudan etkilemeyen, ancak hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilen ek dosyaları adlandırır.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.|  
|`-analyzer`|Bu derlemeden çözümleyiciler çalıştırın (kısa biçim:-a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|DLL 'nin temel adresini belirtir.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Bir hatayı rapor etmelerini kolaylaştıran bilgiler içeren bir dosya oluşturur.|  
|`-checksumalgorithm:<alg>`|PDB 'de depolanan kaynak dosyası sağlama toplamını hesaplamak için algoritmayı belirtin.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256. <br>Microsoft, SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneriyor.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Hata ayıklama bilgileri üretir.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Koşullu derleme için sembolleri tanımlar.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Derlemenin tamamen veya kısmen imzalanacağını belirtir.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Girişlerin özdeş olması halinde, derleyicinin ikili içerik özdeş olan bir derlemeyi çıkış yapmasına neden olur.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Belge açıklamalarını bir XML dosyasına işler.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Visual Basic derleyicisinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Çıktı dosyasının bölümlerinin hangi noktada hizalanacağını belirtir.|  
|[-yardım](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçeneklerini görüntüler. Bu komut, `-?` seçeneğini belirtirken de aynıdır. Hiçbir derleme gerçekleşmez.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Belirli bir yürütülebilir dosyanın yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini gösterir.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Belirtilen derlemeden bir ad alanı içeri aktarır.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Bir derlemeye tanımlayıcı ad vermek için bir anahtar çifti için anahtar kapsayıcısı adı belirtir.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Derlemeye tanımlayıcı ad vermek için bir anahtar veya anahtar çifti içeren bir dosya belirtir.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Dil sürümünü belirtin: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|[-Reference](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneğinin başvurduğu derlemelerin konumunu belirtir.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Yönetilen bir kaynağa bir bağlantı oluşturur.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Başlangıçta kullanılacak `Sub Main` yordamı içeren sınıfı belirtir.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Modülün bir parçası olacağı derlemenin adını belirtir.|  
|`-modulename:<string>`|Kaynak modülünün adını belirtin|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|.NET Compact Framework hedeflemek için derleyiciyi ayarlar.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Vbc. rsp ile derleme kullanmayın.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Derleyici başlık bilgilerini gizler.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Derleyicinin standart kitaplıklara Başvurmamasını sağlar.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Derleyicinin uyarı oluşturma yeteneğini engeller.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Derleyicinin hiçbir uygulama bildirimini yürütülebilir dosyaya katıştırmamasını sağlar.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Kod iyileştirmeyi etkinleştirilir/devre dışı bırakır.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Dize karşılaştırmalarının ikili mı yoksa yerel ayara özgü metin semantiğini mi kullanılacağını belirtir.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Değişkenlerin açık bildirimini uygular.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Katı dil semantiğini zorlar.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Bir çıkış dosyasını belirtir.|  
|`-parallel[+&#124;-]`|Eşzamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Derleyicinin çıkış dosyası için hedeflediği işlemci platformunu belirtir.|  
|`-preferreduilang`|Tercih edilen çıkış dili adını belirtin.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Derleyicinin sözdizimiyle ilgili hatalar ve uyarılar için kod görüntülemesini engeller.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Kaynak dosyaları derlemek için alt dizinleri arar.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Meta verileri bir derlemeden içeri aktarır.|  
|[-refonly](refonly-compiler-option.md)|Yalnızca bir başvuru derlemesini verir.|
|[-refout](refout-compiler-option.md)|Bir başvuru derlemesinin çıkış yolunu belirtir.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Tamsayı taşma denetimini devre dışı bırakır.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Bir derlemede yönetilen bir kaynak gömer.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Tüm tür bildirimleri için bir ad alanı belirtir.|  
|`-ruleset:<file>`|Belirli tanılamayı devre dışı bırakan bir RuleSet dosyası belirtin.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Mscorlib. dll ve Microsoft. VisualBasic. dll dosyasının konumunu belirtir.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Çıkış dosyasının biçimini belirtir.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan veya belirli bir çalışma zamanı kitaplığı başvurusuyla derlenmesi gerektiğini belirtir.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Derleme sırasında ek bilgi verir.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Hatalara yönelik uyarıları yükseltir.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Çıkış dosyasına bir. ico dosyası ekler.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Bir projenin taşınabilir yürütülebilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası tanımlar.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Çıktı dosyasına bir Win32 kaynağı ekler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kategoriye göre listelenmiş Visual Basic derleyici seçenekleri](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)
- [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)

---
title: Alfabetik Listelenmiş Derleyici Seçenekleri
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: d0dbe785edf7a9aa029d4be08a9b854cf1fb2b79
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085301"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Alfabetik olarak listelenen Visual Basic derleyici seçenekleri

Visual Basic komut satırı derleyicisi, Visual Studio tümleşik geliştirme ortamından (IDE) program derlemek için alternatif olarak sağlanır. Aşağıda alfabetik olarak sıralanan Visual Basic komut satırı derleyici seçeneklerinin bir listesi verilmiştir.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Seçenek|Amaç|  
|------------|-------------|  
|[@ (Yanıt Dosyasını Belirtin)](specify-response-file.md)|Bir yanıt dosyası belirtir.|  
|[-?](help.md)|Derleyici seçeneklerini görüntüler. Bu komut, seçeneğini belirtirken de aynıdır `-help` . Hiçbir derleme gerçekleşmez.|  
|`-additionalfile`|Kod oluşturmayı doğrudan etkilemeyen, ancak hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilen ek dosyaları adlandırır.|  
|[-addmodule](addmodule.md)|Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.|  
|`-analyzer`|Bu derlemeden çözümleyiciler çalıştırın (kısa biçim:-a)|  
|[-baseaddress](baseaddress.md)|DLL 'nin temel adresini belirtir.|  
|[-bugreport](bugreport.md)|Bir hatayı rapor etmelerini kolaylaştıran bilgiler içeren bir dosya oluşturur.|  
|`-checksumalgorithm:<alg>`|PDB 'de depolanan kaynak dosyası sağlama toplamını hesaplamak için algoritmayı belirtin.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256. <br>Microsoft, SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneriyor.|  
|[-codepage](codepage.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.|  
|[-Hata Ayıkla](debug.md)|Hata ayıklama bilgileri üretir.|  
|[-tanımla](define.md)|Koşullu derleme için sembolleri tanımlar.|  
|[-delaysign](delaysign.md)|Derlemenin tamamen veya kısmen imzalanacağını belirtir.|  
|[-deterministic](deterministic.md)|Girişlerin özdeş olması halinde, derleyicinin ikili içerik özdeş olan bir derlemeyi çıkış yapmasına neden olur.|
|[-doc](doc.md)|Belge açıklamalarını bir XML dosyasına işler.|  
|[-errorreport](errorreport.md)|Visual Basic derleyicisinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir.|  
|[-filealign](filealign.md)|Çıktı dosyasının bölümlerinin hangi noktada hizalanacağını belirtir.|  
|[-yardım](help.md)|Derleyici seçeneklerini görüntüler. Bu komut, seçeneğini belirtirken de aynıdır `-?` . Hiçbir derleme gerçekleşmez.|  
|[-highentropyva](highentropyva.md)|Belirli bir yürütülebilir dosyanın yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini gösterir.|  
|[-imports](imports.md)|Belirtilen derlemeden bir ad alanı içeri aktarır.|  
|[-keycontainer](keycontainer.md)|Bir derlemeye tanımlayıcı ad vermek için bir anahtar çifti için anahtar kapsayıcısı adı belirtir.|  
|[-keyfile](keyfile.md)|Derlemeye tanımlayıcı ad vermek için bir anahtar veya anahtar çifti içeren bir dosya belirtir.|  
|[-langversion](langversion.md)|Dil sürümünü belirtin: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-libpath](libpath.md)|[-Reference](reference.md) seçeneğinin başvurduğu derlemelerin konumunu belirtir.|  
|[-linkresource](linkresource.md)|Yönetilen bir kaynağa bir bağlantı oluşturur.|  
|[-main](main.md)|Başlangıçta kullanılacak yordamı içeren sınıfı belirtir `Sub Main` .|  
|[-moduleassemblyname](moduleassemblyname.md)|Modülün bir parçası olacağı derlemenin adını belirtir.|  
|`-modulename:<string>`|Kaynak modülünün adını belirtin|  
|[-netcf](netcf.md)|.NET Compact Framework hedeflemek için derleyiciyi ayarlar.|  
|[-noconfig](noconfig.md)|Vbc. rsp ile derleme kullanmayın.|  
|[-nologo](nologo.md)|Derleyici başlık bilgilerini gizler.|  
|[-nostdlib](nostdlib.md)|Derleyicinin standart kitaplıklara Başvurmamasını sağlar.|  
|[-nowarn](nowarn.md)|Derleyicinin uyarı oluşturma yeteneğini engeller.|  
|[-nowin32manifest](nowin32manifest.md)|Derleyicinin hiçbir uygulama bildirimini yürütülebilir dosyaya katıştırmamasını sağlar.|  
|[-optimize et](optimize.md)|Kod iyileştirmeyi etkinleştirilir/devre dışı bırakır.|  
|[-optioncompare](optioncompare.md)|Dize karşılaştırmalarının ikili mı yoksa yerel ayara özgü metin semantiğini mi kullanılacağını belirtir.|  
|[-optionexplicit](optionexplicit.md)|Değişkenlerin açık bildirimini uygular.|  
|[-optioninfer](optioninfer.md)|Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.|  
|[-optionstrict](optionstrict.md)|Katı dil semantiğini zorlar.|  
|[-out](out.md)|Bir çıkış dosyasını belirtir.|  
|<code>-parallel[+&#124;-]</code>|Eşzamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|  
|[-Platform](platform.md)|Derleyicinin çıkış dosyası için hedeflediği işlemci platformunu belirtir.|  
|`-preferreduilang`|Tercih edilen çıkış dili adını belirtin.|  
|[-quiet](quiet.md)|Derleyicinin sözdizimiyle ilgili hatalar ve uyarılar için kod görüntülemesini engeller.|  
|[-recurse](recurse.md)|Kaynak dosyaları derlemek için alt dizinleri arar.|  
|[-başvuru](reference.md)|Meta verileri bir derlemeden içeri aktarır.|  
|[-refonly](refonly-compiler-option.md)|Yalnızca bir başvuru derlemesini verir.|
|[-refout](refout-compiler-option.md)|Bir başvuru derlemesinin çıkış yolunu belirtir.|
|[-removeintchecks](removeintchecks.md)|Tamsayı taşma denetimini devre dışı bırakır.|  
|[-Kaynak](resource.md)|Bir derlemede yönetilen bir kaynak gömer.|  
|[-rootnamespace](rootnamespace.md)|Tüm tür bildirimleri için bir ad alanı belirtir.|  
|`-ruleset:<file>`|Belirli tanılamayı devre dışı bırakan bir RuleSet dosyası belirtin.|  
|[-sdkpath](sdkpath.md)|Mscorlib.dll ve Microsoft.VisualBasic.dll konumunu belirtir.|  
|[-subsystemversion](subsystemversion.md)|Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir.|  
|[-target](target.md)|Çıkış dosyasının biçimini belirtir.|  
|[-utf8output](utf8output.md)|UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.|  
|[-vbruntime](vbruntime.md)|Derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan veya belirli bir çalışma zamanı kitaplığı başvurusuyla derlenmesi gerektiğini belirtir.|  
|[-verbose](verbose.md)|Derleme sırasında ek bilgi verir.|  
|[-warnaserror](warnaserror.md)|Hatalara yönelik uyarıları yükseltir.|  
|[-win32icon](win32icon.md)|Çıkış dosyasına bir. ico dosyası ekler.|  
|[-win32manifest](win32manifest.md)|Bir projenin taşınabilir yürütülebilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası tanımlar.|  
|[-win32resource](win32resource.md)|Çıktı dosyasına bir Win32 kaynağı ekler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kategoriye Göre Listelenmiş Visual Basic Derleyici Seçenekleri](compiler-options-listed-by-category.md)
- [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)

---
description: 'Hakkında daha fazla bilgi edinin: kategoriye göre listelenen Visual Basic derleyici seçenekleri'
title: Kategorilere Göre Listelenen Derleyici Seçenekleri
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: f0535e2aa94cda96610acb0edb24f6d46cc4afa0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474180"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Kategoriye göre listelenmiş Visual Basic derleyici seçenekleri

Visual Basic komut satırı derleyicisi, Visual Studio tümleşik geliştirme ortamı (IDE) içinden program derlemek için alternatif olarak sağlanır. Aşağıda, işlevsel kategoriye göre sıralanan Visual Basic komut satırı derleyici seçeneklerinin bir listesi verilmiştir.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Derleyici çıkışı  
  
|Seçenek|Amaç|  
|---|---|  
|[-nologo](nologo.md)|Derleyici başlık bilgilerini gizler.|  
|[-utf8output](utf8output.md)|UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.|  
|[-verbose](verbose.md)|Derleme sırasında ek bilgi verir.|  
|`-modulename:<string>`|Kaynak modülünün adını belirtin|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Derleyici çıkışı için bir dil belirtin.|
  
## <a name="optimization"></a>İyileştirme  
  
|Seçenek|Amaç|  
|---|---|  
|[-filealign](filealign.md)|Çıktı dosyasının bölümlerinin hangi noktada hizalanacağını belirtir.|  
|[-optimize et](optimize.md)|İyileştirmeleri etkinleştirilir/devre dışı bırakır.|  
  
## <a name="output-files"></a>Çıkış dosyaları  
  
|Seçenek|Amaç|  
|---|---|  
|[-doc](doc.md)|Belge açıklamalarını bir XML dosyası ile işleyin.|  
|[-belirleyici](deterministic.md)|Girişlerin özdeş olması halinde, derleyicinin ikili içerik özdeş olan bir derlemeyi çıkış yapmasına neden olur.|
|[-netcf](netcf.md)|.NET Compact Framework hedeflemek için derleyiciyi ayarlar.|  
|[-Out](out.md)|Bir çıkış dosyasını belirtir.|  
|[-refonly](refonly-compiler-option.md)|Yalnızca bir başvuru derlemesini verir.|
|[-refout](refout-compiler-option.md)|Bir başvuru derlemesinin çıkış yolunu belirtir.|
|[-hedef](target.md)|Çıkışın biçimini belirtir.|  
  
## <a name="net-assemblies"></a>.NET derlemeleri  
  
|Seçenek|Amaç|  
|---|---|  
|[-addmodule](addmodule.md)|Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.|  
|[-delaysign](delaysign.md)|Derlemenin tamamen veya kısmen imzalanacağını belirtir.|  
|[-imports](imports.md)|Belirtilen derlemeden bir ad alanı içeri aktarır.|  
|[-keycontainer](keycontainer.md)|Bir derlemeye tanımlayıcı ad vermek için bir anahtar çifti için anahtar kapsayıcısı adı belirtir.|  
|[-keyfile](keyfile.md)|Derlemeye tanımlayıcı ad vermek için bir anahtar veya anahtar çifti içeren bir dosya belirtir.|  
|[-libpath](libpath.md)|[-Reference](reference.md) seçeneğinin başvurduğu derlemelerin konumunu belirtir.|  
|[-başvuru](reference.md)|Meta verileri bir derlemeden içeri aktarır.|  
|[-moduleassemblyname](moduleassemblyname.md)|Modülün bir parçası olacağı derlemenin adını belirtir.|  
|`-analyzer`|Bu derlemeden çözümleyiciler çalıştırın (kısa biçim:-a)|  
|`-additionalfile`|Kod oluşturmayı doğrudan etkilemeyen, ancak hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilen ek dosyaları adlandırır.|  
  
## <a name="debuggingerror-checking"></a>Hata ayıklama/hata denetimi  
  
|Seçenek|Amaç|  
|---|---|  
|[-bugreport](bugreport.md)|Bir hatayı rapor etmelerini kolaylaştıran bilgiler içeren bir dosya oluşturur.|  
|[-Hata Ayıkla](debug.md)|Hata ayıklama bilgileri üretir.|  
|[-nowarn](nowarn.md)|Derleyicinin uyarı oluşturma yeteneğini engeller.|  
|[-quiet](quiet.md)|Derleyicinin sözdizimiyle ilgili hatalar ve uyarılar için kod görüntülemesini engeller.|  
|[-removeintchecks](removeintchecks.md)|Tamsayı taşma denetimini devre dışı bırakır.|  
|[-warnaserror](warnaserror.md)|Hatalara yönelik uyarıları yükseltir.|  
|`-ruleset:<file>`|Belirli tanılamayı devre dışı bırakan bir RuleSet dosyası belirtin.|  
  
## <a name="help"></a>Yardım  
  
|Seçenek|Amaç|  
|---|---|  
|[-?](help.md)|Derleyici seçeneklerini görüntüler. Bu komut, seçeneğini belirtirken de aynıdır `-help` . Hiçbir derleme gerçekleşmez.|  
|[-yardım](help.md)|Derleyici seçeneklerini görüntüler. Bu komut, seçeneğini belirtirken de aynıdır `-?` . Hiçbir derleme gerçekleşmez.|  
  
## <a name="language"></a>Dil  
  
|Seçenek|Amaç|  
|---|---|  
|[-langversion](langversion.md)|Dil sürümünü belirtin: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-optionexplicit](optionexplicit.md)|Değişkenlerin açık bildirimini uygular.|  
|[-optionstrict](optionstrict.md)|Katı tür semantiğini zorlar.|  
|[-optioncompare](optioncompare.md)|Dize karşılaştırmalarının ikili mı yoksa yerel ayara özgü metin semantiğini mi kullanılacağını belirtir.|  
|[-optioninfer](optioninfer.md)|Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.|  
  
## <a name="preprocessor"></a>Ön işlemci  
  
|Seçenek|Amaç|  
|---|---|  
|[-define](define.md)|Koşullu derleme için sembolleri tanımlar.|  
  
## <a name="resources"></a>Kaynaklar  
  
|Seçenek|Amaç|  
|---|---|  
|[-linkresource](linkresource.md)|Yönetilen bir kaynağa bir bağlantı oluşturur.|  
|[-Kaynak](resource.md)|Bir derlemede yönetilen bir kaynak gömer.|  
|[-win32icon](win32icon.md)|Çıkış dosyasına bir. ico dosyası ekler.|  
|[-win32resource](win32resource.md)|Çıktı dosyasına bir Win32 kaynağı ekler.|  
  
## <a name="miscellaneous"></a>Çeşitli  
  
|Seçenek|Amaç|  
|---|---|  
|[@ (Yanıt Dosyasını Belirtin)](specify-response-file.md)|Bir yanıt dosyası belirtir.|  
|[-baseaddress](baseaddress.md)|DLL 'nin temel adresini belirtir.|  
|[-codepage](codepage.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.|  
|[-errorreport](errorreport.md)|Visual Basic derleyicisinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir.|  
|[-highentropyva](highentropyva.md)|Windows çekirdeğine, belirli bir yürütülebilir dosyanın yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini söyler.|  
|[-Main](main.md)|Başlangıçta kullanılacak yordamı içeren sınıfı belirtir `Sub Main` .|  
|[-noconfig](noconfig.md)|Vbc. rsp ile derleme|  
|[-nostdlib](nostdlib.md)|Derleyicinin standart kitaplıklara Başvurmamasını sağlar.|  
|[-nowin32manifest](nowin32manifest.md)|Derleyicinin hiçbir uygulama bildirimini yürütülebilir dosyaya katıştırmamasını sağlar.|  
|[-Platform](platform.md)|Derleyicinin çıkış dosyası için hedeflediği işlemci platformunu belirtir.|  
|[-recurse](recurse.md)|Kaynak dosyaları derlemek için alt dizinleri arar.|  
|[-rootnamespace](rootnamespace.md)|Tüm tür bildirimleri için bir ad alanı belirtir.|  
|[-sdkpath](sdkpath.md)|Mscorlib.dll ve Microsoft.VisualBasic.dll konumunu belirtir.|  
|[-vbruntime](vbruntime.md)|Derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan veya belirli bir çalışma zamanı kitaplığı başvurusuyla derlenmesi gerektiğini belirtir.|  
|[-win32manifest](win32manifest.md)|Bir projenin taşınabilir yürütülebilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası tanımlar.|  
|`-parallel[+&#124;-]`|Eşzamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|  
|`-checksumalgorithm:<alg>`|PDB 'de depolanan kaynak dosyası sağlama toplamını hesaplamak için algoritmayı belirtin.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256. <br>Microsoft, SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneriyor.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Alfabetik Olarak Listelenmiş Visual Basic Derleyici Seçenekleri](compiler-options-listed-alphabetically.md)
- [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)

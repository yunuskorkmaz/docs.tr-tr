---
title: Kategoriye Göre Listelenmiş Visual Basic Derleyici Seçenekleri
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 333bfb539fc375fd8f2dd170a187002fcf81ea2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827373"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Kategoriye göre listelenmiş Visual Basic derleyici seçenekleri
Visual Basic komut satırı derleyicisi, Visual Studio tümleşik geliştirme ortamında (IDE) programları derleme alternatif olarak sağlanır. İşlevsel kategoriye göre sıralanmış Visual Basic komut satırı derleyicisini seçeneklerin bir listesi verilmiştir.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Derleyici çıkışı  
  
|Seçenek|Amaç|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Derleyici başlık bilgilerini engellemesidir.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|UTF-8 kodlaması kullanarak derleyici çıkışı görüntüler.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Derleme sırasında ek bilgiler çıkarır.|  
|`-modulename:<string>`|Kaynak modülünün adını belirtin|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Derleyici çıkışı için bir dil belirtin.|
  
## <a name="optimization"></a>İyileştirme  
  
|Seçenek|Amaç|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Çıktı dosyasının bölümlerinin hizalanacağı yeri belirtir.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|İyileştirmeleri etkinleştirir/devre dışı bırakır.|  
  
## <a name="output-files"></a>Çıktı dosyaları  
  
|Seçenek|Amaç|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|İşlem belge yorumlarını bir XML dosyası.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|İkili içeriği girişleri özdeş ise derlemeler arasında aynıdır derleme çıktısını almak derleyicinin neden olur.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Derleyicinin hedef ayarlar [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Çıkış dosyasını belirtir.|  
|[-refonly](refonly-compiler-option.md)|Yalnızca bir başvuru bütünleştirilmiş kodu çıkarır.|
|[-refout](refout-compiler-option.md)|Başvuru bütünleştirilmiş kodu çıkış yolunu belirtir.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Çıkış biçimi belirtir.|  
  
## <a name="net-assemblies"></a>.NET derlemeleri  
  
|Seçenek|Amaç|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Derleyicinin tüm kullanılabilir belirtilen dosyalar, şu anda derlemekte olduğunuz projeye kullandırmasına bilgileri yazın.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Derlemenin tamamen veya kısmen imzalanacağını belirtir.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Bir ad alanı, belirtilen bir derlemesinden içeri aktarır.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Bir derlemeyi tanımlayıcı bir ad vermek bir anahtar çifti için bir anahtar kapsayıcısı adını belirtir.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Bir anahtar veya bir derlemeyi bir katı ad vermek için anahtar çifti içeren bir dosyayı belirtir.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Tarafından başvurulan derlemelerin konumunu belirten [-başvuru](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneği.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Bir derlemeye ait meta verileri alır.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Bir modülün bir parçası olacağı derlemenin adını belirtir.|  
|`-analyzer`|Bu derleme Çözümleyicileri çalıştırın (kısa form: - a)|  
|`-additionalfile`|Doğrudan kod üretimini etkilemez, ancak bir hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilir ek dosya adları.|  
  
## <a name="debuggingerror-checking"></a>Hata ayıklama/hata denetimi  
  
|Seçenek|Amaç|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Bir hatayı raporlamak kolaylaştıran bilgilerini içeren bir dosya oluşturur.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Hata ayıklama bilgisi üretir.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Derleyicinin, uyarı oluşturma yeteneğini engeller.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Derleyici, kod söz dizimi ile ilgili hatalar ve Uyarılar için görüntülenmesini engeller.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Tamsayı taşma denetimini devre dışı bırakır.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Hatalar için uyarıları yükseltir.|  
|`-ruleset:<file>`|Belirli tanılama devre dışı bırakan bir kural kümesi dosyası belirtin.|  
  
## <a name="help"></a>Help  
  
|Seçenek|Amaç|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçenekleri görüntüler. Bu komut belirtilmesiyle aynıdır `-help` seçeneği. Hiçbir derleme gerçekleşir.|  
|[-Yardım](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçenekleri görüntüler. Bu komut belirtilmesiyle aynıdır `-?` seçeneği. Hiçbir derleme gerçekleşir.|  
  
## <a name="language"></a>Dil  
  
|Seçenek|Amaç|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Dil sürümünü belirtin: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Değişkenleri açık bildirimini zorlar.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Katı tür semantiklerini zorlar.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Dize karşılaştırmaları veya ikili yerel ayara özgü metin semantiklerini kullanan belirtir.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Değişken bildiriminde yerel tür çıkarımı kullanımını etkinleştirir.|  
  
## <a name="preprocessor"></a>Ön işlemci  
  
|Seçenek|Amaç|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Koşullu derleme sembollerini tanımlar.|  
  
## <a name="resources"></a>Kaynaklar  
  
|Seçenek|Amaç|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Yönetilen kaynağa bağlantı oluşturur.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Yönetilen kaynak bir derlemeye gömer.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Çıktı dosyasına bir .ico simge dosyası ekler.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Bir Win32 kaynağı çıktı dosyasına ekler.|  
  
## <a name="miscellaneous"></a>Çeşitli  
  
|Seçenek|Amaç|  
|---|---|  
|[@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Bir yanıt dosyası belirtir.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Bir DLL temel adresini belirtir.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Visual Basic derleyici iç derleyici hatalarını nasıl raporlayacağını belirtir.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Windows çekirdek, belirli bir yürütülebilir dosya yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini belirtir.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|İçeren sınıf belirtir `Sub Main` başlatma sırasında kullanılacak yordamı.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nezahrnovat ile derlenmiyor|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Standart kitaplıkları başvuruda bulunmamaya derleyici neden olur.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Herhangi bir uygulama bildirimi yürütülebilir dosyasına katıştırma değil derleyicinin sağlar.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|İşlemci platformu çıkış dosyası derleyici hedeflerini belirtir.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Derlenecek kaynak dosyaların için alt arar.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Tüm tür bildirimleri için bir ad alanını belirtir.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin konumunu belirtir.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Derleyici, Visual Basic çalışma zamanı kitaplığı veya bir belirli çalışma zamanı kitaplık başvurusu olan bir başvuru olmadan derlemesi gerektiğini belirtir.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Bir projenin taşınabilir yürütülebilir (PE) dosya gömülü olması için kullanıcı tanımlı Win32 uygulama bildirim dosyası tanımlar.|  
|`-parallel[+&#124;-]`|Eş zamanlı derleme (+) kullanılıp kullanılmayacağını belirtir.|  
|`-checksumalgorithm:<alg>`|PDB içinde depolanan kaynak dosya sağlama toplamı hesaplama algoritması belirtin.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Alfabetik listelenmiş Visual Basic derleyici seçenekleri](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)

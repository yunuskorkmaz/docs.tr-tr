---
title: Kategoriye Göre Listelenmiş Visual Basic Derleyici Seçenekleri
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13aeab52cfd43aa8dfd7fda69e2eb9be798473e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Kategoriye göre listelenmiş Visual Basic derleyici seçenekleri
Visual Basic komut satırı derleyicisi programlardan Visual Studio tümleşik geliştirme ortamı (IDE) içinde derleme alternatif olarak sağlanır. İşlev kategoriye göre sıralanmış Visual Basic komut satırı derleyicisi seçeneklerinin listesi verilmiştir.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Derleyici çıktısı  
  
|Seçenek|Amaç|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Derleyici başlık bilgilerini gizler.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|UTF-8 kodlaması kullanarak derleyici çıkışı görüntülenir.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Derleme sırasında ek bilgiler çıkarır.|  
|`-modulename:<string>`|Kaynak modülünün adını belirtin|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Derleyici çıktısı için bir dil belirtin.|
  
## <a name="optimization"></a>En iyi duruma getirme  
  
|Seçenek|Amaç|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Çıkış dosyasının bölümlerinin hizalamak konumu belirtir.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|En iyi duruma getirme etkinleştirir/devre dışı bırakır.|  
  
## <a name="output-files"></a>Çıkış dosyaları  
  
|Seçenek|Amaç|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Bir XML dosyasına işlem belgeleri açıklamaları.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Derleyicinin girişleri özdeş ise ikili içerikleri derlemeleri arasında aynı olan bir derleme çıktı neden olur.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Hedefe derleyici ayarlar [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Bir çıkış dosyasını belirtir.|  
|[-refonly](refonly-compiler-option.md)|Yalnızca bir referans derlemesini çıkarır.|
|[-refout](refout-compiler-option.md)|Bir başvuru derleme çıktı yolunu belirtir.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Çıkış biçimini belirtir.|  
  
## <a name="net-assemblies"></a>.NET derleme  
  
|Seçenek|Amaç|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Tüm hale getirmesine neden olur. şu anda derlediğiniz proje için belirtilen dosya veya dosyalar kullanılabilir bilgileri yazın.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Derlemenin tamamen veya kısmen imzalanacağını belirtir.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Bir ad alanı belirtilen derlemesinden alır.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Bir derleme tanımlayıcı bir ad vermek bir anahtar çifti için bir anahtar kapsayıcı adı belirtir.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Bir anahtar ya da bir derleme tanımlayıcı bir ad vermek için anahtar çiftini içeren dosyayı belirtir.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Tarafından başvurulan derlemelerin konumunu belirtir [-başvuru](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneği.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Bir derlemeye ait meta verileri alır.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Bir modül bir parçası olacak bütünleştirilmiş kodun adını belirtir.|  
|`-analyzer`|Bu derlemedeki çözümleyiciler çalıştırın (kısa form: - a)|  
|`-additionalfile`|Kod oluşturma doğrudan etkilemez ancak çözümleyicileri tarafından hatalar veya uyarılar üretmek için kullanılabilir başka dosya adları.|  
  
## <a name="debuggingerror-checking"></a>Hata ayıklama hata denetimi  
  
|Seçenek|Amaç|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Bir hata raporu kolaylaştırır bilgilerini içeren bir dosya oluşturur.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Hata ayıklama bilgisi oluşturur.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Derleyicinin uyarıları oluşturma yeteneği gizler.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Derleyici sözdizimi ile ilgili hatalar ve Uyarılar için kod görüntülenmesini engeller.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Tamsayı taşma denetimi devre dışı bırakır.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Hatalar için uyarıları yükseltir.|  
|`-ruleset:<file>`|Belirli Tanılama'yı devre dışı bırakan bir ruleset belirtin.|  
  
## <a name="help"></a>Yardım  
  
|Seçenek|Amaç|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçeneklerini görüntüler. Bu komut belirtme aynıdır `-help` seçeneği. Hiçbir derleme oluşur.|  
|[-Yardım](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçeneklerini görüntüler. Bu komut belirtme aynıdır `-?` seçeneği. Hiçbir derleme oluşur.|  
  
## <a name="language"></a>Dil  
  
|Seçenek|Amaç|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Dil sürümünü belirtin: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Değişkenlerin açıkça bildirilmesini zorunlu tutar.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Kesin türü anlamları zorlar.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Dize karşılaştırmaları veya ikili yerel ayarlara özgü metin semantiğini kullanmasına belirtir.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Yerel türü çıkarımı değişken bildirimlerden kullanımını etkinleştirir.|  
  
## <a name="preprocessor"></a>Ön işlemci  
  
|Seçenek|Amaç|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Koşullu derleme simgelerini tanımlar.|  
  
## <a name="resources"></a>Kaynaklar  
  
|Seçenek|Amaç|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Yönetilen kaynak bağlantısını oluşturur.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Yönetilen bir kaynağın bir derlemede katıştırır.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Bir .ico dosyasını çıktı dosyasına ekler.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Win32 kaynak çıktı dosyasına ekler.|  
  
## <a name="miscellaneous"></a>Çeşitli  
  
|Seçenek|Amaç|  
|---|---|  
|[@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Bir yanıt dosyası belirtir.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Bir DLL'nin temel adresini belirtir.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanmak üzere kod sayfasını belirtir.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Visual Basic derleyici iç derleyici hataları nasıl bildirmelisiniz belirtir.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Windows çekirdek, belirli bir yürütülebilir dosya yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini belirtir.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|İçeren sınıf belirtir `Sub Main` yordamı başlangıçta kullanın.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Vbc.rsp ile derleme değil|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Standart kitaplıkları değil, başvuru için derleyici neden olur.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Herhangi bir uygulama bildirimi yürütülebilir dosyasına katıştırma değil derleyiciye.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|İşlemci platform derleyici hedeflerin çıktı dosyasına belirtir.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Alt dizinleri derlemek kaynak dosyaları için arar.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Tüm tür bildirimleri için bir ad alanını belirtir.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Mscorlib.dll ve Microsoft.VisualBasic.dll içinde konumunu belirtir.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Visual Basic çalışma zamanı kitaplığı için veya belirli çalışma zamanı kitaplığı başvurusu olan bir başvuru olmadan derleyici derleme belirtir.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Bir projenin taşınabilir yürütülebilir (PE) dosyasına katıştırılmış bir kullanıcı tarafından tanımlanan Win32 uygulama bildirim dosyasının tanımlar.|  
|`-parallel[+&#124;-]`|Eş zamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|  
|`-checksumalgorithm:<alg>`|PDB içinde depolanan kaynak dosya sağlama toplamı hesaplama algoritması belirtin.  Desteklenen değerler: SHA1 (varsayılan) veya SHA256.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Alfabetik listelenmiş Visual Basic derleyici seçenekleri](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)  
 [Proje Tasarımcısı giriş](https://msdn.microsoft.com/en-us/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))  
 [Alfabetik Listelenmiş C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-by-category.md)

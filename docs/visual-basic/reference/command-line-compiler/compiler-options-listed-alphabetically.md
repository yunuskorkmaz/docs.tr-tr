---
title: Alfabetik Olarak Listelenmiş Visual Basic Derleyici Seçenekleri
ms.date: 04/12/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6e95c52c708128267ab6dc79a1b37d21b30bac2
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Alfabetik listelenmiş Visual Basic derleyici seçenekleri
Visual Basic komut satırı derleyicisi Visual Studio tümleşik geliştirme ortamı (IDE) programları derleme alternatif olarak sağlanır. Visual Basic komut satırı derleyicisi seçenekleri alfabetik listesi verilmiştir.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Seçenek|Amaç|  
|------------|-------------|  
|[@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Bir yanıt dosyası belirtir.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçeneklerini görüntüler. Bu komut belirtme aynıdır `-help` seçeneği. Hiçbir derleme oluşur.|  
|`-additionalfile`|Kod oluşturma doğrudan etkilemez ancak çözümleyicileri tarafından hatalar veya uyarılar üretmek için kullanılabilir başka dosya adları.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Tüm hale getirmesine neden olur. şu anda derlediğiniz proje için belirtilen dosya veya dosyalar kullanılabilir bilgileri yazın.|  
|`-analyzer`|Bu derlemedeki çözümleyiciler çalıştırın (kısa form: - a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Bir DLL'nin temel adresini belirtir.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Bir hata raporu kolaylaştırır bilgilerini içeren bir dosya oluşturur.|  
|`-checksumalgorithm:<alg>`|PDB içinde depolanan kaynak dosya sağlama toplamı hesaplama algoritması belirtin.  Desteklenen değerler: SHA1 (varsayılan) veya SHA256.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanmak üzere kod sayfasını belirtir.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Hata ayıklama bilgisi oluşturur.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Koşullu derleme simgelerini tanımlar.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Derlemenin tamamen veya kısmen imzalanacağını belirtir.|  
|[-belirleyici](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Derleyicinin girişleri özdeş ise ikili içerikleri derlemeleri arasında aynı olan bir derleme çıktı neden olur.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Belge açıklamaları bir XML dosyasına işler.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Visual Basic derleyici iç derleyici hataları nasıl bildirmelisiniz belirtir.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Çıkış dosyasının bölümlerinin hizalamak konumu belirtir.|  
|[-Yardım](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçeneklerini görüntüler. Bu komut belirtme aynıdır `-?` seçeneği. Hiçbir derleme oluşur.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Belirli bir yürütülebilir dosya yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini belirtir.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Bir ad alanı belirtilen derlemesinden alır.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Bir derleme tanımlayıcı bir ad vermek bir anahtar çifti için bir anahtar kapsayıcı adı belirtir.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Bir anahtar ya da bir derleme tanımlayıcı bir ad vermek için anahtar çiftini içeren dosyayı belirtir.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Dil sürümünü belirtin: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Tarafından başvurulan derlemelerin konumunu belirtir [-başvuru](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneği.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Yönetilen kaynak bağlantısını oluşturur.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|İçeren sınıf belirtir `Sub Main` yordamı başlangıçta kullanın.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Bir modül bir parçası olacak bütünleştirilmiş kodun adını belirtir.|  
|`-modulename:<string>`|Kaynak modülünün adını belirtin|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Hedefe derleyici ayarlar [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Vbc.rsp ile derleme değil.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Derleyici başlık bilgilerini gizler.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Standart kitaplıkları değil, başvuru için derleyici neden olur.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Derleyicinin uyarıları oluşturma yeteneği gizler.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Herhangi bir uygulama bildirimi yürütülebilir dosyasına katıştırma değil derleyiciye.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Etkinleştirir/devre dışı bırakır, en iyi duruma getirme kodu.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Dize karşılaştırmaları veya ikili yerel ayarlara özgü metin semantiğini kullanmasına belirtir.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Değişkenlerin açıkça bildirilmesini zorunlu tutar.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Yerel türü çıkarımı değişken bildirimlerden kullanımını etkinleştirir.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Kesin dil semantiğini uygular.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Bir çıkış dosyasını belirtir.|  
|`-parallel[+&#124;-]`|Eş zamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|İşlemci platform derleyici hedeflerin çıktı dosyasına belirtir.|  
|`-preferreduilang`|Tercih edilen çıkış dil adı belirtin.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Derleyici sözdizimi ile ilgili hatalar ve Uyarılar için kod görüntülenmesini engeller.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Alt dizinleri derlemek kaynak dosyaları için arar.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Bir derlemeye ait meta verileri alır.|  
|[-refonly](refonly-compiler-option.md)|Yalnızca bir referans derlemesini çıkarır.|
|[-refout](refout-compiler-option.md)|Bir başvuru derleme çıktı yolunu belirtir.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Tamsayı taşma denetimi devre dışı bırakır.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Yönetilen bir kaynağın bir derlemede katıştırır.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Tüm tür bildirimleri için bir ad alanını belirtir.|  
|`-ruleset:<file>`|Belirli Tanılama'yı devre dışı bırakan bir ruleset belirtin.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Mscorlib.dll ve Microsoft.VisualBasic.dll içinde konumunu belirtir.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|En düşük sürüm oluşturulan yürütülebilir dosyasını kullanabilirsiniz alt sisteminin belirtir.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Çıktı dosyası biçimini belirtir.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|UTF-8 kodlaması kullanarak derleyici çıkışı görüntülenir.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Visual Basic çalışma zamanı kitaplığı için veya belirli çalışma zamanı kitaplığı başvurusu olan bir başvuru olmadan derleyici derleme belirtir.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Derleme sırasında ek bilgiler çıkarır.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Hatalar için uyarıları yükseltir.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Bir .ico dosyasını çıktı dosyasına ekler.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Bir projenin taşınabilir yürütülebilir (PE) dosyasına katıştırılmış bir kullanıcı tarafından tanımlanan Win32 uygulama bildirim dosyasının tanımlar.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Win32 kaynak çıktı dosyasına ekler.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kategoriye göre listelenmiş Visual Basic derleyici seçenekleri](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)  
 [Proje Tasarımcısı giriş](http://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7)  
 [Alfabetik Listelenmiş C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-by-category.md)

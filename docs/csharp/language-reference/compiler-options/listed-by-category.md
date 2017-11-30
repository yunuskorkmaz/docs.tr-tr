---
title: "Kategorilere Göre Listelenen C# Derleyici Seçenekleri"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95c5c3d1c7ea2461e9bda9a1d58464e97ccc688
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="c-compiler-options-listed-by-category"></a>Kategorilere Göre Listelenen C# Derleyici Seçenekleri
Aşağıdaki derleyici seçenekleri kategoriye göre sıralanır. Alfabetik bir listesi için bkz: [C# derleyici seçenekleri listelenen alfabetik olarak](../../../csharp/language-reference/compiler-options/listed-alphabetically.md).  
  
### <a name="optimization"></a>En iyi duruma getirme  
  
|Seçenek|Amaç|  
|------------|-------------|  
|[/ filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|Çıktı dosyasında bölümlerin boyutunu belirtir.|  
|[/ optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|En iyi duruma getirme etkinleştirir/devre dışı bırakır.|  
  
### <a name="output-files"></a>Çıkış dosyaları  
  
|Seçenek|Amaç|  
|------------|-------------|  
|[/ doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|İşlenen belge açıklamaları yazılacak olduğu bir XML dosyası belirtir.|  
|[/ out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|Çıkış dosyasını belirtir.|  
|[/ pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|.Pdb dosyasının konumu ve dosya adını belirtir.|  
|[/ Platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|Çıktı platformunu belirtin.|  
|[/ preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Derleyici çıktısı için bir dil belirtin.|  
|[/refout](refout-compiler-option.md)|Bir referans derlemesini birincil derlemesinin yanı sıra oluşturur.|  
|[/refonly](refonly-compiler-option.md)|Bir referans derlemesini birincil derlemesi yerine oluşturur.|  
|[/ target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|Beş seçenekten birini kullanarak çıktı dosyasının biçimini belirtir: [/target: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md), [/target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md), [/target: library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md),  [ /target: Module ](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), veya [/target: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md).|  
|/MODULENAME:\<dize >|Kaynak modülünün adını belirtin|  
  
### <a name="net-framework-assemblies"></a>.NET framework derlemeleri  
  
|Seçenek|Amaç|  
|------------|-------------|  
|[/ addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|Bu derleme parçası olarak bir veya daha fazla modül belirtir.|  
|[/ delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|Ortak anahtar eklemek için ancak derlemeyi imzasız bırakmayı derleyiciye.|  
|[/ keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|Şifreleme anahtarı kapsayıcısının adını belirtir.|  
|[/ keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|Şifreleme anahtarını içeren dosya adını belirtir.|  
|[/ lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|Tarafından başvurulan derlemelerin konumunu belirtir [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).|  
|[/ nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|Standart Kitaplığı (mscorlib.dll) almamanız için derleyicisi bildirir.|  
|[/ Reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|Meta veriler içeren bir derleme bir dosyadan içeri aktarır.|  
|/Analyzer|Bu derlemedeki çözümleyiciler çalıştırın (kısa form: / a)|  
|/additionalfile|Kod oluşturma doğrudan etkilemez ancak çözümleyicileri tarafından hatalar veya uyarılar üretmek için kullanılabilir başka dosya adları.|  
  
### <a name="debuggingerror-checking"></a>Hata ayıklama hata denetimi  
  
|Seçenek|Amaç|  
|------------|-------------|  
|[/ bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|Bir hata raporu kolaylaştırır bilgilerini içeren bir dosya oluşturur.|  
|[/ checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|Tamsayı veri türü sınırlarına taşar aritmetik çalışma zamanında bir özel durum neden olup olmayacağını belirtir.|  
|[/ Debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|Hata ayıklama bilgisi yayması için görevlendirin.|  
|[/ errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|Hata Raporlama davranışını ayarlar.|  
|[/ fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|Derleyici çıktısında mutlak dosya yolunu belirtir.|  
|[/ nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|Derleyicinin belirtilen uyarılarının oluşturulmasını önler.|  
|[/ warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|Uyarı düzeyi ayarlar.|  
|[/ warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|Hatalar için uyarıları yükseltir.|  
|/RuleSet:\<dosyası >|Belirli Tanılama'yı devre dışı bırakan bir ruleset belirtin.|  
  
### <a name="preprocessor"></a>Ön işlemci  
  
|Seçenek|Amaç|  
|------------|-------------|  
|[/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|Önişlemci simgelerini tanımlar.|  
  
### <a name="resources"></a>Kaynaklar  
  
|Seçenek|Amaç|  
|------------|-------------|  
|[/ Link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|COM türü bilgileri, belirtilen derlemelerde proje kullanılabilmesini sağlar.|  
|[/ linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|Yönetilen kaynak bağlantısını oluşturur.|  
|[/ Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|.NET Framework kaynağı çıkış dosyası içine katıştırır.|  
|[/ win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|Çıktı dosyasına eklemek için bir .ico dosyasını belirtir.|  
|[/ win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|Çıktı dosyasına eklemek için bir Win32 kaynağı belirtir.|  
  
### <a name="miscellaneous"></a>Diğer  
  
|Seçenek|Amaç|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|Bir yanıt dosyası belirtir.|  
|[/?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Stdout derleyici seçenekleri listeler.|  
|[/ BaseAddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|Tercih edilen temel adrese DLL yükleneceği belirtir.|  
|[/ CodePage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanmak üzere kod sayfasını belirtir.|  
|[/ Help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Stdout derleyici seçenekleri listeler.|  
|[/ highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|Yürütülebilir dosya adres boşluğu düzeni rastgele seçimini (ASLR) desteklediğini belirtir.|  
|[/ langversion](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|Dil sürümü modu belirtin: varsayılan, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1 veya son |  
|[/ main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|Konumunu belirten **ana** yöntemi.|  
|[/ noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|Csc.rsp ile derleme değil derleyiciye.|  
|[/ nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|Derleyici başlık bilgilerini gizler.|  
|[/ recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|Alt dizinleri derlemek kaynak dosyaları için arar.|  
|[/ subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|En düşük sürüm yürütülebilir dosyasını kullanabilirsiniz alt sisteminin belirtir.|  
|[/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|Kullanan kodu derlemesini etkinleştirir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü.|  
|[/ utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|UTF-8 kodlaması kullanarak derleyici çıkışı görüntülenir.|  
|/ Paralel [+ &#124;-]|Eş zamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|  
|/checksumalgorithm:\<algoritma >|PDB içinde depolanan kaynak dosya sağlama toplamı hesaplama algoritması belirtin.  Desteklenen değerler: SHA1 (varsayılan) veya SHA256.|  
  
## <a name="obsolete-options"></a>Artık kullanılmayan seçenekleri  
  
|Seçenek|Amaç|  
|---|---|  
|/ Artımlı|Artımlı derleme sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Alfabetik listelenmiş C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)

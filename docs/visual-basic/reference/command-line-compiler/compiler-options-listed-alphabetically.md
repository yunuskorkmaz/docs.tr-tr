---
title: Alfabetik Olarak Listelenmiş Visual Basic Derleyici Seçenekleri
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f24759d68f007caf5f79096c6d4cebb7c050851
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252440"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Alfabetik listelenmiş Visual Basic derleyici seçenekleri
Visual Basic komut satırı derleyicisi, Visual Studio tümleşik geliştirme ortamından (IDE) programları derleme alternatif olarak sağlanır. Alfabetik olarak sıralanmış Visual Basic derleyici komut satırı seçeneklerinin listesi verilmiştir.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Seçenek|Amaç|  
|------------|-------------|  
|[@ (Yanıt Dosyasını Belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Bir yanıt dosyası belirtir.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçenekleri görüntüler. Bu komut belirtilmesiyle aynıdır `-help` seçeneği. Hiçbir derleme gerçekleşir.|  
|`-additionalfile`|Doğrudan kod üretimini etkilemez, ancak bir hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilir ek dosya adları.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Derleyicinin tüm kullanılabilir belirtilen dosyalar, şu anda derlemekte olduğunuz projeye kullandırmasına bilgileri yazın.|  
|`-analyzer`|Bu derleme Çözümleyicileri çalıştırın (kısa form: - a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Bir DLL temel adresini belirtir.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Bir hatayı raporlamak kolaylaştıran bilgilerini içeren bir dosya oluşturur.|  
|`-checksumalgorithm:<alg>`|PDB içinde depolanan kaynak dosya sağlama toplamı hesaplama algoritması belirtin.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Hata ayıklama bilgisi üretir.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Koşullu derleme sembollerini tanımlar.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Derlemenin tamamen veya kısmen imzalanacağını belirtir.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|İkili içeriği girişleri özdeş ise derlemeler arasında aynıdır derleme çıktısını almak derleyicinin neden olur.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Belge yorumlarını bir XML dosyasına işler.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Visual Basic derleyici iç derleyici hatalarını nasıl raporlayacağını belirtir.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Çıktı dosyasının bölümlerinin hizalanacağı yeri belirtir.|  
|[-Yardım](../../../visual-basic/reference/command-line-compiler/help.md)|Derleyici seçenekleri görüntüler. Bu komut belirtilmesiyle aynıdır `-?` seçeneği. Hiçbir derleme gerçekleşir.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Belirli bir yürütülebilir dosya yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini belirtir.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Bir ad alanı, belirtilen bir derlemesinden içeri aktarır.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Bir derlemeyi tanımlayıcı bir ad vermek bir anahtar çifti için bir anahtar kapsayıcısı adını belirtir.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Bir anahtar veya bir derlemeyi bir katı ad vermek için anahtar çifti içeren bir dosyayı belirtir.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Dil sürümünü belirtin: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Tarafından başvurulan derlemelerin konumunu belirten [-başvuru](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneği.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Yönetilen kaynağa bağlantı oluşturur.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|İçeren sınıf belirtir `Sub Main` başlatma sırasında kullanılacak yordamı.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Bir modülün bir parçası olacağı derlemenin adını belirtir.|  
|`-modulename:<string>`|Kaynak modülünün adını belirtin|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Derleyicinin hedef ayarlar [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nezahrnovat ile derlenmiyor.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Derleyici başlık bilgilerini engellemesidir.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Standart kitaplıkları başvuruda bulunmamaya derleyici neden olur.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Derleyicinin, uyarı oluşturma yeteneğini engeller.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Herhangi bir uygulama bildirimi yürütülebilir dosyasına katıştırma değil derleyicinin sağlar.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Etkinleştirir/devre dışı bırakır, en iyi duruma getirme kodu.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Dize karşılaştırmaları veya ikili yerel ayara özgü metin semantiklerini kullanan belirtir.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Değişkenleri açık bildirimini zorlar.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Değişken bildiriminde yerel tür çıkarımı kullanımını etkinleştirir.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Katı dil semantiklerini zorlar.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Çıkış dosyasını belirtir.|  
|`-parallel[+&#124;-]`|Eş zamanlı derleme (+) kullanılıp kullanılmayacağını belirtir.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|İşlemci platformu çıkış dosyası derleyici hedeflerini belirtir.|  
|`-preferreduilang`|Tercih edilen çıkış dilini belirtin.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Derleyici, kod söz dizimi ile ilgili hatalar ve Uyarılar için görüntülenmesini engeller.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Derlenecek kaynak dosyaların için alt arar.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Bir derlemeye ait meta verileri alır.|  
|[-refonly](refonly-compiler-option.md)|Yalnızca bir başvuru bütünleştirilmiş kodu çıkarır.|
|[-refout](refout-compiler-option.md)|Başvuru bütünleştirilmiş kodu çıkış yolunu belirtir.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Tamsayı taşma denetimini devre dışı bırakır.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Yönetilen kaynak bir derlemeye gömer.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Tüm tür bildirimleri için bir ad alanını belirtir.|  
|`-ruleset:<file>`|Belirli tanılama devre dışı bırakan bir kural kümesi dosyası belirtin.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin konumunu belirtir.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Oluşturulan yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Çıkış dosyasının biçimini belirtir.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|UTF-8 kodlaması kullanarak derleyici çıkışı görüntüler.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Derleyici, Visual Basic çalışma zamanı kitaplığı veya bir belirli çalışma zamanı kitaplık başvurusu olan bir başvuru olmadan derlemesi gerektiğini belirtir.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Derleme sırasında ek bilgiler çıkarır.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Hatalar için uyarıları yükseltir.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Çıktı dosyasına bir .ico simge dosyası ekler.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Bir projenin taşınabilir yürütülebilir (PE) dosya gömülü olması için kullanıcı tanımlı Win32 uygulama bildirim dosyası tanımlar.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Bir Win32 kaynağı çıktı dosyasına ekler.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kategoriye göre listelenmiş Visual Basic derleyici seçenekleri](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)  
 [Proje Tasarımcısı giriş](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7)  
 [Alfabetik Listelenmiş C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-by-category.md)

---
title: Alfabetik Listelenmiş C# Derleyici Seçenekleri
ms.date: 05/15/2018
helpviewer_keywords:
- compiler options [C#], listed alphabetically
- C# language, compiler options listed alphabetically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: d6d471cd27f35de6325a130e6c909d13cb1dcc85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972735"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Alfabetik Listelenmiş C# Derleyici Seçenekleri

Aşağıdaki derleyici seçenekleri alfabetik olarak sıralanır. Kategorik bir liste için, [Kategoriye Göre Listelenen C# Derleyici Seçenekleri'ne](listed-by-category.md)bakın.

|Seçenek|Amaç|
|------------|-------------|
|[@](response-file-compiler-option.md)|Daha fazla seçenek için yanıt dosyalarını okur.|
|[-?](help-compiler-option.md)|Stdout için bir kullanım iletisi görüntüler.|
|-ek dosya|Kod oluşturmayı doğrudan etkilemeyen, ancak çözümleyiciler tarafından hata veya uyarı üretmek için kullanılabilecek ek dosyaları adlandırır.|
|[-addmodule](addmodule-compiler-option.md)|Belirtilen modülleri bu derlemeye bağlar|
|-analizör|Bu derlemeden çözümleyicileri çalıştırın (Kısa form: -a)|
|[-appconfig](appconfig-compiler-option.md)|Derleme bağlama zamanında app.config konumunu belirtir.|
|[-baseaddress](baseaddress-compiler-option.md)|Oluşturulacak kitaplığın temel adresini belirtir.|
|[-bugreport](bugreport-compiler-option.md)|Bir 'Hata Raporu' dosyası oluşturur. Bu dosya -errorreport:prompt veya -errorreport:send ile kullanılırsa, herhangi bir kilitlenme bilgisi ile birlikte gönderilir.|
|[-kontrol edildi](checked-compiler-option.md)|Derleyicinin taşma denetimleri oluşturmasına neden olur.|
|-checksumalgorithm:\<alg>|PDB'de depolanan kaynak dosya checksum'u hesaplamak için algoritmayı belirtir.  Desteklenen değerler şunlardır: SHA256 (varsayılan) veya SHA1.<br>SHA1 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir. |
|[-codepage](codepage-compiler-option.md)|Kaynak dosyaları açarken kullanılacak kod sayfasını belirtir.|
|[-hata ayıklama](debug-compiler-option.md)|Hata ayıklama bilgilerini yayar.|
|[-define](define-compiler-option.md)|Koşullu derleme sembollerini tanımlar.|
|[-delaysign](delaysign-compiler-option.md)|Güçlü ad anahtarının yalnızca ortak kısmını kullanarak montajı geciktirir.|
|[-deterministic](deterministic-compiler-option.md)|Derleyicinin, girişler aynıysa, ikili içeriği derlemeler arasında aynı olan bir derlemeyi çıktısına neden olur.|
|[-doc](doc-compiler-option.md)|Oluşturmak için bir XML Dokümantasyon dosyası belirtir.|
|-gömmek|Tüm kaynak dosyaları PDB'ye gömün.|
|-gömmek:\<dosya listesi>|BELIRLI dosyaları PDB'ye gömün.|
|-hata son konumu|Her hatanın bitiş konumunun çıktı satırı ve sütunu.|
|-errorlog:\<dosya>|Tüm derleyici ve çözümleyici tanılama günlüğe kaydetmek için bir dosya belirtin.|
|[-errorreport](errorreport-compiler-option.md)|İç derleyici hatalarının nasıl işleyeceğini belirtir: istem, gönderme veya hiç. Varsayılan değer none'dır.|
|[-filealign](filealign-compiler-option.md)|Çıktı dosyası bölümleri için kullanılan hizalamayı belirtir.|
|[-fullpaths](fullpaths-compiler-option.md)|Derleyicinin tam nitelikli yollar oluşturmasına neden olur.|
|[-yardım](help-compiler-option.md)|Stdout için bir kullanım iletisi görüntüler.|
|[-highentropyva](highentropyva-compiler-option.md)|Yüksek entropi ASLR'Nin desteklenir olduğunu belirtir.|
|-artımlı|Artımlı derlemeyi [eski] sağlar.|
|[-keycontainer](keycontainer-compiler-option.md)|Güçlü bir ad anahtar kapsayıcıbelirtir.|
|[-keyfile](keyfile-compiler-option.md)|Güçlü bir ad anahtarı dosyası belirtir.|
|[-langversion:\<dize>](langversion-compiler-option.md)|Dil sürümünü belirtin: Varsayılan, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 veya En Son |
|[-lib](lib-compiler-option.md)|Başvuruları aramak için ek dizinler belirtir.|
|[-bağlantı](link-compiler-option.md)|Belirtilen derlemelerde COM türü bilgilerini projenin kullanımına açık hale getirir.|
|[-linkresource](linkresource-compiler-option.md)|Belirtilen kaynağı bu derlemeye bağlar.|
|[-main](main-compiler-option.md)|Giriş noktasını içeren türü belirtir (diğer tüm olası giriş noktalarını yoksay).|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Ortak olmayan türleri bir .netmodule erişebileceği bir derleme belirtir.|
|-modulename:\<string>|Kaynak modülün adını belirtin|
|[-noconfig](noconfig-compiler-option.md)|Derleyiciye CSC'yi otomatik olarak eklememesi talimatını verir. RSP dosyası.|
|[-nologo](nologo-compiler-option.md)|Derleyici telif hakkı iletisi bastırır.|
|[-nostdlib](nostdlib-compiler-option.md)|Derleyiciye standart kitaplık (mscorlib.dll) göndermemesi için talimat verir.|
|[-nowarn](nowarn-compiler-option.md)|Belirli uyarı iletilerini devre dışı kılabilir|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Derleyiciye yürütülebilir dosyaya bir uygulama bildirimi gömmemesi talimatını verir.|
|[-optimize etmek](optimize-compiler-option.md)|Optimizasyonları etkinleştiri/devre dışı kılabilir.|
|[-çıkış](out-compiler-option.md)|Çıktı dosya adını belirtir (varsayılan: ana sınıf veya ilk dosya içeren dosyanın temel adı).|
|-paralel[+&#124;-]|Eşzamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|
|[-pathmap](pathmap-compiler-option.md)|Derleyici tarafından kaynak yol adları çıktısı için bir eşleme belirtir.|
|[-pdb](pdb-compiler-option.md)|.pdb dosyasının dosya adını ve konumunu belirtir.|
|[-platform](platform-compiler-option.md)|Bu kodun hangi platformlarda çalıştırılabildiği sınırlar: x86, Itanium, x64, anycpu veya anycpu32bitpreferred. Varsayılan anycpu olduğunu.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Derleyici çıktısı için kullanılacak dili belirtir.|
|[-publicsign](publicsign-compiler-option.md)|Derlemeyi imzalamadan ortak anahtar uygulayın, ancak mecliste montajın imzalanmış olduğunu belirten biti ayarlayın.|
|[-recurse](recurse-compiler-option.md)|Joker karakter özelliklerine göre geçerli dizindeki tüm dosyaları ve alt dizini içerir.|
|[-referans](reference-compiler-option.md)|Belirtilen derleme dosyalarından meta verilere başvurur.|
|[-refout](refout-compiler-option.md)|Birincil derlemeye ek olarak bir başvuru derlemesi oluşturun.|
|[-refonly](refonly-compiler-option.md)|Birincil derleme yerine bir başvuru derlemesi oluşturun.|
|-reportanalyzer|Yürütme süresi gibi ek çözümleyici bilgilerini bildirin.|
|[-kaynak](resource-compiler-option.md)|Belirtilen kaynağı katıştırıyor.|
|-ruleset:\<dosya>|Belirli tanılamadevre devre dışı bırakan bir kural kümesi dosyası belirtin.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Çalıştırılabilir dosyanın kullanabileceği alt sistemin minimum sürümünü belirtir.|
|[-hedef](target-compiler-option.md)|Çıkış dosyasının biçimini dört seçenekten birini kullanarak belirtir: [-hedef:appcontainerexe](target-appcontainerexe-compiler-option.md), [-target:exe](target-exe-compiler-option.md), [-target:library](target-library-compiler-option.md), [-target:module](target-module-compiler-option.md), [-target:winexe](target-winexe-compiler-option.md), [-target:winmdobj](target-winmdobj-compiler-option.md).|
|[-unsafe](unsafe-compiler-option.md)|[Güvenli olmayan](../keywords/unsafe.md) kod sağlar.|
|[-utf8output](utf8output-compiler-option.md)|UTF-8 kodlamasında derleyici iletileri çıktıları.|
|-sürüm|Derleyici sürüm numarasını ve çıkışını görüntüleyin.|
|[-warn](warn-compiler-option.md)|Uyarı düzeyini ayarlar (0-4).|
|[-warnaserror](warnaserror-compiler-option.md)|Belirli uyarıları hata olarak bildirir.|
|[-win32icon](win32icon-compiler-option.md)|Çıktı için bu simgeyi kullanır.|
|[-win32manifest](win32manifest-compiler-option.md)|Özel bir win32 bildirim dosyası belirtir.|
|[-win32res](win32res-compiler-option.md)|win32 kaynak dosyasını (.res) belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](listed-by-category.md)
- [Visual Studio Komut Satırı için ortam değişkenlerini ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<derleyici> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)

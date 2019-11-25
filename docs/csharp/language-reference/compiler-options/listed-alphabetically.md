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
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972735"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Alfabetik Listelenmiş C# Derleyici Seçenekleri

Aşağıdaki derleyici seçenekleri alfabetik olarak sıralanır. Kategorik bir liste için, bkz [ C# . kategoriye göre listelenen derleyici seçenekleri](listed-by-category.md).

|Seçenek|Amaç|
|------------|-------------|
|[@](response-file-compiler-option.md)|Daha fazla seçenek için bir yanıt dosyası okur.|
|[-?](help-compiler-option.md)|Stdout için bir kullanım iletisi görüntüler.|
|-additionalfile|Kod oluşturmayı doğrudan etkilemeyen, ancak hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilen ek dosyaları adlandırır.|
|[-addmodule](addmodule-compiler-option.md)|Belirtilen modülleri bu derlemeye bağlar|
|-çözümleyici|Bu derlemeden çözümleyiciler çalıştırın (kısa biçim:-a)|
|[-appconfig](appconfig-compiler-option.md)|Derleme bağlama zamanında app. config dosyasının konumunu belirtir.|
|[-baseaddress](baseaddress-compiler-option.md)|Oluşturulacak kitaplığın temel adresini belirtir.|
|[-bugreport](bugreport-compiler-option.md)|' Hata raporu ' dosyası oluşturur. Bu dosya,-errorreport: Prompt veya-errorreport: Send ile kullanılırsa tüm kilitlenme bilgileriyle birlikte gönderilir.|
|[-checked](checked-compiler-option.md)|Derleyicinin taşma denetimleri oluşturmasına neden olur.|
|-checksumalgorithm:\<alg >|PDB 'de depolanan kaynak dosyası sağlama toplamını hesaplamak için algoritmayı belirtir.  Desteklenen değerler şunlardır: SHA256 (varsayılan) veya SHA1.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir. |
|[-codepage](codepage-compiler-option.md)|Kaynak dosyalar açılırken kullanılacak kod sayfasını belirtir.|
|[-debug](debug-compiler-option.md)|Hata ayıklama bilgilerini yayar.|
|[-define](define-compiler-option.md)|Koşullu derleme sembollerini tanımlar.|
|[-delaysign](delaysign-compiler-option.md)|Derlemeyi yalnızca tanımlayıcı ad anahtarının ortak kısmını kullanarak imzalar.|
|[-deterministic](deterministic-compiler-option.md)|Girişlerin özdeş olması halinde, derleyicinin ikili içerik özdeş olan bir derlemeyi çıkış yapmasına neden olur.|
|[-doc](doc-compiler-option.md)|Oluşturulacak XML belge dosyasını belirtir.|
|-katıştır|Tüm kaynak dosyalarını PDB 'ye ekleyin.|
|-Embed:\<dosya listesi >|PDB 'ye belirli dosyaları ekleyin.|
|-errorendlocation|Her hatanın bitiş konumunun çıkış satırı ve sütunu.|
|-hata günlüğü:\<Dosya >|Tüm derleyici ve çözümleyici tanılamayı günlüğe kaydetmek için bir dosya belirtin.|
|[-errorreport](errorreport-compiler-option.md)|İç derleyici hatalarının nasıl işleneceğini belirtir: Prompt, Send veya None. Varsayılan değer None ' dır.|
|[-filealign](filealign-compiler-option.md)|Çıkış dosyası bölümleri için kullanılan hizalamayı belirtir.|
|[-fullpaths](fullpaths-compiler-option.md)|Derleyicinin tam olarak nitelenmiş yollar oluşturmasına neden olur.|
|[-yardım](help-compiler-option.md)|Stdout için bir kullanım iletisi görüntüler.|
|[-highentropyva](highentropyva-compiler-option.md)|Yüksek entropi ASLR desteklendiğini belirtir.|
|-artımlı|Artımlı derlemeyi [eski] izin vermez.|
|[-keycontainer](keycontainer-compiler-option.md)|Bir tanımlayıcı ad anahtar kapsayıcısı belirtir.|
|[-keyfile](keyfile-compiler-option.md)|Tanımlayıcı ad anahtar dosyasını belirtir.|
|[-langversion:\<dize >](langversion-compiler-option.md)|Dil sürümünü belirtin: varsayılan, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7,1, 7,2, 7,3 veya en son |
|[-lib](lib-compiler-option.md)|Başvuruların aranacağı ek dizinleri belirtir.|
|[-link](link-compiler-option.md)|Belirtilen derlemelerdeki COM türü bilgilerini proje için kullanılabilir hale getirir.|
|[-linkresource](linkresource-compiler-option.md)|Belirtilen kaynağı bu derlemeye bağlar.|
|[-main](main-compiler-option.md)|Giriş noktasını içeren türü belirtir (diğer tüm olası giriş noktalarını yoksayın).|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Genel olmayan türleri bir. netmodule 'nin erişebileceği bir derlemeyi belirtir.|
|-ModuleName:\<String >|Kaynak modülünün adını belirtin|
|[-noconfig](noconfig-compiler-option.md)|Derleyiciye CSC 'yi otomatik olarak eklemesi talimatını verir. RSP dosyası.|
|[-nologo](nologo-compiler-option.md)|Derleyici telif hakkı iletisini bastırır.|
|[-nostdlib](nostdlib-compiler-option.md)|Derleyiciye standart kitaplığa (mscorlib. dll) Başvurmamasını söyler.|
|[-nowarn](nowarn-compiler-option.md)|Belirli uyarı iletilerini devre dışı bırakır|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Derleyicinin yürütülebilir dosyaya bir uygulama bildirimi katıştırmamasını sağlar.|
|[-optimize](optimize-compiler-option.md)|İyileştirmeleri etkinleştirilir/devre dışı bırakır.|
|[-out](out-compiler-option.md)|Çıkış dosyası adını belirtir (varsayılan: Ana sınıf veya ilk dosya ile dosyanın temel adı).|
|-Parallel [+&#124;-]|Eşzamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|
|[-pathmap](pathmap-compiler-option.md)|Derleyici tarafından çıkış kaynak yolu adları için bir eşleme belirtir.|
|[-pdb](pdb-compiler-option.md)|Dosya adını ve. pdb dosyasının konumunu belirtir.|
|[-platform](platform-compiler-option.md)|Bu kodun çalıştırılabileceği platformları sınırlar: x86, Itanium, x64, anycpu veya anycpu32bitpreferred. Varsayılan değer anycpu ' dır.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Derleyici çıktısı için kullanılacak dili belirtir.|
|[-publicsign](publicsign-compiler-option.md)|Derlemeyi imzalamadan ortak anahtar uygulayın, ancak derlemenin imzalandığını belirten derlemede bit ayarlayın.|
|[-recurse](recurse-compiler-option.md)|Joker karakter belirtimlerine göre geçerli dizindeki ve alt dizinlerdeki tüm dosyaları içerir.|
|[-reference](reference-compiler-option.md)|Belirtilen derleme dosyalarından meta verilere başvurur.|
|[-refout](refout-compiler-option.md)|Birincil derlemeye ek olarak bir başvuru bütünleştirilmiş kodu oluşturun.|
|[-refonly](refonly-compiler-option.md)|Birincil derleme yerine bir başvuru bütünleştirilmiş kodu oluşturun.|
|-reportanalyzer|Yürütme süresi gibi ek çözümleyici bilgilerini bildirin.|
|[-resource](resource-compiler-option.md)|Belirtilen kaynağı katıştırır.|
|-RuleSet:\<Dosya >|Belirli tanılamayı devre dışı bırakan bir RuleSet dosyası belirtin.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir.|
|[-target](target-compiler-option.md)|Dört seçenekten birini kullanarak çıkış dosyasının biçimini belirtir: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: Library](target-library-compiler-option.md), [-target: Module](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), [-target: winmdobj](target-winmdobj-compiler-option.md).|
|[-unsafe](unsafe-compiler-option.md)|[Güvenli olmayan](../keywords/unsafe.md) koda izin verir.|
|[-utf8output](utf8output-compiler-option.md)|Derleyici iletilerini UTF-8 kodlamasında çıkarır.|
|-sürüm|Derleyici sürüm numarasını ve çıkışı görüntüleyin.|
|[-warn](warn-compiler-option.md)|Uyarı düzeyini (0-4) ayarlar.|
|[-warnaserror](warnaserror-compiler-option.md)|Belirli uyarıları hata olarak raporlar.|
|[-win32icon](win32icon-compiler-option.md)|Çıkış için bu simgeyi kullanır.|
|[-win32manifest](win32manifest-compiler-option.md)|Özel bir Win32 bildirim dosyası belirtir.|
|[-win32res](win32res-compiler-option.md)|Win32 kaynak dosyasını (. res) belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](listed-by-category.md)
- [Visual Studio komut satırı için ortam değişkenlerini ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<derleyici > öğesi](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)

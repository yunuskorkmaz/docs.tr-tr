---
title: Alfabetik Listelenmiş C# Derleyici Seçenekleri
ms.date: 05/15/2018
helpviewer_keywords:
- compiler options [C#], listed alpabetically
- C# language, compiler options listed alphabitically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: ca21aeb6ae1cf53bc3ff4edbcf575b733a52a1cf
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
---
# <a name="c-compiler-options-listed-alphabetically"></a>Alfabetik Listelenmiş C# Derleyici Seçenekleri

Aşağıdaki derleyici seçenekleri alfabetik olarak sıralanır. Kategorik bir listesi için bkz: [C# derleyici seçenekleri listelenen kategoriye göre](listed-by-category.md).

|Seçenek|Amaç|
|------------|-------------|
|[@](response-file-compiler-option.md)|Daha fazla seçenek için bir yanıt dosyasını okur.|
|[-?](help-compiler-option.md)|Stdout kullanım iletisini görüntüler.|
|-additionalfile|Kod oluşturma doğrudan etkilemez ancak çözümleyicileri tarafından hatalar veya uyarılar üretmek için kullanılabilir başka dosya adları.|
|[-addmodule](addmodule-compiler-option.md)|Belirtilen modülleri bu derlemeye bağlar|
|-Çözümleyicisi|Bu derlemedeki çözümleyiciler çalıştırın (kısa form: - a)|
|[-appconfig](appconfig-compiler-option.md)|Derleme bağlama zamanında app.config konumunu belirtir.|
|[-baseaddress](baseaddress-compiler-option.md)|Oluşturulacak kitaplığın temel adresini belirtir.|
|[-bugreport](bugreport-compiler-option.md)|'Hata raporu' dosyası oluşturur. -Errorreport ile kullandıysanız, bu dosyayı herhangi çökmesi bilgi ile birlikte gönderilir: istemi veya - errorreport: gönderin.|
|[-checked](checked-compiler-option.md)|Derleyicinin taşma denetimleri oluşturmasına neden olur.|
|-checksumalgorithm:\<algoritma >|PDB içinde depolanan kaynak dosya sağlama toplamı hesaplamak için algoritmasını belirtir.  Desteklenen değerler: SHA1 (varsayılan) veya SHA256.|
|[-codepage](codepage-compiler-option.md)|Kaynak dosyalar açılırken kullanılacak kod sayfasını belirtir.|
|[-debug](debug-compiler-option.md)|Hata ayıklama bilgisi yayar.|
|[-define](define-compiler-option.md)|Koşullu derleme simgelerini tanımlar.|
|[-delaysign](delaysign-compiler-option.md)|Gecikmeli imzalar güçlü ad anahtarı yalnızca ortak kısmını kullanarak derleme.|
|[-deterministic](deterministic-compiler-option.md)|Derleyicinin girişleri özdeş ise ikili içerikleri derlemeleri arasında aynı olan bir derleme çıktı neden olur.|
|[-doc](doc-compiler-option.md)|Bir XML belge dosyası oluşturmak için belirtir.|
|[-errorreport](errorreport-compiler-option.md)|Derleyici iç hataların nasıl işleneceğini belirtir: istemi, Gönder veya yok. Varsayılan, Yok'tur.|
|[-filealign](filealign-compiler-option.md)|Çıkış dosyası bölümleri için kullanılan hizalamasını belirtir.|
|[-fullpaths](fullpaths-compiler-option.md)|Derleyicinin tam olarak nitelenmiş yollar oluşturmasına neden olur.|
|[-Yardım](help-compiler-option.md)|Stdout kullanım iletisini görüntüler.|
|[-highentropyva](highentropyva-compiler-option.md)|ASLR desteklenen bu yüksek entropi belirtir.|
|-artan|Artımlı derlemeyi [eski] sağlar.|
|[-keycontainer](keycontainer-compiler-option.md)|Güçlü ad anahtar kapsayıcısı belirtir.|
|[-keyfile](keyfile-compiler-option.md)|Güçlü ad anahtar dosyası belirtir.|
|[-langversion:\<dize >](langversion-compiler-option.md)|Dil sürümünü belirtin: varsayılan, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 ya da son |
|[-lib](lib-compiler-option.md)|Ek başvurular için aranacak dizinlerde belirtir.|
|[-link](link-compiler-option.md)|COM türü bilgileri, belirtilen derlemelerde proje kullanılabilmesini sağlar.|
|[-linkresource](linkresource-compiler-option.md)|Belirtilen kaynak bu derlemeye bağlar.|
|[-main](main-compiler-option.md)|Giriş noktası içeren türünü belirtir (diğer tüm giriş noktalarını yoksayar).|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Ortak olmayan türlere bir .netmodule erişebileceği bir derleme belirtir.|
|-modulename:\<dize >|Kaynak modülünün adını belirtin|
|[-noconfig](noconfig-compiler-option.md)|Otomatik derleyiciye CSC içerir. RSP dosyası.|
|[-nologo](nologo-compiler-option.md)|Derleyici telif hakkı iletisi gizler.|
|[-nostdlib](nostdlib-compiler-option.md)|Başvuru standart kitaplığı (mscorlib.dll) için derleyiciye.|
|[-nowarn](nowarn-compiler-option.md)|Özel uyarı iletilerini devre dışı bırakır|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Bir uygulama bildirimi yürütülebilir dosyasına katıştırma değil derleyiciye.|
|[-optimize](optimize-compiler-option.md)|En iyi duruma getirme etkinleştirir/devre dışı bırakır.|
|[-out](out-compiler-option.md)|Çıkış dosyası adı belirtin (varsayılan: ana sınıfı içeren dosyanın veya ilk dosyanın temel adı).|
|-Paralel [+&#124;-]|Eş zamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|
|[-pathmap](pathmap-compiler-option.md)|Kaynak yolu adları çıktısı için bir eşleme derleyici tarafından belirtir.|
|[-pdb](pdb-compiler-option.md)|.Pdb dosyasının konumu ve dosya adını belirtir.|
|[-platform](platform-compiler-option.md)|Hangi platformları bu kodun çalışabileceği sınırları: x86, Itanium, x 64, anycpu, veya anycpu32bitpreferred. Anycpu varsayılandır.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Derleyici çıktı için kullanılacak dili belirtir.|
|[-publicsign](publicsign-compiler-option.md)|Derleme imzalama olmadan bir ortak anahtar geçerli, ancak derleme imzalanmamış belirten derlemede bit ayarlayın.|
|[-recurse](recurse-compiler-option.md)|Geçerli dizindeki ve alt dizinleri joker karakteri belirtimlerine göre tüm dosyaları içerir.|
|[-reference](reference-compiler-option.md)|Belirtilen derleme dosyalarından meta verilere başvurur.|
|[-refout](refout-compiler-option.md)|Bir referans derlemesini birincil derlemesinin yanı sıra oluşturur.|
|[-refonly](refonly-compiler-option.md)|Bir referans derlemesini birincil derlemesi yerine oluşturur.|
|[-resource](resource-compiler-option.md)|Belirtilen kaynak katıştırır.|
|-ruleset:\<dosyası >|Belirli Tanılama'yı devre dışı bırakan bir ruleset belirtin.|
|[-subsystemversion](subsystemversion-compiler-option.md)|En düşük sürüm yürütülebilir dosyasını kullanabilirsiniz alt sisteminin belirtir.|
|[-target](target-compiler-option.md)|Dört seçenekten birini kullanarak çıktı dosyası biçimini belirtir: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [-hedef: Modül](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), [-target: winmdobj](target-winmdobj-compiler-option.md).|
|[-unsafe](unsafe-compiler-option.md)|Verir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) kodu.|
|[-utf8output](utf8output-compiler-option.md)|Çıkış derleyici iletilerini UTF-8 kodlaması.|
|[-warn](warn-compiler-option.md)|Uyarı düzeyi (0-4) ayarlar.|
|[-warnaserror](warnaserror-compiler-option.md)|Belirli uyarıları hata olarak bildirir.|
|[-win32icon](win32icon-compiler-option.md)|Bu simgeyi çıkış için kullanır.|
|[-win32manifest](win32manifest-compiler-option.md)|Özel bir win32 bildirim dosyasını belirtir.|
|[-win32res](win32res-compiler-option.md)|Win32 kaynak dosyasını (.res) belirtir.|

## <a name="see-also"></a>Ayrıca Bkz.

 [C# Derleyici Seçenekleri](index.md)  
 [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](listed-by-category.md)  
 [Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [\<Derleyici > öğesi](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)

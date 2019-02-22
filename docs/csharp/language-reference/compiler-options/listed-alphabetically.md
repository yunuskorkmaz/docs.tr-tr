---
title: Alfabetik Listelenmiş C# Derleyici Seçenekleri
ms.date: 05/15/2018
helpviewer_keywords:
- compiler options [C#], listed alpabetically
- C# language, compiler options listed alphabitically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: 7be62b3a97614faea14eb874be58c79246754903
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583660"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Alfabetik Listelenmiş C# Derleyici Seçenekleri

Aşağıdaki derleyici seçeneklerinin alfabetik olarak sıralanır. Kategorisel liste için bkz: [C# derleyici seçenekleri kategoriye göre listelenmiş](listed-by-category.md).

|Seçenek|Amaç|
|------------|-------------|
|[@](response-file-compiler-option.md)|Daha fazla seçenek için bir yanıt dosyasını okur.|
|[-?](help-compiler-option.md)|Stdout kullanım iletisini görüntüler.|
|-additionalfile|Doğrudan kod üretimini etkilemez, ancak bir hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilir ek dosya adları.|
|[-addmodule](addmodule-compiler-option.md)|Belirtilen modülleri bu derlemeye bağlar.|
|-Çözümleyicisi|Bu derleme Çözümleyicileri çalıştırın (kısa form: - a)|
|[-appconfig](appconfig-compiler-option.md)|Derleme bağlama zamanında app.config konumunu belirtir.|
|[-baseaddress](baseaddress-compiler-option.md)|Oluşturulacak kitaplığın temel adresini belirtir.|
|[-bugreport](bugreport-compiler-option.md)|'Hata raporu' dosyası oluşturur. -Errorreport ile kullanılıyorsa, bu dosyayı herhangi bir kilitlenme bilgi ile birlikte gönderilir: komut istemi veya - errorreport: gönderin.|
|[-checked](checked-compiler-option.md)|Taşma denetimleri oluşturmak derleyicinin neden olur.|
|-checksumalgorithm:\<algoritma >|PDB içinde depolanan kaynak dosya sağlama toplamı hesaplama algoritmasını belirtir.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256.|
|[-codepage](codepage-compiler-option.md)|Kaynak dosyalar açılırken kullanılacak kod sayfasını belirtir.|
|[-debug](debug-compiler-option.md)|Hata ayıklama bilgilerini gösterir.|
|[-define](define-compiler-option.md)|Koşullu derleme sembollerini tanımlar.|
|[-delaysign](delaysign-compiler-option.md)|Gecikmeli imzalar derlemenin tanımlayıcı ad anahtarının yalnızca ortak bölümünü kullanarak.|
|[-deterministic](deterministic-compiler-option.md)|İkili içeriği girişleri özdeş ise derlemeler arasında aynıdır derleme çıktısını almak derleyicinin neden olur.|
|[-doc](doc-compiler-option.md)|Oluşturmak için bir XML belgesi dosyasını belirtir.|
|-ekleme|Tüm kaynak dosyaları PDB'de ekleyin.|
|-ekleme:\<dosya listesi >|Belirli dosyaları PDB'de ekleyin.|
|-errorendlocation|Çıkış satırı ve sütunu her hatanın bitiş konumunun.|
|-errorlog:\<file>|Tüm derleyici ve Çözümleyicisi tanılama günlük dosyayı belirtin.|
|[-errorreport](errorreport-compiler-option.md)|Derleyici iç hatalarının nasıl işleneceğini belirtir: istemi, Gönder veya yok. Varsayılan, Yok'tur.|
|[-filealign](filealign-compiler-option.md)|Çıkış dosyası bölümleri için kullanılan hizalamayı belirtir.|
|[-fullpaths](fullpaths-compiler-option.md)|Derleyicinin tam olarak nitelenmiş yollar oluşturmasını neden olur.|
|[-Yardım](help-compiler-option.md)|Stdout kullanım iletisini görüntüler.|
|[-highentropyva](highentropyva-compiler-option.md)|Bu yüksek entropi aslr desteği belirtir.|
|-artan|[Eski] Artımlı derlemeyi etkinleştirir.|
|[-keycontainer](keycontainer-compiler-option.md)|Tanımlayıcı ad anahtar kapsayıcısı belirtir.|
|[-keyfile](keyfile-compiler-option.md)|Tanımlayıcı ad anahtar dosyası belirtir.|
|[-langversion:\<dize >](langversion-compiler-option.md)|Dil sürümünü belirtin: Varsayılan, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 veya en son |
|[-lib](lib-compiler-option.md)|Başvurular için aranacağı ek dizinleri belirtir.|
|[-link](link-compiler-option.md)|COM tür bilgilerini belirtilen derlemeleri projeye kullanılabilir hale getirir.|
|[-linkresource](linkresource-compiler-option.md)|Belirtilen kaynağı bu derlemeye bağlar.|
|[-main](main-compiler-option.md)|Giriş noktasını içeren türü belirtir (diğer tüm olası girdi noktalarını yok sayar).|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Genel olmayan türler .netmodule erişebilmeniz için bir derleme belirtir.|
|-modulename:\<dize >|Kaynak modülünün adını belirtin|
|[-noconfig](noconfig-compiler-option.md)|Derleyiciye otomatik olmayan CSC içerir. RSP dosyası.|
|[-nologo](nologo-compiler-option.md)|Derleyici telif hakkı iletisini bastırır.|
|[-nostdlib](nostdlib-compiler-option.md)|Derleyicinin başvuru standart kitaplığa (mscorlib.dll) için sağlar.|
|[-nowarn](nowarn-compiler-option.md)|Belirli uyarı iletilerini devre dışı bırakır|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Bir uygulama bildirimi yürütülebilir dosyasına katıştırma değil derleyicinin sağlar.|
|[-optimize](optimize-compiler-option.md)|İyileştirmeleri etkinleştirir/devre dışı bırakır.|
|[-out](out-compiler-option.md)|Çıkış dosyası adını belirtir (varsayılan: ana sınıfı içeren dosyanın veya ilk dosyanın temel adı).|
|-Paralel [+&#124;-]|Eş zamanlı derleme (+) kullanılıp kullanılmayacağını belirtir.|
|[-pathmap](pathmap-compiler-option.md)|Kaynak yol adları çıkış için bir eşleme derleyici tarafından belirtir.|
|[-pdb](pdb-compiler-option.md)|.Pdb dosyasının konumunu ve dosya adını belirtir.|
|[-platform](platform-compiler-option.md)|Hangi platformların bu kod üzerinde çalıştırılabilir sınırları: x86, Itanium, x 64, anycpu veya anycpu32bitpreferred. Anycpu varsayılandır.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Derleyici çıktısı için kullanılacak dili belirtir.|
|[-publicsign](publicsign-compiler-option.md)|Bir ortak anahtar derleme imzalamadan geçerlidir ancak derleme imzalanması belirten derlemede biti ayarlanmış.|
|[-recurse](recurse-compiler-option.md)|Geçerli dizin ve joker karakteri belirtimlerine göre alt dizinlerdeki tüm dosyaları içerir.|
|[-reference](reference-compiler-option.md)|Belirtilen derleme dosyalarından meta verilere başvurur.|
|[-refout](refout-compiler-option.md)|Birincil derlemesi ek olarak bir başvuru bütünleştirilmiş kodu oluşturur.|
|[-refonly](refonly-compiler-option.md)|Birincil bir derleme yerine bir başvuru bütünleştirilmiş kodu oluşturur.|
|-reportanalyzer|Yürütme süresi gibi ek Çözümleyicisi bilgileri rapor.|
|[-resource](resource-compiler-option.md)|Belirtilen kaynak katıştırır.|
|-Kural kümesi:\<dosyası >|Belirli tanılama devre dışı bırakan bir kural kümesi dosyası belirtin.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir.|
|[-target](target-compiler-option.md)|Dört seçenekten birini kullanarak çıkış dosyasının biçimini belirtir: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [-hedef: Modül](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), [-target: winmdobj](target-winmdobj-compiler-option.md).|
|[-unsafe](unsafe-compiler-option.md)|Sağlar [güvenli](../../../csharp/language-reference/keywords/unsafe.md) kod.|
|[-utf8output](utf8output-compiler-option.md)|Çıkışları derleyici iletilerini UTF-8 kodlaması.|
|-Sürüm|Derleyicinin sürüm numarası ve çıkış görüntüler.|
|[-warn](warn-compiler-option.md)|Uyarı düzeyi (0-4) ayarlar.|
|[-warnaserror](warnaserror-compiler-option.md)|Belirli uyarıları hata olarak bildirir.|
|[-win32icon](win32icon-compiler-option.md)|Bu simge, çıkış için kullanır.|
|[-win32manifest](win32manifest-compiler-option.md)|Özel bir win32 bildirim dosyasını belirtir.|
|[-win32res](win32res-compiler-option.md)|Win32 kaynak dosyası (.res) belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Kategorilere Göre Listelenen C# Derleyici Seçenekleri](listed-by-category.md)
- [Nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<Derleyici > öğesi](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)

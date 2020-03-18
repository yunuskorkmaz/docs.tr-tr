---
title: Kategorilere Göre Listelenen C# Derleyici Seçenekleri
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 5cd5607c25dabd8f56ebb58366116666e8e649ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972713"
---
# <a name="c-compiler-options-listed-by-category"></a>Kategorilere Göre Listelenen C# Derleyici Seçenekleri

Aşağıdaki derleyici seçenekleri kategoriye göre sıralanır. Alfabetik bir liste için, [Alfabetik olarak listelenen C# Derleyici Seçenekleri'ne](listed-alphabetically.md)bakın.

## <a name="optimization"></a>İyileştirme

|Seçenek|Amaç|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Çıktı dosyasındaki bölümlerin boyutunu belirtir.|
|[-optimize etmek](optimize-compiler-option.md)|Optimizasyonları etkinleştiri/devre dışı kılabilir.|

## <a name="output-files"></a>Çıkış Dosyaları

|Seçenek|Amaç|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Derleyicinin, girişler aynıysa, ikili içeriği derlemeler arasında aynı olan bir derlemeyi çıktısına neden olur.|
|[-doc](doc-compiler-option.md)|İşlenmiş belge açıklamalarının yazılması gereken bir XML dosyasını belirtir.|
|[-çıkış](out-compiler-option.md)|Çıktı dosyasını belirtir.|
|[-pathmap](pathmap-compiler-option.md)|Derleyici tarafından kaynak yol adları çıktısı için eşleme belirtin|
|[-pdb](pdb-compiler-option.md)|.pdb dosyasının dosya adını ve konumunu belirtir.|
|[-platform](platform-compiler-option.md)|Çıktı platformını belirtin.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Derleyici çıktısı için bir dil belirtin.|
|[-refout](refout-compiler-option.md)|Birincil derlemeye ek olarak bir başvuru derlemesi oluşturun.|
|[-refonly](refonly-compiler-option.md)|Birincil derleme yerine bir başvuru derlemesi oluşturun.|
|[-hedef](target-compiler-option.md)|Beş seçenekten birini kullanarak çıktı dosyasının biçimini belirtir: [-hedef:appcontainerexe](target-appcontainerexe-compiler-option.md), [-target:exe](target-exe-compiler-option.md), [-target:library](target-library-compiler-option.md), [-target:module](target-module-compiler-option.md), [-target:winexe](target-winexe-compiler-option.md), veya [-target:winmdobj](target-winmdobj-compiler-option.md).|
|-modulename:\<string>|Kaynak modülün adını belirtin|

## <a name="net-framework-assemblies"></a>.NET Çerçeve Meclisleri

|Seçenek|Amaç|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Bir veya daha fazla modülün bu derlemenin bir parçası olmasını belirtir.|
|[-delaysign](delaysign-compiler-option.md)|Derleyiciye ortak anahtarı eklemesini, ancak derlemeyi imzasız bırakmasını bildirir.|
|[-keycontainer](keycontainer-compiler-option.md)|Şifreleme anahtar kapsayıcısının adını belirtir.|
|[-keyfile](keyfile-compiler-option.md)|Şifreleme anahtarını içeren dosya adını belirtir.|
|[-lib](lib-compiler-option.md)|[-referans](reference-compiler-option.md)yoluyla başvurulan derlemelerin konumunu belirtir.|
|[-nostdlib](nostdlib-compiler-option.md)|Derleyiciye standart kitaplığı (mscorlib.dll) almamasını bildirir.|
|[-publicsign](publicsign-compiler-option.md)|Derlemeyi imzalamadan ortak anahtar uygulayın, ancak mecliste montajın imzalanmış olduğunu belirten biti ayarlayın.|
|[-referans](reference-compiler-option.md)|Derleme içeren bir dosyadan meta veri aktarın.|
|-analizör|Bu derlemeden çözümleyicileri çalıştırın (Kısa form: /a)|
|-ek dosya|Kod oluşturmayı doğrudan etkilemeyen, ancak çözümleyiciler tarafından hata veya uyarı üretmek için kullanılabilecek ek dosyaları adlandırır.|
|-gömmek|Tüm kaynak dosyaları PDB'ye gömün.|
|-gömmek:\<dosya listesi>|BELIRLI dosyaları PDB'ye gömün.|
## <a name="debuggingerror-checking"></a>Hata Ayıklama/Hata Denetimi

|Seçenek|Amaç|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Bir hatayı bildirmeyi kolaylaştıran bilgiler içeren bir dosya oluşturur.|
|[-kontrol edildi](checked-compiler-option.md)|Veri türünün sınırlarını taşan tamsayı aritmetiğinin çalışma zamanında özel bir özel durum olup olmadığını belirtir.|
|[-hata ayıklama](debug-compiler-option.md)|Derleyiciye hata ayıklama bilgilerini yayışmasını öğretin.|
|[-errorreport](errorreport-compiler-option.md)|Hata raporlama davranışını ayarlar.|
|[-fullpaths](fullpaths-compiler-option.md)|Derleyici çıktısında dosyaya giden mutlak yolu belirtir.|
|[-nowarn](nowarn-compiler-option.md)|Derleyicinin belirtilen uyarıları oluşturmasını bastırır.|
|[-warn](warn-compiler-option.md)|Uyarı düzeyini ayarlar.|
|[-warnaserror](warnaserror-compiler-option.md)|Uyarılara karşı uyarıları hatalara teşvik eder.|
|-ruleset:\<dosya>|Belirli tanılamadevre devre dışı bırakan bir kural kümesi dosyası belirtin.|

## <a name="preprocessor"></a>Ön işlemci

|Seçenek|Amaç|
|------------|-------------|
|[-define](define-compiler-option.md)|Önişlemci sembollerini tanımlar.|

## <a name="resources"></a>Kaynaklar

|Seçenek|Amaç|
|------------|-------------|
|[-bağlantı](link-compiler-option.md)|Belirtilen derlemelerde COM türü bilgilerini projenin kullanımına açık hale getirir.|
|[-linkresource](linkresource-compiler-option.md)|Yönetilen bir kaynağa bağlantı oluşturur.|
|[-kaynak](resource-compiler-option.md)|Bir .NET Framework kaynağını çıktı dosyasına yerle bir eder.|
|[-win32icon](win32icon-compiler-option.md)|Çıktı dosyasına eklemek için bir .ico dosyası belirtir.|
|[-win32res](win32res-compiler-option.md)|Çıktı dosyasına eklemek için win32 kaynağı belirtir.|

## <a name="miscellaneous"></a>Çeşitli

|Seçenek|Amaç|
|------------|-------------|
|[@](response-file-compiler-option.md)|Yanıt dosyalarını belirtir.|
|[-?](help-compiler-option.md)|Stdout için derleyici seçeneklerini listeler.|
|[-baseaddress](baseaddress-compiler-option.md)|DLL yüklemek için tercih edilen temel adresi belirtir.|
|[-codepage](codepage-compiler-option.md)|Derlemedeki tüm kaynak kod dosyaları için kullanılacak kod sayfasını belirtir.|
|[-yardım](help-compiler-option.md)|Stdout için derleyici seçeneklerini listeler.|
|[-highentropyva](highentropyva-compiler-option.md)|Yürütülebilir dosyaadres alanı düzeni rasgeleleştirme (ASLR) destekler belirtir.|
|[-langversion](langversion-compiler-option.md)|Dil sürümünü belirtin: Varsayılan, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 veya En Son |
|[-main](main-compiler-option.md)|**Ana** yöntemin konumunu belirtir.|
|[-noconfig](noconfig-compiler-option.md)|Derleyiciye csc.rsp ile derlememesi için talimat verir.|
|[-nologo](nologo-compiler-option.md)|Derleyici banner bilgilerini bastırır.|
|[-recurse](recurse-compiler-option.md)|Derlemek için kaynak dosyaları için alt dizinleri arar.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Çalıştırılabilir dosyanın kullanabileceği alt sistemin minimum sürümünü belirtir.|
|[-unsafe](unsafe-compiler-option.md)|[Güvenli olmayan](../keywords/unsafe.md) anahtar sözcüğü kullanan kodun derlenmesine olanak tanır.|
|[-utf8output](utf8output-compiler-option.md)|UTF-8 kodlamasını kullanarak derleyici çıktısını görüntüler.|
|-paralel[+&#124;-]|Eşzamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|
|-checksumalgorithm:\<alg>|PDB'de depolanan kaynak dosya checksum'u hesaplamak için algoritmayı belirtin.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256.<br>SHA1 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.|

## <a name="obsolete-options"></a>Eski Seçenekler

|Seçenek|Amaç|
|---|---|
|-artımlı|Artımlı derleme sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](listed-alphabetically.md)
- [Visual Studio Komut Satırı için ortam değişkenlerini ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md)

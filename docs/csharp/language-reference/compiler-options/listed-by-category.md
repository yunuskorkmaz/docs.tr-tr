---
title: Kategorilere Göre Listelenen C# Derleyici Seçenekleri
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 5cd5607c25dabd8f56ebb58366116666e8e649ea
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972713"
---
# <a name="c-compiler-options-listed-by-category"></a>Kategorilere Göre Listelenen C# Derleyici Seçenekleri

Aşağıdaki derleyici seçenekleri kategoriye göre sıralanır. Alfabetik bir liste için bkz [ C# . alfabetik olarak listelenen derleyici seçenekleri](listed-alphabetically.md).

## <a name="optimization"></a>İyileştirme

|Seçenek|Amaç|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Çıkış dosyasındaki bölümlerin boyutunu belirtir.|
|[-optimize](optimize-compiler-option.md)|İyileştirmeleri etkinleştirilir/devre dışı bırakır.|

## <a name="output-files"></a>Çıkış dosyaları

|Seçenek|Amaç|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Girişlerin özdeş olması halinde, derleyicinin ikili içerik özdeş olan bir derlemeyi çıkış yapmasına neden olur.|
|[-doc](doc-compiler-option.md)|İşlenen belge yorumlarının yazılacağı bir XML dosyası belirtir.|
|[-out](out-compiler-option.md)|Çıkış dosyasını belirtir.|
|[-pathmap](pathmap-compiler-option.md)|Derleyici tarafından çıkış kaynak yolu adları için bir eşleme belirtin|
|[-pdb](pdb-compiler-option.md)|Dosya adını ve. pdb dosyasının konumunu belirtir.|
|[-platform](platform-compiler-option.md)|Çıkış platformunu belirtin.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Derleyici çıkışı için bir dil belirtin.|
|[-refout](refout-compiler-option.md)|Birincil derlemeye ek olarak bir başvuru bütünleştirilmiş kodu oluşturun.|
|[-refonly](refonly-compiler-option.md)|Birincil derleme yerine bir başvuru bütünleştirilmiş kodu oluşturun.|
|[-target](target-compiler-option.md)|Şu beş seçenekten birini kullanarak çıkış dosyasının biçimini belirtir: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: Library](target-library-compiler-option.md), [-target: Module](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md)veya [-target: winmdobj](target-winmdobj-compiler-option.md).|
|-ModuleName:\<String >|Kaynak modülünün adını belirtin|

## <a name="net-framework-assemblies"></a>.NET Framework derlemeleri

|Seçenek|Amaç|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Bu derlemenin parçası olacak bir veya daha fazla modül belirtir.|
|[-delaysign](delaysign-compiler-option.md)|Derleyiciye ortak anahtar eklemesini, ancak derlemeyi işaretsiz olarak bırakmasını söyler.|
|[-keycontainer](keycontainer-compiler-option.md)|Şifreleme anahtarı kapsayıcısının adını belirtir.|
|[-keyfile](keyfile-compiler-option.md)|Şifreleme anahtarını içeren dosya adını belirtir.|
|[-lib](lib-compiler-option.md)|[Başvuru](reference-compiler-option.md)aracılığıyla başvurulan derlemelerin konumunu belirtir.|
|[-nostdlib](nostdlib-compiler-option.md)|Derleyiciye standart kitaplığı (mscorlib. dll) içeri aktarmamasını söyler.|
|[-publicsign](publicsign-compiler-option.md)|Derlemeyi imzalamadan ortak anahtar uygulayın, ancak derlemenin imzalandığını belirten derlemede bit ayarlayın.|
|[-reference](reference-compiler-option.md)|Derleme içeren bir dosyadan meta verileri içeri aktarır.|
|-çözümleyici|Bu derlemeden çözümleyiciler çalıştırın (kısa biçim:/a)|
|-additionalfile|Kod oluşturmayı doğrudan etkilemeyen, ancak hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilen ek dosyaları adlandırır.|
|-katıştır|Tüm kaynak dosyalarını PDB 'ye ekleyin.|
|-Embed:\<dosya listesi >|PDB 'ye belirli dosyaları ekleyin.|
## <a name="debuggingerror-checking"></a>Hata ayıklama/hata denetimi

|Seçenek|Amaç|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Bir hatayı rapor etmelerini kolaylaştıran bilgiler içeren bir dosya oluşturur.|
|[-checked](checked-compiler-option.md)|Veri türü sınırlarının dışına taşan tamsayı aritmetiğinin çalışma zamanında bir özel duruma neden olup olmayacağını belirtir.|
|[-debug](debug-compiler-option.md)|Derleyiciye hata ayıklama bilgilerini yaymasını bildirin.|
|[-errorreport](errorreport-compiler-option.md)|Hata raporlama davranışını ayarlar.|
|[-fullpaths](fullpaths-compiler-option.md)|Derleyici çıkışında dosyanın mutlak yolunu belirtir.|
|[-nowarn](nowarn-compiler-option.md)|Derleyicinin belirtilen uyarıların oluşturulmasını engeller.|
|[-warn](warn-compiler-option.md)|Uyarı düzeyini ayarlar.|
|[-warnaserror](warnaserror-compiler-option.md)|Hatalara yönelik uyarıları yükseltir.|
|-RuleSet:\<Dosya >|Belirli tanılamayı devre dışı bırakan bir RuleSet dosyası belirtin.|

## <a name="preprocessor"></a>Ön işlemci

|Seçenek|Amaç|
|------------|-------------|
|[-define](define-compiler-option.md)|Önişlemci sembolleri tanımlar.|

## <a name="resources"></a>Kaynaklar

|Seçenek|Amaç|
|------------|-------------|
|[-link](link-compiler-option.md)|Belirtilen derlemelerdeki COM türü bilgilerini proje için kullanılabilir hale getirir.|
|[-linkresource](linkresource-compiler-option.md)|Yönetilen bir kaynağa bir bağlantı oluşturur.|
|[-resource](resource-compiler-option.md)|Bir .NET Framework kaynağını çıkış dosyasına katıştırır.|
|[-win32icon](win32icon-compiler-option.md)|Çıktı dosyasına eklenecek bir. ico dosyasını belirtir.|
|[-win32res](win32res-compiler-option.md)|Çıktı dosyasına eklenecek bir Win32 kaynağı belirtir.|

## <a name="miscellaneous"></a>Çeşitli

|Seçenek|Amaç|
|------------|-------------|
|[@](response-file-compiler-option.md)|Bir yanıt dosyası belirtir.|
|[-?](help-compiler-option.md)|Stdout için derleyici seçeneklerini listeler.|
|[-baseaddress](baseaddress-compiler-option.md)|DLL 'nin yükleneceği tercih edilen temel adresi belirtir.|
|[-codepage](codepage-compiler-option.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.|
|[-yardım](help-compiler-option.md)|Stdout için derleyici seçeneklerini listeler.|
|[-highentropyva](highentropyva-compiler-option.md)|Yürütülebilir dosyanın adres alanı düzeni rastgele seçme (ASLR) öğesini desteklediğini belirtir.|
|[-langversion](langversion-compiler-option.md)|Dil sürümünü belirtin: varsayılan, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7,1, 7,2, 7,3 veya en son |
|[-main](main-compiler-option.md)|**Main** yönteminin konumunu belirtir.|
|[-noconfig](noconfig-compiler-option.md)|Derleyicinin Csc. rsp ile derlenmeyeceğini söyler.|
|[-nologo](nologo-compiler-option.md)|Derleyici başlık bilgilerini gizler.|
|[-recurse](recurse-compiler-option.md)|Kaynak dosyaları derlemek için alt dizinleri arar.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir.|
|[-unsafe](unsafe-compiler-option.md)|[Unsafe](../keywords/unsafe.md) anahtar sözcüğünü kullanan kodun derlemesini sunar.|
|[-utf8output](utf8output-compiler-option.md)|UTF-8 kodlamasını kullanarak derleyici çıkışını görüntüler.|
|-Parallel [+&#124;-]|Eşzamanlı yapı (+) kullanılıp kullanılmayacağını belirtir.|
|-checksumalgorithm:\<alg >|PDB 'de depolanan kaynak dosyası sağlama toplamını hesaplamak için algoritmayı belirtin.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|

## <a name="obsolete-options"></a>Eski seçenekler

|Seçenek|Amaç|
|---|---|
|-artımlı|Artımlı derlemeyi etkinleştirilir.|

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](listed-alphabetically.md)
- [Visual Studio komut satırı için ortam değişkenlerini ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md)

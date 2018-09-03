---
title: Kategorilere Göre Listelenen C# Derleyici Seçenekleri
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 891e5eac249f4bd22b6eadde7509de2d07cd1576
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479844"
---
# <a name="c-compiler-options-listed-by-category"></a>Kategorilere Göre Listelenen C# Derleyici Seçenekleri

Aşağıdaki derleyici seçeneklerinin kategoriye göre sıralanır. Alfabetik liste için bkz: [C# derleyici seçenekleri listelenen alfabetik](listed-alphabetically.md).

## <a name="optimization"></a>En iyi duruma getirme

|Seçenek|Amaç|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Bölüm boyutu, çıkış dosyasında belirtir.|
|[-optimize](optimize-compiler-option.md)|İyileştirmeleri etkinleştirir/devre dışı bırakır.|

## <a name="output-files"></a>Çıktı dosyaları

|Seçenek|Amaç|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|İkili içeriği girişleri özdeş ise derlemeler arasında aynıdır derleme çıktısını almak derleyicinin neden olur.|
|[-doc](doc-compiler-option.md)|İşlenen belge açıklamaları için yazılmış olduğu bir XML dosyasını belirtir.|
|[-out](out-compiler-option.md)|Çıkış dosyasını belirtir.|
|[-pathmap](pathmap-compiler-option.md)|Kaynak yol adları çıkış için bir eşleme derleyici tarafından belirtin|
|[-pdb](pdb-compiler-option.md)|.Pdb dosyasının konumunu ve dosya adını belirtir.|
|[-platform](platform-compiler-option.md)|Çıktı platformunu belirtin.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Derleyici çıkışı için bir dil belirtin.|
|[-refout](refout-compiler-option.md)|Birincil derlemesi ek olarak bir başvuru bütünleştirilmiş kodu oluşturur.|
|[-refonly](refonly-compiler-option.md)|Birincil bir derleme yerine bir başvuru bütünleştirilmiş kodu oluşturur.|
|[-target](target-compiler-option.md)|Beş seçeneklerinden birini kullanarak çıkış dosyasının biçimini belirtir: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [-target: module ](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), veya [-target: winmdobj](target-winmdobj-compiler-option.md).|
|-modulename:\<dize >|Kaynak modülünün adını belirtin|

## <a name="net-framework-assemblies"></a>.NET framework derlemeleri

|Seçenek|Amaç|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Bu derlemenin bir parçası olarak bir veya daha fazla modül belirtir.|
|[-delaysign](delaysign-compiler-option.md)|Derleyici ortak anahtarı ekleyin ancak derlemeyi imzasız bırakmayı bildirir.|
|[-keycontainer](keycontainer-compiler-option.md)|Şifreleme anahtar kapsayıcısı adını belirtir.|
|[-keyfile](keyfile-compiler-option.md)|Şifreleme anahtarını içeren dosya adını belirtir.|
|[-lib](lib-compiler-option.md)|Tarafından başvurulan derlemelerin konumunu belirten [-başvuru](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Standart kitaplığa (mscorlib.dll) içe derleyicinin sağlar.|
|[-publicsign](publicsign-compiler-option.md)|Bir ortak anahtar derleme imzalamadan geçerlidir ancak derleme imzalanması belirten derlemede biti ayarlanmış.|
|[-reference](reference-compiler-option.md)|Bir derlemeyi içeren bir dosyanın meta verilerini alır.|
|-Çözümleyicisi|Bu derleme Çözümleyicileri çalıştırın (kısa form: / a)|
|-additionalfile|Doğrudan kod üretimini etkilemez, ancak bir hata veya uyarı üretmek için çözümleyiciler tarafından kullanılabilir ek dosya adları.|

## <a name="debuggingerror-checking"></a>Hata ayıklama/hata denetimi

|Seçenek|Amaç|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Bir hatayı raporlamak kolaylaştıran bilgilerini içeren bir dosya oluşturur.|
|[-checked](checked-compiler-option.md)|Tamsayı veri türü sınırları taşıyor, aritmetik çalışma zamanında bir özel durum neden olup olmayacağını belirtir.|
|[-debug](debug-compiler-option.md)|Hata ayıklama bilgileri yayılamıyor derleyicisinin.|
|[-errorreport](errorreport-compiler-option.md)|Hata Raporlama davranışını ayarlar.|
|[-fullpaths](fullpaths-compiler-option.md)|Derleyici çıktısında mutlak dosya yolunu belirtir.|
|[-nowarn](nowarn-compiler-option.md)|Belirtilen Uyarıları derleyicinin oluşturulmasını bastırır.|
|[-warn](warn-compiler-option.md)|Uyarı düzeyini ayarlar.|
|[-warnaserror](warnaserror-compiler-option.md)|Hatalar için uyarıları yükseltir.|
|-Kural kümesi:\<dosyası >|Belirli tanılama devre dışı bırakan bir kural kümesi dosyası belirtin.|

## <a name="preprocessor"></a>Ön işlemci

|Seçenek|Amaç|
|------------|-------------|
|[-define](define-compiler-option.md)|Önişlemci sembolleri tanımlar.|

## <a name="resources"></a>Kaynaklar

|Seçenek|Amaç|
|------------|-------------|
|[-link](link-compiler-option.md)|COM tür bilgilerini belirtilen derlemeleri projeye kullanılabilir hale getirir.|
|[-linkresource](linkresource-compiler-option.md)|Yönetilen kaynağa bağlantı oluşturur.|
|[-resource](resource-compiler-option.md)|.NET Framework kaynak çıkış dosyasına katıştırır.|
|[-win32icon](win32icon-compiler-option.md)|Çıkış dosyasına eklemek için bir .ico dosyasını belirtir.|
|[-win32res](win32res-compiler-option.md)|Çıkış dosyasına eklemek için bir Win32 kaynağı belirtir.|

## <a name="miscellaneous"></a>Çeşitli

|Seçenek|Amaç|
|------------|-------------|
|[@](response-file-compiler-option.md)|Bir yanıt dosyası belirtir.|
|[-?](help-compiler-option.md)|Stdout derleyici seçenekleri listeler.|
|[-baseaddress](baseaddress-compiler-option.md)|Bir DLL yüklemek için tercih edilen temel adresini belirtir.|
|[-codepage](codepage-compiler-option.md)|Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.|
|[-Yardım](help-compiler-option.md)|Stdout derleyici seçenekleri listeler.|
|[-highentropyva](highentropyva-compiler-option.md)|Yürütülebilir dosyayı rastgele adres alanı düzenini (ASLR) desteklediğini belirtir.|
|[-langversion](langversion-compiler-option.md)|Dil sürümünü belirtin: varsayılan, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 veya en son |
|[-main](main-compiler-option.md)|Konumunu belirtir **ana** yöntemi.|
|[-noconfig](noconfig-compiler-option.md)|Csc.rsp ile derleme değil derleyicinin sağlar.|
|[-nologo](nologo-compiler-option.md)|Derleyici başlık bilgilerini engellemesidir.|
|[-recurse](recurse-compiler-option.md)|Derlenecek kaynak dosyaların için alt arar.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Yürütülebilir dosyanın kullanabileceği alt sistemin en düşük sürümünü belirtir.|
|[-unsafe](unsafe-compiler-option.md)|Kullanan kod derlemesini etkinleştirir [güvenli](../../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü.|
|[-utf8output](utf8output-compiler-option.md)|UTF-8 kodlaması kullanarak derleyici çıkışı görüntüler.|
|-Paralel [+&#124;-]|Eş zamanlı derleme (+) kullanılıp kullanılmayacağını belirtir.|
|-checksumalgorithm:\<algoritma >|PDB içinde depolanan kaynak dosya sağlama toplamı hesaplama algoritması belirtin.  Desteklenen değerler şunlardır: SHA1 (varsayılan) veya SHA256.|

## <a name="obsolete-options"></a>Geçersiz Seçenekler

|Seçenek|Amaç|
|---|---|
|-artan|Artımlı derleme sağlar.|

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Derleyici Seçenekleri](index.md)  
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](listed-alphabetically.md)  
- [Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md)

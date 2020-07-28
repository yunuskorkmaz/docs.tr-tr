---
title: Ildasm.exe (IL Ayrıştırıcı)
description: Ara dil (IL) kodu içeren taşınabilir bir çalıştırılabilir (PE) dosyayı alan ve Ilasm.exe için bir metin dosyası oluşturan Ildasm.exe (IL Disassembler) kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
ms.openlocfilehash: 6f2611488e7f653783cab833ad47131978bf74aa
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166842"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Ayrıştırıcı)

Il ayırıcı, Il derleyicisi için yardımcı bir araçtır (*Ilasm.exe*). *Ildasm.exe* , ara DIL (IL) kodu içeren bir taşınabilir ÇALıŞTıRıLABILIR (PE) dosyası alır ve *Ilasm.exe*giriş olarak uygun bir metin dosyası oluşturur.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Söz dizimi

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametreler

*. Exe*, *. dll*, *. obj*, *. lib*ve *. winmd* dosyaları için aşağıdaki seçenekler kullanılabilir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/Out =**`filename`|`filename`Sonuçları grafik kullanıcı arabiriminde görüntülemek yerine, belirtilen bir çıkış dosyası oluşturur.|
|**/RTF**|Zengin metin biçiminde çıktılar üretir. **/Text** seçeneğiyle geçersiz.|
|**/Text**|Sonuçları grafik kullanıcı arabiriminde veya çıktı dosyası olarak değil, konsol penceresinde görüntüler.|
|**/HTML**|HTML biçiminde çıktı üretir. Yalnızca **/output** seçeneği ile geçerlidir.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

*. Exe*, *. dll*ve *. winmd* dosyaları için aşağıdaki ek seçenekler kullanılabilir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/bytes**|Gerçek bayt miktarını yönerge yorumları olarak onaltılık biçimde gösterir.|
|**/caverbal**|Sözlü biçimde özel öznitelik blob'ları üretir. Varsayılan ikili biçimdir.|
|**/linenum**|Özgün kaynak satırları için başvurular içerir.|
|**/Nobar**|Parçalara ayırma işleminin ilerleme durumu açılır penceresini gizler.|
|**/Noca**|Özel özniteliklerin çıkışını gizler.|
|**/Project**|Meta verileri, yerel Windows Çalışma Zamanı görünme şekli yerine, yönetilen koda göründüğü şekilde görüntüler. `PEfilename`Bir Windows meta veri (*. winmd*) dosyası değilse, bu seçeneğin hiçbir etkisi yoktur. Bkz. [Windows Mağazası uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**yalnızca/pub**|Yalnızca genel türleri ve üyeleri ayrıştırır. **/Visibility: pub**ile eşdeğerdir.|
|**/quoteallnames**|Tüm adları tek tırnak işaretleri içine alır.|
|**/raweh**|Özel durum işleme yan tümcelerini ham biçimde gösterir.|
|**/Source**|Özgün kaynak satırları açıklamalar olarak gösterir.|
|**/Tokens**|Sınıfların ve üyelerin meta veri belirteçlerini gösterir.|
|**/visibility:** `vis` [+`vis`...]|Yalnızca belirtilen görünürlüğe sahip türleri veya üyeleri ayrıştırır. Şunlar için geçerli değerler şunlardır `vis` :<br /><br /> **Yayın** — genel<br /><br /> **PRI** — özel<br /><br /> **FAM** — aile<br /><br /> **Asm** — derleme<br /><br /> **FAA** — aile ve derleme<br /><br /> **FOA** — aile veya derleme<br /><br /> **PSC** — özel kapsam<br /><br /> Bu görünürlük değiştiricilerin tanımları için bkz <xref:System.Reflection.MethodAttributes> . ve <xref:System.Reflection.TypeAttributes> .|

Yalnızca dosya veya konsol çıktısı için *. exe*, *. dll*ve *. winmd* dosyaları için aşağıdaki seçenekler geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/All**|**/Header**, **/bytes**, **/stats**, **/classlist**ve **/Tokens** seçeneklerinin bir birleşimini belirtir.|
|**/classlist**|Modülde tanımlanmış sınıfların bir listesini içerir.|
|**/ilet**|İleriye dönük sınıf bildirimini kullanır.|
|**/Headers**|Çıktıya dosyanın başlık bilgilerini ekler.|
|**/item:** `class` [**::** `member` [`(sig`]]|Sağlanan bağımsız değişkene bağlı olarak aşağıdakileri ayrıştırır:<br /><br /> -Belirtilen olarak ayrıştırır `class` .<br />-Belirtilen ' i ayrıştırır `member` `class` .<br />- `member` Belirtilen imzayla öğesinin öğesini ayrıştırır `class` `sig` . Biçimi `sig` :<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Göz önünde** 1,0 ve 1,1 .NET Framework sürümlerinde, `sig` arkasından bir kapanış ayracı gelmelidir: `(sig)` . NET Framework 2,0 ile başlayarak kapatma parantezi atlanmalıdır: `(sig` .|
|**/NOIL**|IL derlemesi kod çıktısını engeller.|
|**/stats**|Görüntüye istatistikleri ekler.|
|**/Typelist**|Gidiş dönüş içinde tür sıralamasını korumak üzere türlerin tam listesini oluşturur.|
|**/Unicode**|Çıktı için Unicode kodlaması kullanır.|
|**/UTF8**|Çıktı için UTF-8 kodlaması kullanır. ANSI varsayılandır.|

Aşağıdaki seçenekler yalnızca dosya ya da konsol çıktısı için *. exe*, *. dll*, *. obj*, *. lib*ve *. winmd* dosyaları için geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/metadata**[= `specifier` ]|Meta verileri gösterir; burada `specifier` :<br /><br /> **MDHEADER** — meta veri üst bilgisi bilgilerini ve boyutlarını gösterir.<br /><br /> **Onaltılık** — bilgileri, onaltılı ve kelimeyle birlikte gösterir.<br /><br /> **CSV** — kayıt sayılarını ve yığın boyutlarını gösterir.<br /><br /> **UNREX** — çözümlenmemiş dışlar göster.<br /><br /> **Şema** — meta veri üst bilgisini ve şema bilgilerini gösterir.<br /><br /> **RAW** — Ham meta veri tablolarını gösterir.<br /><br /> **Heap** 'ler: ham yığınlarını gösterir.<br /><br /> **Doğrula** — meta verilerin tutarlılığını doğrulayın.<br /><br /> **/Metadata** öğesini farklı değerlerle birden çok kez belirtebilirsiniz `specifier` .|

Aşağıdaki seçenekler yalnızca dosya ya da konsol çıktısı için *. lib* dosyaları için geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/objectfile**=`filename`|Belirtilen kitaplıkta tek bir nesne dosyasının meta verilerini gösterir.|

> [!NOTE]
> Tüm *Ildasm.exe* seçenekleri büyük/küçük harfe duyarlıdır ve ilk üç harf tarafından tanınır. Örneğin, **/Quo** , **/quoteallnames**ile eşdeğerdir. Bağımsız değişkenler belirten seçenekler, seçenek ve bağımsız değişken arasında ayıraç olarak ya iki nokta üst üste (:) ya da eşittir işaretini (=) kabul eder. Örneğin, **/output:** *filename* , **/output =** *filename*ile eşdeğerdir.

## <a name="remarks"></a>Açıklamalar

*Ildasm.exe* yalnızca diskteki PE dosyaları üzerinde çalışır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

*Ildasm.exe* tarafından üretilen metin dosyası, Il Assembler (*Ilasm.exe*) girişi olarak kullanılabilir. Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kodu derleyip ve çıkışını *Ildasm.exe*aracılığıyla çalıştırdıktan sonra, elde edilen Il metin dosyası, eksik öznitelikleri eklemek için el ile düzenlenebilir. Ardından bu metin dosyasını IL Derleyicisi aracılığıyla çalıştırarak son bir çalıştırılabilir dosya oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.  

Meta veriyi ve varolan herhangi bir PE dosyasının ayrıştırılmış kodunu hiyerarşik bir ağaç görünümünde görüntülemek için varsayılan GUI'yi IL Ayrıştırıcısı'nda kullanabilirsiniz. GUI 'yi kullanmak için, *PEfilename* bağımsız değişkenini veya herhangi bir seçeneği sağlamadan, komut satırına **ıldadsm** yazın. **Dosya** menüsünde, *Ildasm.exe*yüklemek istediğiniz pe dosyasına gidebilirsiniz. Seçili PE için görüntülenecek meta verileri ve ayrıştırılmış kodu kaydetmek için, **Dosya** menüsünden **döküm** komutunu seçin. Yalnızca hiyerarşik ağaç görünümünü kaydetmek için **Dosya** menüsünden TreeView 'Yi **dökümünü al** komutunu seçin. *Ildasm.exe* bir dosya yükleme ve çıktıyı yorumlama hakkında ayrıntılı kılavuz için, Windows SDK birlikte gelen örnekler klasöründe bulunan *Ildasm.exe* öğreticisine bakın.

Katıştırılmış kaynakları içeren bir *PEfilename* bağımsız değişkeni ile *Ildasm.exe* sağlarsanız, araç birden çok ÇıKTı dosyası üretir: IL kodu içeren bir metin dosyası ve her katıştırılmış yönetilen kaynak için, kaynağın meta verilerden adı kullanılarak üretilen. resources dosyası. Yönetilmeyen bir kaynak *PEfilename*içine katıştırılırsa, **/output** seçeneği tarafından Il çıktısı için belirtilen dosya adı kullanılarak bir. res dosyası oluşturulur.

> [!NOTE]
> *Ildasm.exe* , *. obj* ve *. lib* giriş dosyaları için yalnızca meta veri açıklamalarını gösterir. Bu dosya türleri için IL kodu ayrıştırılmaz.

Dosyanın yönetilip yönetilmediğini anlamak için, an.exe veya *. dll* dosyası üzerinden *Ildasm.exe* çalıştırabilirsiniz. Dosya yönetilmiyorsa; araç, dosyada geçerli hiçbir ortak dil çalışma zamanı başlığı olmadığını ve ayrıştırılamayacağını belirten bir ileti görüntüler. Dosya yönetiliyorsa, araç başarıyla çalışır.

## <a name="version-information"></a>Sürüm Bilgileri

.NET Framework 4,5 ' den başlayarak, ham ikili içeriği görüntüleyerek *Ildasm.exe* tanınmayan BIR sıralama Blobu (ikili büyük nesne) işler. Örneğin aşağıdaki kod, bir C# programı tarafından oluşturulmuş sıralama BLOB'unun nasıl görüntülendiğini gösterir:

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

.NET Framework 4,5 ' den başlayarak *Ildasm.exe* , *Ildasm.exe* çıktısından alınan aşağıdaki alıntıda gösterildiği gibi, arabirim uygulamalarına uygulanan öznitelikleri görüntüler:

```il
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

## <a name="examples"></a>Örnekler

Aşağıdaki komut, PE dosyası için meta verilerin ve ayrıştırılmış kodun `MyHello.exe` varsayılan guı *Ildasm.exe* görüntülenmesine neden olur.

```console
ildasm myHello.exe
```

Aşağıdaki komut dosyayı ayrıştırır `MyFile.exe` ve sonuçta elde EDILEN Il assembler metnini *MyFile.il*dosyasına depolar.

```console
ildasm MyFile.exe /output:MyFile.il
```

Aşağıdaki komut dosyayı ayrıştırır `MyFile.exe` ve sonuçta elde EDILEN Il assembler metnini konsol penceresine görüntüler.

```console
ildasm MyFile.exe /text
```

Dosya `MyApp.exe` gömülü yönetilen ve yönetilmeyen kaynaklar içeriyorsa, aşağıdaki komut dört dosya üretir: *MyApp.il*, *MyApp. res*, *simgeler. resources*ve *Message. resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Aşağıdaki komut `MyMethod` içindeki sınıfındaki Yöntemi ayrıştırır `MyClass` `MyFile.exe` ve çıktıyı konsol penceresinde görüntüler.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

Önceki örnekte, farklı imzalarla adlandırılan birkaç yöntem olabilir `MyMethod` . Aşağıdaki komut, `MyMethod` **void** dönüş türü ve **Int32** ve **String**parametre türleri ile örnek yöntemi ayrıştırır.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> 1,0 ve 1,1 .NET Framework sürümlerinde, yöntem adını izleyen sol parantez, imzadan sonra sağ parantez ile dengelenmelidir: `MyMethod(instance void(int32))` . .NET Framework 2,0 ile başlayarak kapatma parantezi atlanmalıdır: `MyMethod(instance void(int32)` .

Bir yöntemi almak için `static` ( `Shared` Visual Basic yöntemi), anahtar sözcüğünü atlayın `instance` . Gibi basit türler olmayan `int32` ve `string` ad alanını içermesi gereken sınıf türleri ve önünde anahtar sözcüğü gelmelidir `class` . Dış türlerin başına köşeli ayraçlar içinde kitaplık adı gelmelidir. Aşağıdaki komut, `MyMethod` türünde bir parametreye sahip <xref:System.AppDomain> ve dönüş türü olan adlı statik bir yöntemi ayrıştırır <xref:System.AppDomain> .

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

İç içe geçmiş bir türün başında, eğik çizgi ile sınırlandırılmış kapsayan sınıfı bulunmalıdır. Örneğin, `MyNamespace.MyClass` sınıfı adlı bir iç içe sınıf içeriyorsa `NestedClass` , iç içe yerleştirilmiş sınıf şu şekilde tanımlanır: `class MyNamespace.MyClass/NestedClass` .

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Ilasm.exe (Il Assembler)](ilasm-exe-il-assembler.md)
- [Yönetilen yürütme Işlemi](../../standard/managed-execution-process.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)

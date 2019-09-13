---
title: Ildasm.exe (IL Ayrıştırıcı)
ms.date: 03/30/2017
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9e6d9e57528f3eae9b30706013a0529313877c7
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894873"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Ayrıştırıcı)

Il ayırıcı, Il derleyiciciye (*Ilasm. exe*) yardımcı olan bir araçtır. *Ildadsm. exe* , ara DIL (IL) kodu içeren bir taşınabilir ÇALıŞTıRıLABILIR (PE) dosyası alır ve *Ilasm. exe*' ye giriş olarak uygun bir metin dosyası oluşturur.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametreler

*. Exe*, *. dll*, *. obj*, *. lib*ve *. winmd* dosyaları için aşağıdaki seçenekler kullanılabilir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/Out =** `filename`|Sonuçları grafik kullanıcı arabiriminde görüntülemek yerine, `filename`belirtilen bir çıkış dosyası oluşturur.|
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
|**/Project**|Meta verileri, yerel Windows Çalışma Zamanı görünme şekli yerine, yönetilen koda göründüğü şekilde görüntüler. Bir Windows meta veri ( *. winmd*) dosyası değilse, bu seçeneğin hiçbir etkisi yoktur. `PEfilename` Bkz. [Windows Mağazası uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**yalnızca/pub**|Yalnızca genel türleri ve üyeleri ayrıştırır. **/Visibility: pub**ile eşdeğerdir.|
|**/quoteallnames**|Tüm adları tek tırnak işaretleri içine alır.|
|**/raweh**|Özel durum işleme yan tümcelerini ham biçimde gösterir.|
|**/Source**|Özgün kaynak satırları açıklamalar olarak gösterir.|
|**/Tokens**|Sınıfların ve üyelerin meta veri belirteçlerini gösterir.|
|**/visibility:** `vis`[+`vis`...]|Yalnızca belirtilen görünürlüğe sahip türleri veya üyeleri ayrıştırır. Şunlar için `vis`geçerli değerler şunlardır:<br /><br /> **Yayın** — genel<br /><br /> **PRI** — özel<br /><br /> **FAM** — aile<br /><br /> **Asm** — derleme<br /><br /> **FAA** — aile ve derleme<br /><br /> **FOA** — aile veya derleme<br /><br /> **PSC** — özel kapsam<br /><br /> Bu görünürlük değiştiricilerin tanımları için bkz <xref:System.Reflection.MethodAttributes> . ve. <xref:System.Reflection.TypeAttributes>|

Yalnızca dosya veya konsol çıktısı için *. exe*, *. dll*ve *. winmd* dosyaları için aşağıdaki seçenekler geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/All**|**/Header**, **/bytes**, **/stats**, **/classlist**ve **/Tokens** seçeneklerinin bir birleşimini belirtir.|
|**/classlist**|Modülde tanımlanmış sınıfların bir listesini içerir.|
|**/ilet**|İleriye dönük sınıf bildirimini kullanır.|
|**/Headers**|Çıktıya dosyanın başlık bilgilerini ekler.|
|**/item:** `class`[ **::** `member`[`(sig`]]|Sağlanan bağımsız değişkene bağlı olarak aşağıdakileri ayrıştırır:<br /><br /> -Belirtilen `class`olarak ayrıştırır.<br />-Belirtilen `member` `class`' i ayrıştırır.<br />-Belirtilen imzayla `class` `member` öğesininöğesiniayrıştırır`sig`. Biçimi `sig` :<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Göz önünde** 1,0 ve 1,1 .NET Framework sürümlerinde, `sig` arkasından bir kapanış ayracı gelmelidir:. `(sig)` NET Framework 2,0 ile başlayarak kapatma parantezi atlanmalıdır: `(sig`.|
|**/NOIL**|IL derlemesi kod çıktısını engeller.|
|**/stats**|Görüntüye istatistikleri ekler.|
|**/Typelist**|Gidiş dönüş içinde tür sıralamasını korumak üzere türlerin tam listesini oluşturur.|
|**/Unicode**|Çıktı için Unicode kodlaması kullanır.|
|**/UTF8**|Çıktı için UTF-8 kodlaması kullanır. ANSI varsayılandır.|

Aşağıdaki seçenekler yalnızca dosya ya da konsol çıktısı için *. exe*, *. dll*, *. obj*, *. lib*ve *. winmd* dosyaları için geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/metadata** [=`specifier`]|Meta verileri gösterir; `specifier` burada:<br /><br /> **MDHEADER** — meta veri üst bilgisi bilgilerini ve boyutlarını gösterir.<br /><br /> **Onaltılık** — bilgileri, onaltılı ve kelimeyle birlikte gösterir.<br /><br /> **CSV** — kayıt sayılarını ve yığın boyutlarını gösterir.<br /><br /> **UNREX** — çözümlenmemiş dışlar göster.<br /><br /> **Şema** — meta veri üst bilgisini ve şema bilgilerini gösterir.<br /><br /> **RAW** — Ham meta veri tablolarını gösterir.<br /><br /> **Heap** 'ler: ham yığınlarını gösterir.<br /><br /> **Doğrula** — meta verilerin tutarlılığını doğrulayın.<br /><br /> **/Metadata** öğesini farklı değerlerle `specifier`birden çok kez belirtebilirsiniz.|

Aşağıdaki seçenekler yalnızca dosya ya da konsol çıktısı için *. lib* dosyaları için geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/objectfile**=`filename`|Belirtilen kitaplıkta tek bir nesne dosyasının meta verilerini gösterir.|

> [!NOTE]
> *Ildadsm. exe* ' nin tüm seçenekleri büyük/küçük harfe duyarlıdır ve ilk üç harf tarafından tanınır. Örneğin, **/Quo** , **/quoteallnames**ile eşdeğerdir. Bağımsız değişkenler belirten seçenekler, seçenek ve bağımsız değişken arasında ayıraç olarak ya iki nokta üst üste (:) ya da eşittir işaretini (=) kabul eder. Örneğin, **/output:** *filename* , **/output =** *filename*ile eşdeğerdir.

## <a name="remarks"></a>Açıklamalar

*Ildadsm. exe* yalnızca diskteki PE dosyaları üzerinde çalışır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

*Ildadsm. exe* tarafından üretilen metin dosyası, Il derleyicgunda (*Ilasm. exe*) giriş olarak kullanılabilir. Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kodu derleyip ve çıkışını *ıldadsm. exe*aracılığıyla çalıştırdıktan sonra, elde edilen Il metin dosyası, eksik öznitelikleri eklemek için el ile düzenlenebilir. Ardından bu metin dosyasını IL Derleyicisi aracılığıyla çalıştırarak son bir çalıştırılabilir dosya oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.  

Meta veriyi ve varolan herhangi bir PE dosyasının ayrıştırılmış kodunu hiyerarşik bir ağaç görünümünde görüntülemek için varsayılan GUI'yi IL Ayrıştırıcısı'nda kullanabilirsiniz. GUI 'yi kullanmak için, *PEfilename* bağımsız değişkenini veya herhangi bir seçeneği sağlamadan, komut satırına **ıldadsm** yazın. **Dosya** menüsünde, *ıldadsm. exe*' ye yüklemek istediğiniz pe dosyasına gidebilirsiniz. Seçili PE için görüntülenecek meta verileri ve ayrıştırılmış kodu kaydetmek için, **Dosya** menüsünden **döküm** komutunu seçin. Yalnızca hiyerarşik ağaç görünümünü kaydetmek için **Dosya** menüsünden TreeView 'Yi **dökümünü al** komutunu seçin. *Ildadsm. exe* ' ye bir dosya yükleme ve çıktıyı yorumlama hakkında ayrıntılı kılavuz için, Windows SDK birlikte gelen Samples klasöründe bulunan *ıldadsm. exe* öğreticisine bakın.

Gömülü kaynakları içeren bir *PEfilename* bağımsız değişkeni Ile *ıldadsm. exe* sağlarsanız, araç birden çok ÇıKTı dosyası üretir: IL kodu içeren bir metin dosyası ve her ekli yönetilen kaynak için, bir. resources dosyası kullanılarak oluşturulan meta verilerden kaynak adı. Yönetilmeyen bir kaynak *PEfilename*içine katıştırılırsa, **/output** seçeneği tarafından Il çıktısı için belirtilen dosya adı kullanılarak bir. res dosyası oluşturulur.

> [!NOTE]
> *Ildadsm. exe* , *. obj* ve *. lib* giriş dosyaları için yalnızca meta veri açıklamalarını gösterir. Bu dosya türleri için IL kodu ayrıştırılmaz.

Dosyanın yönetilip yönetilmediğini anlamak için, bir. exe veya *. dll* dosyası üzerinde *ıldadsm. exe* ' yi çalıştırabilirsiniz. Dosya yönetilmiyorsa; araç, dosyada geçerli hiçbir ortak dil çalışma zamanı başlığı olmadığını ve ayrıştırılamayacağını belirten bir ileti görüntüler. Dosya yönetiliyorsa, araç başarıyla çalışır.

## <a name="version-information"></a>Sürüm Bilgileri

4,5 .NET Framework başlayarak *ıldadsm. exe* , ham ikili içeriği görüntüleyerek tanınmayan BIR sıralama Blobu (ikili büyük nesne) işler. Örneğin aşağıdaki kod, bir C# programı tarafından oluşturulmuş sıralama BLOB'unun nasıl görüntülendiğini gösterir:

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

.NET Framework 4,5 ' den başlayarak *ıldadsm. exe* , aşağıdaki *ıldadsm. exe* çıktısında gösterildiği gibi, arabirim uygulamalarına uygulanan öznitelikleri görüntüler:

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

Aşağıdaki komut, PE dosyası `MyHello.exe` için meta verilerin ve ayrıştırılmış kodun *ıldadsm. exe* Varsayılan GUI 'de görüntülenmesine neden olur.

```console
ildasm myHello.exe
```

Aşağıdaki komut dosyayı `MyFile.exe` ayrıştırır ve sonuçta elde edilen Il assembler metnini *MyFile.il*dosyasına depolar.

```console
ildasm MyFile.exe /output:MyFile.il
```

Aşağıdaki komut dosyayı `MyFile.exe` ayrıştırır ve sonuçta elde edilen Il assembler metnini konsol penceresine görüntüler.

```console
ildasm MyFile.exe /text
```

Dosya `MyApp.exe` gömülü yönetilen ve yönetilmeyen kaynaklar içeriyorsa aşağıdaki komut dört dosya üretir: *MyApp.il*, *MyApp. res*, *simgeler. resources*ve *Message. resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Aşağıdaki komut içindeki `MyMethod` `MyClass` sınıfındaki`MyFile.exe` Yöntemi ayrıştırır ve çıktıyı konsol penceresinde görüntüler.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

Önceki örnekte, farklı imzalarla adlandırılan `MyMethod` birkaç yöntem olabilir. `MyMethod` Aşağıdaki komut, **void** dönüş türü ve **Int32** ve **String**parametre türleri ile örnek yöntemi ayrıştırır.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> 1,0 ve 1,1 .NET Framework sürümlerinde, yöntem adını izleyen sol parantez, imzadan sonra sağ parantez ile dengelenmelidir: `MyMethod(instance void(int32))`. .NET Framework 2,0 ile başlayarak kapatma parantezi atlanmalıdır: `MyMethod(instance void(int32)`.

Bir `static` yöntemi almak için (`Shared` Visual Basic yöntemi), anahtar sözcüğünü `instance`atlayın. Gibi `int32` basit türler olmayan ve `string` ad alanını içermesi gereken sınıf türleri ve önünde anahtar sözcüğü `class`gelmelidir. Dış türlerin başına köşeli ayraçlar içinde kitaplık adı gelmelidir. Aşağıdaki komut, türünde `MyMethod` <xref:System.AppDomain> bir parametreye sahip ve dönüş türü <xref:System.AppDomain>olan adlı statik bir yöntemi ayrıştırır.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

İç içe geçmiş bir türün başında, eğik çizgi ile sınırlandırılmış kapsayan sınıfı bulunmalıdır. Örneğin, `MyNamespace.MyClass` sınıfı adlı `NestedClass`bir iç içe sınıf içeriyorsa, iç içe yerleştirilmiş sınıf şu şekilde tanımlanır: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](../../../docs/framework/tools/index.md)
- [Ilasm.exe (IL Derleyici)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Yönetilen Yürütme İşlemi](../../standard/managed-execution-process.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

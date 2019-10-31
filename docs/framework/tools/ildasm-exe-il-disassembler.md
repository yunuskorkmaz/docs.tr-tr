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
ms.openlocfilehash: f23f8c48a31dffa7d350c872aed7505da7a36861
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105052"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Ayrıştırıcı)

Il ayırıcı, Il derleyiciciye (*Ilasm. exe*) yardımcı olan bir araçtır. *Ildadsm. exe* , ara DIL (IL) kodu içeren bir taşınabilir ÇALıŞTıRıLABILIR (PE) dosyası alır ve *Ilasm. exe*' ye giriş olarak uygun bir metin dosyası oluşturur.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametreler

*. Exe*, *. dll*, *. obj*, *. lib*ve *. winmd* dosyaları için aşağıdaki seçenekler kullanılabilir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/Out =** `filename`|Sonuçları grafik kullanıcı arabiriminde görüntülemek yerine, belirtilen `filename`bir çıktı dosyası oluşturur.|
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
|**/Project**|Meta verileri, yerel Windows Çalışma Zamanı görünme şekli yerine, yönetilen koda göründüğü şekilde görüntüler. `PEfilename` bir Windows meta veri ( *. winmd*) dosyası değilse, bu seçeneğin hiçbir etkisi yoktur. Bkz. [Windows Mağazası uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**yalnızca/pub**|Yalnızca genel türleri ve üyeleri ayrıştırır. **/Visibility: pub**ile eşdeğerdir.|
|**/quoteallnames**|Tüm adları tek tırnak işaretleri içine alır.|
|**/raweh**|Özel durum işleme yan tümcelerini ham biçimde gösterir.|
|**/Source**|Özgün kaynak satırları açıklamalar olarak gösterir.|
|**/Tokens**|Sınıfların ve üyelerin meta veri belirteçlerini gösterir.|
|**/visibility:** `vis`[+`vis`...]|Yalnızca belirtilen görünürlüğe sahip türleri veya üyeleri ayrıştırır. `vis`için geçerli değerler aşağıda verilmiştir:<br /><br /> **Yayın** — genel<br /><br /> **PRI** — özel<br /><br /> **FAM** — aile<br /><br /> **Asm** — derleme<br /><br /> **FAA** — aile ve derleme<br /><br /> **FOA** — aile veya derleme<br /><br /> **PSC** — özel kapsam<br /><br /> Bu görünürlük değiştiricilerin tanımları için bkz. <xref:System.Reflection.MethodAttributes> ve <xref:System.Reflection.TypeAttributes>.|

Yalnızca dosya veya konsol çıktısı için *. exe*, *. dll*ve *. winmd* dosyaları için aşağıdaki seçenekler geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/All**|**/Header**, **/bytes**, **/stats**, **/classlist**ve **/Tokens** seçeneklerinin bir birleşimini belirtir.|
|**/classlist**|Modülde tanımlanmış sınıfların bir listesini içerir.|
|**/ilet**|İleriye dönük sınıf bildirimini kullanır.|
|**/Headers**|Çıktıya dosyanın başlık bilgilerini ekler.|
|**/Item:** `class`[ **::** `member`[`(sig`]]|Sağlanan bağımsız değişkene bağlı olarak aşağıdakileri ayrıştırır:<br /><br /> -Belirtilen `class`ayrıştırır.<br />-`class`belirtilen `member` ayrıştırır.<br />-Belirtilen imza `sig`ile `class` `member` ayrıştırır. `sig` biçimi:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`,..., `parameterTypeN`)<br />     **Göz önünde** 1,0 ve 1,1 .NET Framework sürümlerinde `sig` bir kapanış ayracı gelmelidir: `(sig)`. NET Framework 2,0 ile başlayarak kapatma parantezi atlanmalıdır: `(sig`.|
|**/NOIL**|IL derlemesi kod çıktısını engeller.|
|**/stats**|Görüntüye istatistikleri ekler.|
|**/Typelist**|Gidiş dönüş içinde tür sıralamasını korumak üzere türlerin tam listesini oluşturur.|
|**/Unicode**|Çıktı için Unicode kodlaması kullanır.|
|**/UTF8**|Çıktı için UTF-8 kodlaması kullanır. ANSI varsayılandır.|

Aşağıdaki seçenekler yalnızca dosya ya da konsol çıktısı için *. exe*, *. dll*, *. obj*, *. lib*ve *. winmd* dosyaları için geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/metadata**[=`specifier`]|Meta verileri gösterir; burada `specifier`:<br /><br /> **MDHEADER** — meta veri üst bilgisi bilgilerini ve boyutlarını gösterir.<br /><br /> **Onaltılık** — bilgileri, onaltılı ve kelimeyle birlikte gösterir.<br /><br /> **CSV** — kayıt sayılarını ve yığın boyutlarını gösterir.<br /><br /> **UNREX** — çözümlenmemiş dışlar göster.<br /><br /> **Şema** — meta veri üst bilgisini ve şema bilgilerini gösterir.<br /><br /> **RAW** — Ham meta veri tablolarını gösterir.<br /><br /> **Heap** 'ler: ham yığınlarını gösterir.<br /><br /> **Doğrula** — meta verilerin tutarlılığını doğrulayın.<br /><br /> `specifier`için farklı değerlerle **/metadata** birden çok kez belirtebilirsiniz.|

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

Aşağıdaki komut, PE dosya `MyHello.exe` için meta verilerin ve ayrıştırılmış kodun *ıldadsm. exe* Varsayılan GUI 'de görüntülenmesine neden olur.

```console
ildasm myHello.exe
```

Aşağıdaki komut `MyFile.exe` dosyayı ayrıştırır ve elde edilen Il assembler metnini *MyFile.il*dosyasına depolar.

```console
ildasm MyFile.exe /output:MyFile.il
```

Aşağıdaki komut `MyFile.exe` dosyayı ayrıştırır ve sonuçta elde edilen Il assembler metnini konsol penceresine görüntüler.

```console
ildasm MyFile.exe /text
```

Dosya `MyApp.exe` gömülü yönetilen ve yönetilmeyen kaynaklar içeriyorsa, aşağıdaki komut dört dosya üretir: *MyApp.il*, *MyApp. res*, *simgeler. resources*ve *Message. resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Aşağıdaki komut, `MyClass` sınıf içindeki `MyMethod` Yöntemi ayrıştırır `MyFile.exe` ve çıktıyı konsol penceresinde görüntüler.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

Önceki örnekte, farklı imzalara sahip `MyMethod` adlı birkaç yöntem olabilir. Aşağıdaki komut, **void** dönüş türü ve **Int32** ve **String**parametre türleri ile `MyMethod` örnek yöntemi ayrıştırır.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> 1,0 ve 1,1 .NET Framework sürümlerinde, yöntem adını izleyen sol ayraç, imzadan sonra sağ parantez ile dengelenmesi gerekir: `MyMethod(instance void(int32))`. .NET Framework 2,0 ile başlayarak kapatma parantezi atlanmalıdır: `MyMethod(instance void(int32)`.

`static` bir yöntemi`Shared` (Visual Basic) almak için, `instance`anahtar sözcüğünü atlayın. `int32` ve `string` gibi basit türler olmayan sınıf türleri ad alanını içermelidir ve önünde anahtar sözcüğü `class`olmalıdır. Dış türlerin başına köşeli ayraçlar içinde kitaplık adı gelmelidir. Aşağıdaki komut, <xref:System.AppDomain> türünde bir parametreye sahip `MyMethod` adlı statik bir yöntemi ayrıştırır ve <xref:System.AppDomain>dönüş türüne sahiptir.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

İç içe geçmiş bir türün başında, eğik çizgi ile sınırlandırılmış kapsayan sınıfı bulunmalıdır. Örneğin, `MyNamespace.MyClass` sınıfı `NestedClass`adlı iç içe bir sınıf içeriyorsa, iç içe yerleştirilmiş sınıf şu şekilde tanımlanır: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Ilasm.exe (IL Derleyici)](ilasm-exe-il-assembler.md)
- [Yönetilen Yürütme İşlemi](../../standard/managed-execution-process.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)

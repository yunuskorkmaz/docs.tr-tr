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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105052"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Ayrıştırıcı)

IL Desassembler IL Assembler *(Ilasm.exe)* için bir eşlik aracıdır. *Ildasm.exe* ara dil (IL) kodu içeren taşınabilir bir yürütülebilir (PE) dosya alır ve *Ilasm.exe*girişi olarak uygun bir metin dosyası oluşturur.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametreler

*.exe*, *.dll*, *.obj*, *.lib*ve *.winmd* dosyaları için aşağıdaki seçenekler mevcuttur.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/out=**`filename`|Sonuçları grafik kullanıcı arabiriminde görüntülemek yerine belirtilen `filename`çıktı dosyası oluşturur.|
|**/rtf**|Zengin metin biçiminde çıktılar üretir. **/text** seçeneği ile geçersiz.|
|**/metin**|Sonuçları grafik kullanıcı arabiriminde veya çıktı dosyası olarak değil, konsol penceresinde görüntüler.|
|**/html**|HTML biçiminde çıktı üretir. Yalnızca **/çıkış** seçeneği ile geçerlidir.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

*.exe*, *.dll*ve *.winmd* dosyaları için aşağıdaki ek seçenekler mevcuttur.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/bayt**|Gerçek bayt miktarını yönerge yorumları olarak onaltılık biçimde gösterir.|
|**/caverbal**|Sözlü biçimde özel öznitelik blob'ları üretir. Varsayılan ikili biçimdir.|
|**/keten**|Özgün kaynak satırları için başvurular içerir.|
|**/nobar**|Parçalara ayırma işleminin ilerleme durumu açılır penceresini gizler.|
|**/noca**|Özel özniteliklerin çıkışını gizler.|
|**/proje**|Meta verileri, ana windows runtime'da göründüğü gibi değil, yönetilen kodda göründüğü şekilde görüntüler. `PEfilename` Windows meta data (*.winmd*) dosyası değilse, bu seçeneğin hiçbir etkisi yoktur. [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği'ne](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)bakın.|
|**/pubonly**|Yalnızca genel türleri ve üyeleri ayrıştırır. **/görünürlüğe eşdeğer:PUB**.|
|**/quoteallnames**|Tüm adları tek tırnak işaretleri içine alır.|
|**/raweh**|Özel durum işleme yan tümcelerini ham biçimde gösterir.|
|**/kaynak**|Özgün kaynak satırları açıklamalar olarak gösterir.|
|**/belirteçler**|Sınıfların ve üyelerin meta veri belirteçlerini gösterir.|
|**/görünürlük:** `vis`[+`vis`...]|Yalnızca belirtilen görünürlüğe sahip türleri veya üyeleri ayrıştırır. Aşağıdakiler için `vis`geçerli değerler şunlardır:<br /><br /> **PUB** — Genel<br /><br /> **PRI** — Özel<br /><br /> **FAM** — Aile<br /><br /> **ASM** — Montaj<br /><br /> **FAA** — Aile ve Meclis<br /><br /> **FOA** — Aile veya Meclis<br /><br /> **PSC** — Özel Kapsam<br /><br /> Bu görünürlük değiştiricilerinin tanımları <xref:System.Reflection.MethodAttributes> için <xref:System.Reflection.TypeAttributes>bkz.|

Aşağıdaki seçenekler yalnızca dosya veya konsol çıktısı için *.exe*, *.dll*ve *.winmd* dosyaları için geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/tümü**|**/üstbilgi**, **/bayt**, **/istatistikler**, **/classlist**, ve **/belirteç seçeneklerinin** bir birleşimini belirtir.|
|**/classlist**|Modülde tanımlanmış sınıfların bir listesini içerir.|
|**/ileri**|İleriye dönük sınıf bildirimini kullanır.|
|**/üstbilgi**|Çıktıya dosyanın başlık bilgilerini ekler.|
|**/madde:** `class`[**::** `member`[`(sig`[]|Sağlanan bağımsız değişkene bağlı olarak aşağıdakileri ayrıştırır:<br /><br /> - Belirtilen `class`sökülür.<br />- Belirtilen `member` leri `class`söker.<br />- Belirtilen imza `member` `class` `sig`ile sökülür. `sig` Biçimi:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Not** .NET Framework sürümlerinde 1.0 ve `sig` 1.1, kapanış parantezi takip `(sig)`edilmelidir: . Net Framework 2.0 ile başlayarak kapanış parantezi atlanmalıdır: `(sig`.|
|**/noil**|IL derlemesi kod çıktısını engeller.|
|**/istatistikler**|Görüntüye istatistikleri ekler.|
|**/typelist**|Gidiş dönüş içinde tür sıralamasını korumak üzere türlerin tam listesini oluşturur.|
|**/unicode**|Çıktı için Unicode kodlaması kullanır.|
|**/utf8**|Çıktı için UTF-8 kodlaması kullanır. ANSI varsayılandır.|

Aşağıdaki seçenekler *.exe*, *.dll*, *.obj*, *.lib*ve sadece dosya veya konsol çıktısı için *.winmd* dosyaları için geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/meta data**`specifier`[= ]|Meta verileri gösterir, nerede: `specifier`<br /><br /> **MDHEADER** — Meta veri üstbilgi bilgilerini ve boyutlarını göster.<br /><br /> **HEX** — Bilgileri hex olarak ve kelimelerle göster.<br /><br /> **CSV** — Kayıt sayılarını ve yığın boyutlarını göster.<br /><br /> **UNREX** — Çözülmemiş haricileri göster.<br /><br /> **SCHEMA** — Meta veri üstbilgisini ve şema bilgilerini göster.<br /><br /> **RAW** — Ham meta veri tablolarını göster.<br /><br /> **HEAPS** — Ham yığınları göster.<br /><br /> **DOĞRULAMA** — Meta verilerin tutarlılığını doğrulayın.<br /><br /> **/meta verileri** birden çok kez belirtebilirsiniz, `specifier`için farklı değerler.|

Aşağıdaki seçenekler yalnızca dosya veya konsol çıktısı için *.lib* dosyaları için geçerlidir.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/objectfile**=`filename`|Belirtilen kitaplıkta tek bir nesne dosyasının meta verilerini gösterir.|

> [!NOTE]
> *Ildasm.exe* için tüm seçenekler büyük/küçük harf duyarsız ve ilk üç harf tarafından tanınan. Örneğin, **/quo** **/quoteallnames'e**eşdeğerdir. Bağımsız değişkenler belirten seçenekler, seçenek ve bağımsız değişken arasında ayıraç olarak ya iki nokta üst üste (:) ya da eşittir işaretini (=) kabul eder. Örneğin, **/output:** *dosya adı* **/output=** dosya *adı*eşdeğerdir.

## <a name="remarks"></a>Açıklamalar

*Ildasm.exe* sadece diskte PE dosyaları üzerinde çalışır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

*Ildasm.exe* tarafından üretilen metin dosyası IL Assembler *(Ilasm.exe)* girişi olarak kullanılabilir. Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kodu derleyip çıktısını *Ildasm.exe*üzerinden çalıştırdıktan sonra, ortaya çıkan IL metin dosyası eksik öznitelikleri eklemek için elle düzenlenebilir. Ardından bu metin dosyasını IL Derleyicisi aracılığıyla çalıştırarak son bir çalıştırılabilir dosya oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.  

Meta veriyi ve varolan herhangi bir PE dosyasının ayrıştırılmış kodunu hiyerarşik bir ağaç görünümünde görüntülemek için varsayılan GUI'yi IL Ayrıştırıcısı'nda kullanabilirsiniz. GUI'yi kullanmak için, *PEfilename* bağımsız değişkenini veya herhangi bir seçeneği sağlamadan komut satırına **ildasm** yazın. **Dosya** menüsünden *Ildasm.exe'ye*yüklemek istediğiniz PE dosyasına gidebilirsiniz. Seçili PE için görüntülenen meta verileri ve sökülen kodu kaydetmek için **Dosya** menüsünden **Dökümü** komutunu seçin. Yalnızca hiyerarşik ağaç görünümünü kaydetmek için **Dosya** menüsünden **Ağaç Görünümü Boşalt** komutunu seçin. Bir dosyayı *Ildasm.exe'ye* yüklemek ve çıktıyı yorumlamak için ayrıntılı bir kılavuz için, Windows SDK ile birlikte gelen Örnekler klasöründe bulunan *Ildasm.exe* Tutorial'a bakın.

*Ildasm.exe'ye* katıştırılmış kaynaklar içeren bir *PEfilename* bağımsız değişkeni sağlarsanız, araç birden çok çıktı dosyası üretir: IL kodu içeren bir metin dosyası ve her katıştırılmış yönetilen kaynak için, meta verilerden kaynağın adı kullanılarak üretilen bir .resources dosyası. *PEfilename'ye*yönetilmeyen bir kaynak katıştırılmışsa, **/çıktı** seçeneği tarafından IL çıktısı için belirtilen dosya adı kullanılarak bir .res dosyası üretilir.

> [!NOTE]
> *Ildasm.exe,.obj* ve *.lib* giriş *.lib* dosyaları için yalnızca meta veri açıklamalarını gösterir. Bu dosya türleri için IL kodu ayrıştırılmaz.

Dosyanın yönetilip yönetilmediğini belirlemek için *Ildasm.exe'yi* an.exe veya *.dll* dosyası üzerinden çalıştırabilirsiniz. Dosya yönetilmiyorsa; araç, dosyada geçerli hiçbir ortak dil çalışma zamanı başlığı olmadığını ve ayrıştırılamayacağını belirten bir ileti görüntüler. Dosya yönetiliyorsa, araç başarıyla çalışır.

## <a name="version-information"></a>Sürüm Bilgileri

.NET Framework 4.5 ile başlayarak, *Ildasm.exe* ham ikili içeriği görüntüleyerek tanınmayan bir mareşal BLOB (ikili büyük nesne) işler. Örneğin aşağıdaki kod, bir C# programı tarafından oluşturulmuş sıralama BLOB'unun nasıl görüntülendiğini gösterir:

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

.NET Framework 4.5 ile başlayarak *Ildasm.exe,* *ildasm.exe* çıktısından aşağıdaki alıntıda gösterildiği gibi, arabirim uygulamalarına uygulanan öznitelikleri görüntüler:

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

Aşağıdaki komut, PE dosyasının `MyHello.exe` *Ildasm.exe* varsayılan GUI'de görüntülenmesi için meta verilerin ve sökülen kodun bulunmasına neden olur.

```console
ildasm myHello.exe
```

Aşağıdaki komut dosyayı `MyFile.exe` söker ve ortaya çıkan IL Assembler *metnini MyFile.il*dosyada depolar.

```console
ildasm MyFile.exe /output:MyFile.il
```

Aşağıdaki komut dosyayı `MyFile.exe` söker ve ortaya çıkan IL Assembler metnini konsol penceresine görüntüler.

```console
ildasm MyFile.exe /text
```

Dosya `MyApp.exe` gömülü yönetilen ve yönetilmeyen kaynaklar içeriyorsa, aşağıdaki komut dört dosya üretir: *MyApp.il*, *MyApp.res*, *Icons.resources*ve *Message.resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Aşağıdaki komut, içindeki `MyMethod` `MyClass` yöntemi söker `MyFile.exe` ve çıktıyı konsol penceresine görüntüler.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

Önceki örnekte, farklı imzalarla `MyMethod` birlikte birkaç yöntem olabilir. Aşağıdaki komut, örnek `MyMethod` **yöntemini void'in** dönüş türü ve **int32** ve **string**parametre türleri ile söker.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> .NET Framework 1.0 ve 1.1 sürümlerinde, yöntem adını izleyen sol parantez imzadan sonra sağ parantez ile `MyMethod(instance void(int32))`dengelenmelidir: . .NET Framework 2.0 ile başlayarak kapanış parantezi atlanmalıdır: `MyMethod(instance void(int32)`.

Bir `static` yöntemi (Visual`Shared` Basic'teki yöntem) almak `instance`için, anahtar sözcüğü atla. Gibi `int32` ilkel türleri olmayan ve `string` ad alanını içermesi gereken ve önce `class`anahtar sözcük ten önce olması gereken sınıf türleri. Dış türlerin başına köşeli ayraçlar içinde kitaplık adı gelmelidir. Aşağıdaki komut, bir parametre `MyMethod` türüne <xref:System.AppDomain> sahip ve bir dönüş türüne <xref:System.AppDomain>sahip statik bir yöntemi söker.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

İç içe geçmiş bir türün başında, eğik çizgi ile sınırlandırılmış kapsayan sınıfı bulunmalıdır. Örneğin, `MyNamespace.MyClass` sınıf adlı `NestedClass`iç içe bir sınıf içeriyorsa, iç `class MyNamespace.MyClass/NestedClass`içe geçen sınıf aşağıdaki gibi tanımlanır: .

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Ilasm.exe (IL Derleyici)](ilasm-exe-il-assembler.md)
- [Yönetilen Yürütme İşlemi](../../standard/managed-execution-process.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)

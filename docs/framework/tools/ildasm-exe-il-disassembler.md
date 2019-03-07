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
ms.openlocfilehash: 3e96f86e516e7b741aa9fbf67efd1683d0845101
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488519"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Ayrıştırıcı)

IL ayrıştırıcısı IL derleyicisi için bir yardımcı araç olan (*Ilasm.exe*). *Ildasm.exe* Ara dil (IL) kodunu içerir ve bir metin dosyası olarak uygun oluşturan bir taşınabilir yürütülebilir (PE) dosyayı alır girdi için *Ilasm.exe*.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametreler

Aşağıdaki seçenekler kullanılabilir *.exe*, *.dll*, *.obj*, *.lib*, ve *.winmd* dosyaları.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/ out =** `filename`|Belirtilen bir çıktı dosyası oluşturur `filename`, sonuçları bir grafik kullanıcı arabiriminde görüntülemek yerine.|
|**/RTF**|Zengin metin biçiminde çıktılar üretir. İle geçersiz **/Text** seçeneği.|
|**/ Text**|Sonuçları grafik kullanıcı arabiriminde veya çıktı dosyası olarak değil, konsol penceresinde görüntüler.|
|**/HTML**|HTML biçiminde çıktı üretir. Geçerli **/output** yalnızca seçeneği.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

Aşağıdaki ek seçenekler kullanılabilir *.exe*, *.dll*, ve *.winmd* dosyaları.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/bytes**|Gerçek bayt miktarını yönerge yorumları olarak onaltılık biçimde gösterir.|
|**/caverbal**|Sözlü biçimde özel öznitelik blob'ları üretir. Varsayılan ikili biçimdir.|
|**/LineNum**|Özgün kaynak satırları için başvurular içerir.|
|**/nobar**|Parçalara ayırma işleminin ilerleme durumu açılır penceresini gizler.|
|**/noca**|Özel özniteliklerin çıkışını gizler.|
|**/ Project**|Göründüğü şekilde yerine yönetilen kod için bu meta veriyi özgün görüntüler [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Varsa `PEfilename` Windows meta verileri değil (*.winmd*) dosyası, bu seçenek, hiçbir etkiye sahiptir. Bkz: [Windows Store uygulamaları ve Windows çalışma zamanı için .NET Framework desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Yalnızca genel türleri ve üyeleri ayrıştırır. Eşdeğer **/visibility:PUB**.|
|**/quoteallnames**|Tüm adları tek tırnak işaretleri içine alır.|
|**/raweh**|Özel durum işleme yan tümcelerini ham biçimde gösterir.|
|**/ Source**|Özgün kaynak satırları açıklamalar olarak gösterir.|
|**tokens**|Sınıfların ve üyelerin meta veri belirteçlerini gösterir.|
|**/ Visibility:** `vis`[+`vis`...]|Yalnızca belirtilen görünürlüğe sahip türleri veya üyeleri ayrıştırır. Aşağıdakiler için geçerli değerler `vis`:<br /><br /> **PUB** — genel<br /><br /> **PRI** — özel<br /><br /> **FAM** — aile<br /><br /> **ASM** — derleme<br /><br /> **FAA** — Aile ve derleme<br /><br /> **FOA** — Aile veya derleme<br /><br /> **PSC** — özel kapsam<br /><br /> Bu görünürlük değiştiricilerinin tanımları için bkz. <xref:System.Reflection.MethodAttributes> ve <xref:System.Reflection.TypeAttributes>.|

Aşağıdaki seçenekler geçerlidir *.exe*, *.dll*, ve *.winmd* dosya ya da konsol çıktısı yalnızca dosyaları.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/ all**|Bir bileşimini belirtir **/header**, **/bytes**, **stats**, **/classlist**, ve **/belirteçler** Seçenekler.|
|**/classlist**|Modülde tanımlanmış sınıfların bir listesini içerir.|
|**/ iletme**|İleriye dönük sınıf bildirimini kullanır.|
|**OPTIONAL**|Çıktıya dosyanın başlık bilgilerini ekler.|
|**/ item:** `class`[**::** `member`[`(sig`]]|Sağlanan bağımsız değişkene bağlı olarak aşağıdakileri ayrıştırır:<br /><br /> -Belirtilen ayrıştırır `class`.<br />-Belirtilen ayrıştırır `member` , `class`.<br />-Ayrıştırır `member` , `class` belirtilen imzayla `sig`. Biçimi `sig` olan:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Not** .NET Framework sürümleri 1.0 ve 1.1 `sig` bir kapanış parantezi gelmelidir: `(sig)`. Net Framework 2.0 ile kapanış parantezi eklenmemelidir: (`sig`.|
|**/noil**|IL derlemesi kod çıktısını engeller.|
|**stats**|Görüntüye istatistikleri ekler.|
|**/typelist**|Gidiş dönüş içinde tür sıralamasını korumak üzere türlerin tam listesini oluşturur.|
|**/ Unicode**|Çıktı için Unicode kodlaması kullanır.|
|**/UTF8**|Çıktı için UTF-8 kodlaması kullanır. ANSI varsayılandır.|

Aşağıdaki seçenekler geçerlidir *.exe*, *.dll*, *.obj*, *.lib*, ve *.winmd* dosyaları Dosya ya da konsol çıktısı yalnızca.

| Seçenek | Açıklama |
| ------ | ----------- |
|**Metadata**[=`specifier`]|Meta verileri gösterir burada `specifier` olan:<br /><br /> **MDHEADER** — meta veri başlık bilgilerini ve boyutlarını görüntüleyin.<br /><br /> **ONALTILIK** — bilgileri onaltılık de sözcükler göster.<br /><br /> **CSV** — kayıt sayılarını gösterir ve yığın boyutlarını.<br /><br /> **UNREX** — çözülmemiş dış öğeleri görüntüleyin.<br /><br /> **ŞEMA** — meta veri başlığı ve şema bilgilerini görüntüleyin.<br /><br /> **Ham** — ham meta veri tablolarını görüntüleyin.<br /><br /> **YIĞINLAR** — ham yığınları görüntüleyin.<br /><br /> **DOĞRULAMA** — meta veri tutarlılığını doğrulayın.<br /><br /> Belirtebileceğiniz **metadata** birden çok kez için farklı değerlerle `specifier`.|

Aşağıdaki seçenekler geçerlidir *.lib* dosya ya da konsol çıktısı yalnızca dosyaları.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/objectfile**=`filename`|Belirtilen kitaplıkta tek bir nesne dosyasının meta verilerini gösterir.|

> [!NOTE]
> Tüm seçenekler için *Ildasm.exe* büyük/küçük harfe ve ilk üç harfinden tanınır. Örneğin, **/quo** eşdeğerdir **/quoteallnames**. Bağımsız değişkenler belirten seçenekler, seçenek ve bağımsız değişken arasında ayıraç olarak ya iki nokta üst üste (:) ya da eşittir işaretini (=) kabul eder. Örneğin, **/output:** *filename* eşdeğerdir **/output =** *filename*.

## <a name="remarks"></a>Açıklamalar

*Ildasm.exe* yalnızca diskteki PE dosyaları üzerinde çalışır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

Tarafından üretilen metin dosyası *Ildasm.exe* IL derleyicisi giriş olarak kullanılabilir (*Ilasm.exe*). Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kodu derledikten çıktısını çalıştıran sonra *Ildasm.exe*, eksik öznitelikler eklemek için elle düzenlenerek elde edilen IL metin dosyası olabilir. Ardından bu metin dosyasını IL Derleyicisi aracılığıyla çalıştırarak son bir çalıştırılabilir dosya oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.  

Meta veriyi ve varolan herhangi bir PE dosyasının ayrıştırılmış kodunu hiyerarşik bir ağaç görünümünde görüntülemek için varsayılan GUI'yi IL Ayrıştırıcısı'nda kullanabilirsiniz. GUI'yi kullanmak için yazmanız **ildasm** sağlama olmadan komut satırında *PEfilename* bağımsız değişkeni veya herhangi bir seçenek. Gelen **dosya** menüsünde gidebilirsiniz yüklemek istediğiniz PE dosyasına *Ildasm.exe*. Meta verileri ve seçili PE için görüntülenen ayrıştırılmış kodu kaydetmek için seçmeniz **dökümü** komutunu **dosya** menüsü. Seçeneğini yalnızca hiyerarşik ağaç görünümünü kaydetmek için **döküm Treeview** komutunu **dosya** menüsü. İçine bir dosya yüklemek için ayrıntılı bir kılavuz için *Ildasm.exe* ve çıktıyı yorumlama, *Ildasm.exe* ile birlikte gelen örnekler klasöründe bulunan öğreticide [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

Sağlarsanız *Ildasm.exe* ile bir *PEfilename* katıştırılmış kaynakları içeren bağımsız değişkeni, aracın birden çok çıktı dosyası üretir: IL kodunu içeren ve katıştırılmış her yönetilen bir metin dosyası Kaynak, kaynağın meta verideki adı kullanılarak oluşturulan bir .resources dosyası. Yönetilmeyen bir kaynağı olarak eklendiyse *PEfilename*, tarafından IL .çıktısı için belirtilen dosya adı kullanılarak bir .res dosyası üretilir **/output** seçeneği.

> [!NOTE]
> *Ildasm.exe* yalnızca meta veri açıklamalarını gösterir *.obj* ve *.lib* giriş dosyaları. Bu dosya türleri için IL kodu ayrıştırılmaz.

Çalıştırabileceğiniz *Ildasm.exe* üzerinden an.exe veya *.dll* dosyanın yönetilip yönetilmediğini belirlemek için dosya. Dosya yönetilmiyorsa; araç, dosyada geçerli hiçbir ortak dil çalışma zamanı başlığı olmadığını ve ayrıştırılamayacağını belirten bir ileti görüntüler. Dosya yönetiliyorsa, araç başarıyla çalışır.

## <a name="version-information"></a>Sürüm Bilgileri

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* ham ikili içeriği görüntüleyerek, tanınmayan bir sıralama BLOB'u (ikili büyük nesne) işler. Örneğin aşağıdaki kod, bir C# programı tarafından oluşturulmuş sıralama BLOB'unun nasıl görüntülendiğini gösterir:

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* alınan aşağıdaki alıntıda gösterildiği arabirim uygulamalarına uygulanan öznitelikleri görüntüler *Ildasm.exe* çıktı:

```
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

Aşağıdaki komut, meta veriler neden olur ve PE dosyası için kodu çözülürken `MyHello.exe` görüntülenecek *Ildasm.exe* GUI varsayılan.

```console
ildasm myHello.exe
```

Aşağıdaki komut dosyasını ayrıştırır `MyFile.exe` ve elde edilen IL derleyicisi metnini dosyasında depolar *MyFile.il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Aşağıdaki komut dosyasını ayrıştırır `MyFile.exe` ve elde edilen IL derleyicisi metnini konsol penceresinde görüntüler.

```console
ildasm MyFile.exe /text
```

Varsa dosyayı `MyApp.exe` katıştırılmış yönetilen ve yönetilmeyen kaynaklar içeren aşağıdaki komut dört dosya üretir: *Gt;MyApp.İl &*, *gt;MyApp.res*, *gt;Icons.Resources*, ve *Message.resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Aşağıdaki komutu yöntemini ayrıştırır `MyMethod` sınıf içindeki `MyClass` içinde `MyFile.exe` ve çıktıyı konsol penceresinde görüntüler.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

Önceki örnekte olabilir adlandırılmış çeşitli yöntemler `MyMethod` farklı imzalara sahip. Aşağıdaki komut örnek yöntemini ayrıştırır `MyMethod` dönüş türüyle **void** ve parametre türleri **Int32** ve **dize**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> İmzadan sonra .NET Framework sürümleri 1.0 ve 1.1, yöntem bir sol ayraç adı sağ ayraç ile dengelenmelidir: `MyMethod(instance void(int32))`. .NET Framework 2.0 ile kapanış parantezi eklenmemelidir: `MyMethod(instance void(int32)`.

Alınacak bir `static` yöntemi (`Shared` yöntem Visual Basic'te), anahtar sözcüğünü kullanmayın `instance`. Sınıf gibi basit türlerin olmayan türleri `int32` ve `string` ad alanı içermelidir ve anahtar sözcüğünden sonra gelen gerekir `class`. Dış türlerin başına köşeli ayraçlar içinde kitaplık adı gelmelidir. Aşağıdaki komutu adlı statik bir yöntemi ayrıştırır `MyMethod` türünde bir parametreye sahip <xref:System.AppDomain> ve bir dönüş türüne sahip <xref:System.AppDomain>.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

İç içe geçmiş bir türün başında, eğik çizgi ile sınırlandırılmış kapsayan sınıfı bulunmalıdır. Örneğin, varsa `MyNamespace.MyClass` sınıfı içeren bir iç içe geçmiş sınıf adlı `NestedClass`, iç içe sınıf şu şekilde tanımlanır: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](../../../docs/framework/tools/index.md)
- [Ilasm.exe (IL Derleyici)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Yönetilen Yürütme İşlemi](../../../docs/standard/managed-execution-process.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

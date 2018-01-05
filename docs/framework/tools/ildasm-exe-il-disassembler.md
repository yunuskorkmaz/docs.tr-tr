---
title: "Ildasm.exe (IL Ayrıştırıcı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f42726b24abe78b151e4174da37b7c7bfff4c8d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Ayrıştırıcı)

IL ayrıştırıcı Yardımcısı IL derleyici için araçtır (*Ilasm.exe*). *Ildasm.exe* alır Giriş Ara dile (IL) kodunu içerir ve bir metin dosyası olarak uygun oluşturan bir taşınabilir yürütülebilir (PE) dosyası *Ilasm.exe*.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```
ildasm [options] [PEfilename] [options]
```

#### <a name="parameters"></a>Parametreler

Aşağıdaki seçenekler kullanılabilir *.exe*, *.dll*, *.obj*, *.lib*, ve *.winmd* dosyaları.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/ out =**`filename`|Bir çıkış dosyası belirtilen oluşturur `filename`, sonuçlarını görüntüleyen bir grafik kullanıcı arabirimi yerine.|
|**/RTF**|Zengin metin biçiminde çıktılar üretir. İle geçersiz **/Text** seçeneği.|
|**/ Text**|Sonuçları grafik kullanıcı arabiriminde veya çıktı dosyası olarak değil, konsol penceresinde görüntüler.|
|**/HTML**|HTML biçiminde çıktı üretir. Geçerli ile **/çıkış** yalnızca seçeneği.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

Aşağıdaki ek seçenekler için kullanılabilir *.exe*, *.dll*, ve *.winmd* dosyaları.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/bytes**|Gerçek bayt miktarını yönerge yorumları olarak onaltılık biçimde gösterir.|
|**/caverbal**|Sözlü biçimde özel öznitelik blob'ları üretir. Varsayılan ikili biçimdir.|
|**/LineNum**|Özgün kaynak satırları için başvurular içerir.|
|**/nobar**|Parçalara ayırma işleminin ilerleme durumu açılır penceresini gizler.|
|**/noca**|Özel özniteliklerin çıkışını gizler.|
|**/ Project**|Yerel göründüğü şekilde yerine yönetilen kod için bu şekilde görünür meta verileri görüntüler [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Varsa `PEfilename` Windows meta veri değil (*.winmd*) dosyası, bu seçenek etkisi yoktur. Bkz: [Windows mağazası uygulamaları ve Windows çalışma zamanı için .NET Framework Destek](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Yalnızca genel türleri ve üyeleri ayrıştırır. Eşdeğer **/visibility:PUB**.|
|**/quoteallnames**|Tüm adları tek tırnak işaretleri içine alır.|
|**/raweh**|Özel durum işleme yan tümcelerini ham biçimde gösterir.|
|**/ Source**|Özgün kaynak satırları açıklamalar olarak gösterir.|
|**tokens**|Sınıfların ve üyelerin meta veri belirteçlerini gösterir.|
|**/Visibility:** `vis`[+`vis`...]|Yalnızca belirtilen görünürlüğe sahip türleri veya üyeleri ayrıştırır. Aşağıdaki geçerli değerler `vis`:<br /><br /> **PUB** — ortak<br /><br /> **Bi** — özel<br /><br /> **FAM** — ailesi<br /><br /> **ASM** — derleme<br /><br /> **FAA** — ailesi ve derleme<br /><br /> **FOA** — ailesi veya derleme<br /><br /> **PSC** — özel kapsamı<br /><br /> Bu görünürlük değiştiricileri tanımları için bkz: <xref:System.Reflection.MethodAttributes> ve <xref:System.Reflection.TypeAttributes>.|

Aşağıdaki seçenekler için geçerli *.exe*, *.dll*, ve *.winmd* dosya veya yalnızca çıkış konsol için dosyalar.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/ all**|Bir bileşimini belirtir **/header**, **/bytes**, **/stats**, **/classlist**, ve **/belirteçler** Seçenekler.|
|**/classlist**|Modülde tanımlanmış sınıfların bir listesini içerir.|
|**/ iletme**|İleriye dönük sınıf bildirimini kullanır.|
|**/Headers**|Çıktıya dosyanın başlık bilgilerini ekler.|
|**/ Madde:** `class`[**::** `member`[`(sig`]]|Sağlanan bağımsız değişkene bağlı olarak aşağıdakileri ayrıştırır:<br /><br /> -Ayrıştırır belirtilen `class`.<br />-Ayrıştırır belirtilen `member` , `class`.<br />-Ayrıştırır `member` , `class` belirtilen imzayla `sig`. Biçimi `sig` değil:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Not** .NET Framework sürüm 1.0 ve 1.1 `sig` bir kapatma parantezi gelmelidir: `(sig)`. Kapatma parantezi Net Framework 2.0 ile başlayan gereken atlanmış: (`sig`.|
|**/noil**|IL derlemesi kod çıktısını engeller.|
|**/ stats**|Görüntüye istatistikleri ekler.|
|**/typelist**|Gidiş dönüş içinde tür sıralamasını korumak üzere türlerin tam listesini oluşturur.|
|**/ Unicode**|Çıktı için Unicode kodlaması kullanır.|
|**/UTF8**|Çıktı için UTF-8 kodlaması kullanır. ANSI varsayılandır.|

Aşağıdaki seçenekler için geçerli *.exe*, *.dll*, *.obj*, *.lib*, ve *.winmd* dosyaları Dosya veya yalnızca çıkış konsol.

| Seçenek | Açıklama |
| ------ | ----------- |
|**Metadata**[=`specifier`]|Meta veriler gösterir nerede `specifier` değil:<br /><br /> **MDHEADER** — boyutları ve meta verileri üst bilgileri göster.<br /><br /> **ONALTILIK** — onaltılık de sözcükler olduğu gibi bilgileri göster.<br /><br /> **CSV** — kayıt sayıları göstermek ve yığın boyutu.<br /><br /> **UNREX** — çözümlenmemiş externals göster.<br /><br /> **ŞEMA** — meta verileri üstbilgi ve şema bilgilerini gösterir.<br /><br /> **Ham** — ham meta veri tabloları göster.<br /><br /> **YIĞIN** — ham yığın göster.<br /><br /> **DOĞRULAMA** — meta veri tutarlılığını doğrula.<br /><br /> Belirleyebileceğiniz **metadata** birden çok kez farklı değerlere sahip `specifier`.|

Aşağıdaki seçenekler için geçerli *.lib* dosya veya yalnızca çıkış konsol için dosyalar.

| Seçenek | Açıklama |
| ------ | ----------- |
|**/objectfile**=`filename`|Belirtilen kitaplıkta tek bir nesne dosyasının meta verilerini gösterir.|

> [!NOTE]
> Tüm seçenekler için *Ildasm.exe* büyük küçük harf duyarsız ve ilk üç harf tarafından tanınan. Örneğin, **/quo** eşdeğerdir **/quoteallnames**. Bağımsız değişkenler belirten seçenekler, seçenek ve bağımsız değişken arasında ayıraç olarak ya iki nokta üst üste (:) ya da eşittir işaretini (=) kabul eder. Örneğin, **/çıktı:** *filename* eşdeğerdir **/çıkış =** *filename*.

## <a name="remarks"></a>Açıklamalar

*Ildasm.exe* yalnızca diskte PE dosyaları çalıştırır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

Metin dosyasını üretilen tarafından *Ildasm.exe* IL derleyici giriş olarak kullanılan (*Ilasm.exe*). Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kod derleme ve çıktısını çalıştıran sonra *Ildasm.exe*, el ile düzenleyebilirsiniz eksik öznitelikler eklemek için sonuçta elde edilen IL metin dosyası olabilir. Ardından bu metin dosyasını IL Derleyicisi aracılığıyla çalıştırarak son bir çalıştırılabilir dosya oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.  

Meta veriyi ve varolan herhangi bir PE dosyasının ayrıştırılmış kodunu hiyerarşik bir ağaç görünümünde görüntülemek için varsayılan GUI'yi IL Ayrıştırıcısı'nda kullanabilirsiniz. GUI kullanılacak türü **ildasm** sağladığını olmadan komut satırında *PEfilename* bağımsız değişken veya herhangi bir seçenek. Gelen **dosya** menüsünde gezinmenizi içine yüklemek istediğiniz PE dosyasına *Ildasm.exe*. Seçili PE için görüntülenen artık hata ayıklayabildiğinize kodunu ve meta verileri kaydetmek için seçin **dökümü** komutunu **dosya** menüsü. Yalnızca, select hiyerarşik ağaç görünümü kaydetmek için **dökümü Treeview** komutunu **dosya** menüsü. İçine bir dosya yüklemek için ayrıntılı bir kılavuz için *Ildasm.exe* ve çıktı yorumlama, *Ildasm.exe* ile birlikte örnekleri klasöründe öğretici, [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

Sağlarsanız *Ildasm.exe* ile bir *PEfilename* katıştırılmış kaynakları içeren bağımsız değişkeni, aracı birden çok çıktı dosyalarını oluşturur: IL kodu içeren ve her biri için yönetilen katıştırılmış bir metin dosyası Kaynak, kaynağın adını meta veriler kullanılarak üretilen bir .resources dosyası. Yönetilmeyen bir kaynak olarak eklendiyse *PEfilename*, IL çıktı tarafından belirtilen dosya adı kullanılarak oluşturulan bir .res dosyası **/çıkış** seçeneği.

> [!NOTE]
> *Ildasm.exe* yalnızca meta veri açıklamalarını gösterir *.obj* ve *.lib* giriş dosyaları. Bu dosya türleri için IL kodu ayrıştırılmaz.

Çalıştırabilirsiniz *Ildasm.exe* an.exe üzerinden veya *.dll* dosya yönetilen olup olmadığını belirlemek için dosya. Dosya yönetilmiyorsa; araç, dosyada geçerli hiçbir ortak dil çalışma zamanı başlığı olmadığını ve ayrıştırılamayacağını belirten bir ileti görüntüler. Dosya yönetiliyorsa, araç başarıyla çalışır.

## <a name="version-information"></a>Sürüm Bilgileri

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* ham ikili içerik görüntüleyerek tanınmayan bir sıralama BLOB (ikili büyük nesne) işler. Örneğin aşağıdaki kod, bir C# programı tarafından oluşturulmuş sıralama BLOB'unun nasıl görüntülendiğini gösterir:

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* yapılan aşağıdaki alıntı gösterildiği gibi arabirim uygulamaları için uygulanan öznitelikleri görüntüler *Ildasm.exe* çıktı:

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

Aşağıdaki komut meta verileri neden olur ve PE dosyasının kodu çözülürken `MyHello.exe` görüntülemek için *Ildasm.exe* GUI varsayılan.

```console
ildasm myHello.exe
```

Aşağıdaki komut dosyasını ayrıştırır `MyFile.exe` ve sonuçta elde edilen IL derleyici metin dosyasında depolar *MyFile.il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Aşağıdaki komut dosyasını ayrıştırır `MyFile.exe` ve sonuçta elde edilen IL derleyici metin konsol penceresinde görüntüler.

```console
ildasm MyFile.exe /text
```

Varsa dosyayı `MyApp.exe` katıştırılmış yönetilen ve yönetilmeyen kaynakları içeren aşağıdaki komutu, dört dosyaları üretir: *MyApp.il*, *MyApp.res*, *Icons.resources*, ve *Message.resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Aşağıdaki komutu yöntemi ayrıştırır `MyMethod` sınıfı içinde `MyClass` içinde `MyFile.exe` ve çıktıyı konsol penceresinde görüntüler.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

Önceki örnekte olabilir adlı birkaç yöntem `MyMethod` farklı imzalara sahip. Aşağıdaki komutu örnek yöntemi ayrıştırır `MyMethod` dönüş türüne sahip **void** ve parametre türleri **Int32** ve **dize**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> İmza sonra .NET Framework sürüm 1.0 ve 1.1, yöntem aşağıdaki sol parantez adı sağ parantez ile dengelenmelidir: `MyMethod(instance void(int32))`. .NET Framework 2.0 ile kapatma parantezi başlangıç gerekir atlanmış: `MyMethod(instance void(int32)`.

Alınacak bir `static` yöntemi (`Shared` yöntemi Visual Basic'te), anahtar sözcüğü atlayın `instance`. Sınıf gibi basit türler olmayan türlerini `int32` ve `string` ad içermelidir ve anahtar sözcüğüyle gelmelidir `class`. Dış türlerin başına köşeli ayraçlar içinde kitaplık adı gelmelidir. Aşağıdaki komutu adlı bir statik yöntem ayrıştırır `MyMethod` türünde bir parametre olan <xref:System.AppDomain> ve dönüş türüne sahip <xref:System.AppDomain>.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

İç içe geçmiş bir türün başında, eğik çizgi ile sınırlandırılmış kapsayan sınıfı bulunmalıdır. Örneğin, varsa `MyNamespace.MyClass` sınıfı içeren adlı bir iç içe geçmiş sınıf `NestedClass`, iç içe geçmiş sınıf şu şekilde tanımlanır: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Ayrıca bkz.

[Araçlar](../../../docs/framework/tools/index.md)  
[Ilasm.exe (IL Derleyici)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)  
[Yönetilen Yürütme İşlemi](../../../docs/standard/managed-execution-process.md)  
[Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

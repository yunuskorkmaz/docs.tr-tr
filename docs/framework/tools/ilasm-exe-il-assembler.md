---
title: Ilasm.exe (IL Derleyici)
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b73a98542dfc6fa68e79655bc5538cf005e4636
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492597"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Derleyici)

IL Derleyicisi ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur. (IL hakkında daha fazla bilgi için bkz. [Managed Execution Process](../../../docs/standard/managed-execution-process.md).) IL ve gereken meta veriyi içeren elde edilen çalıştırılabilir dosyayı çalıştırarak IL'in beklendiği gibi çalışıp çalışmadığını belirleyebilirsiniz.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parametreler

| Bağımsız Değişken | Açıklama |
| -------- | ----------- |
|`filename`|.il kaynak dosyasının adı. Bu dosya meta veri bildirim yönergeleri ve simgesel IL yönergelerinden oluşur. Birden çok kaynak dosya bağımsız değişkeni ile tek bir PE dosyası oluşturmak için sağlanan *Ilasm.exe*. **Not:** .il kaynak dosyasındaki son kod satırının bir boşluk karakteri veya satır sonu karakteri olduğundan emin olun.|

| Seçenek | Açıklama |
| ------ | ----------- |
|**/32bitpreferred**|32 bit tercih edilen bir görüntü (PE32) oluşturur.|
|**/ alignment:** `integer`|Filealignment değerini tarafından belirtilen değere ayarlar `integer` NT isteğe bağlı üst bilgisindeki. Eğer .alignment IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/ appcontaıner**|Üreten bir *.dll* veya *.exe* çıktı olarak Windows uygulama kapsayıcısında çalışan dosya.|
|**/ARM**|Hedef işlemci olarak Gelişmiş RISC Makinesi (ARM) belirtir.<br /><br /> Eğer görüntü bit genişliği belirtilmezse, varsayılan değer **/32bitpreferred**.|
|**/ Base:** `integer`|ImageBase tarafından belirtilen değere ayarlar `integer` NT isteğe bağlı üst bilgisindeki. Eğer .imagebase IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/Clock**|Belirtilen .il kaynak dosyası için aşağıdaki derleme sürelerini milisaniye cinsinden ölçer ve raporlar:<br /><br /> **Toplam çalışma**: İzleyen tüm belirli görevleri gerçekleştirirken geçen toplam süre.<br /><br /> **Başlangıç**: Yükleme ve dosya açma.<br /><br /> **MD yayma**: Meta veriyi yaymak.<br /><br /> **Ref Def çözümleme**: Başvuruları dosyadaki tanımlara çözümlemek.<br /><br /> **CEE dosya oluşturma**: Bellekte dosya görüntüsünü oluşturuluyor.<br /><br /> **PE dosyası yazma**: Görüntüyü bir PE dosyasına yazmak.|
|**/ debug**[:**IMPL**&#124;**OPT**]|Hata ayıklama bilgisi içerir (yerel değişken ve bağımsız değişken adları ve satır numaraları). Bir PDB dosyası oluşturur.<br /><br /> **/ debug** ek değer olmadan JIT iyileştirmesini devre dışı bırakır ve PDB dosyasındaki dizi noktalarını kullanır.<br /><br /> **IMPL** JIT iyileştirmesini devre dışı bırakır ve örtülü dizi noktalarını kullanır.<br /><br /> **OPT** JIT iyileştirmesini etkinleştirir ve örtülü dizi noktalarını kullanır.|
|**/ dll**|Üreten bir *.dll* çıktı olarak bir dosya.|
|**ENC:** `file`|Belirtilen kaynak dosyasından Düzenle ve Devam Et deltaları oluşturur.<br /><br /> Bu bağımsız değişken yalnızca akademik amaçlıdır ve ticari kullanım için desteklenmez.|
|**/ exe**|Çıktı olarak bir yürütülebilir dosya oluşturur. Bu varsayılandır.|
|**/ Flags:** `integer`|Bilgisindeki ımageflags değerini tarafından belirtilen değere ayarlar `integer` ortak dil çalışma zamanı üst bilgisindeki. Eğer .corflags IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar. CorHdr.h, comımage_flags bölümüne için geçerli değerlerin bir listesi için bkz. *tamsayı*.|
|**/fold**|Eşdeğer metot gövdelerini tek bir gövde olarak katlar.|
|/**highentropyva**|Yüksek entropili adres alanı düzenini (ASLR) destekleyen bir çıktı çalıştırılabilir dosyası oluşturur. (İçin varsayılan **/appcontaıner**.)|
|**/ include:** `includePath`|İle eklenen dosyaların aranacağı bir yol ayarlar `#include`.|
|**/itanium**|Hedef işlemci olarak Intel Itanium belirtir.<br /><br /> Eğer görüntü bit genişliği belirtilmezse, varsayılan değer **/pe64**.|
|**/Key:** `keyFile`|Derleme `filename` bulunan özel anahtarı kullanarak güçlü bir imzayla `keyFile`.|
|**/Key:** @`keySource`|Derleme `filename` , özel anahtarı kullanarak güçlü bir imza ile üretilen `keySource`.|
|**/ listeleme**|Standart çıktıda bir listeleme dosyası oluşturur. Eğer bu seçeneği koymazsanız, listeleme dosyası oluşturulmaz.<br /><br /> Bu parametre .NET Framework 2.0 ve sonrasında desteklenmez.|
|**/MDV:** `versionString`|Meta veri sürümü dizesini ayarlar.|
|**/msv:** `major`.`minor`|Meta veri akış sürümünü ayarlar burada `major` ve `minor` tamsayılardır.|
|**/noautoinherit**|Devre dışı bırakır öğesinden varsayılan devralmayı <xref:System.Object> temel sınıfa belirtildiğinde.|
|**/nocorstub**|CORExeMain taslağının oluşturulmasını bastırır.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/ Output:** `file.ext`|Çıktı dosyası adını ve uzantısını belirtir. Varsayılan olarak, çıktı dosyası adı ilk kaynak dosyasının adıyla aynıdır. Varsayılan uzantı *.exe*. Belirtirseniz **/dll** seçeneği, varsayılan uzantısıdır *.dll*. **Not:** Belirtme **/output**: lt;1}MyFile.dll **/dll** seçeneği. Siz belirtmezseniz **/dll**, sonuç adlı yürütülebilir bir dosya olacaktır *myfile.dll*.|
|**/optimize**|Uzun yönergeleri kısa olarak iyileştirir. Örneğin, `br` için `br.s`.|
|**/pe64**|64 bitlik bir görüntü oluşturur (PE32+).<br /><br /> Hiçbir hedef işlemci belirtilmezse, varsayılan değer `/itanium`.|
|**/ pdb**|Hata ayıklama bilgisi izlemeyi etkinleştirmeden bir PDB dosyası oluşturur.|
|**/quiet**|Sessiz modu belirtir; hiçbir derleme ilerlemesini bildirmez.|
|**/ Resource:** `file.res`|Belirtilen kaynak dosyayı içeren \*sonuç olarak .res biçimi *.exe* veya *.dll* dosya. Yalnızca tek bir .res dosyası belirtilebilir **/Resource** seçeneği.|
|**ssver:** `int`.`int`|NT isteğe bağlı üst bilgisinde alt sistem sürümünü ayarlar. İçin **/appcontaıner** ve **/arm** 6.02 en düşük sürüm numarasıdır.|
|**/Stack:** `stackSize`|İçin NT isteğe bağlı üst bilgisindeki SizeOfStackReserve değerini ayarlar `stackSize`.|
|**/stripreloc**|Temel yeniden konumlandırmanın gerekmediğini belirtir.|
|**/ Subsystem:** `integer`|Alt sistemi tarafından belirtilen değere ayarlar `integer` NT isteğe bağlı üst bilgisindeki. Eğer .subsystem IL yönergesi dosyada belirtiliyorsa, bu komut onu geçersiz kılar. Bkz. Winnt.h, IMAGE_SUBSYSTEM için geçerli değerlerin bir listesi için `integer`.|
|**/x64**|Hedef işlemci olarak bir 64 bitlik AMD işlemci belirtir.<br /><br /> Eğer görüntü bit genişliği belirtilmezse, varsayılan değer **/pe64**.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

> [!NOTE]
> Tüm seçenekler için *Ilasm.exe* büyük/küçük harfe ve ilk üç harfinden tanınır. Örneğin, **/lis** eşdeğerdir **/listing** ve **/res**: myresfile.res eşdeğerdir **/Resource**: myresfile.res eşdeğerdir. Bağımsız değişkenler belirten seçenekler, seçenek ve bağımsız değişken arasında ayıraç olarak ya iki nokta üst üste (:) ya da eşittir işaretini (=) kabul eder. Örneğin, **/output**:*file.ext* eşdeğerdir **/output**=*file.ext*.

## <a name="remarks"></a>Açıklamalar

IL Derleyicisi araç satıcılarına IL oluşturucuları tasarlamaları ve uygulamaları için yardımcı olur. Kullanarak *Ilasm.exe*, araç ve derleyici geliştiriciler odaklanmasına IL ve meta verileri nesil IL PE dosyası biçiminde yayma ile ilgili olmadan.

Benzer şekilde gibi çalışma zamanını hedefleyen diğer derleyiciler C# ve Visual Basic *Ilasm.exe* Ara nesne dosyaları oluşturmaz ve bir PE dosyası oluşturmak için bağlama aşaması gerektirmez.

IL Derleyicisi, çalışma zamanını hedef alan programlama dillerinin tüm varolan meta veri ve IL özelliklerini ifade edebilir. Böylece, IL yeterince ifade edilmesine bu programlama dillerinden birine yazılır ve ile derlenmiş yönetilen kod *Ilasm.exe*.

> [!NOTE]
> Eğer .il kaynak dosyasının son kod satırında bir boşluk veya satır sonu karakteri yoksa derleme başarısız olabilir.

Kullanabileceğiniz *Ilasm.exe* yardımcı aracı ile birlikte [ *Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). *Ildasm.exe* alır, IL kodunu içeren ve bir metin dosyası olarak uygun oluşturan bir PE dosyası için giriş *Ilasm.exe*. Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kodu derledikten ve çıktıyı çalıştıran sonra *Ildasm.exe*, eksik öznitelikler eklemek için elle düzenlenerek elde edilen IL metin dosyası olabilir. Ardından bu metin dosyasını çalıştırarak *Ilasm.exe* son bir yürütülebilir dosya.

Bu tekniği kullanarak ayrı derleyiciler tarafından üretilen çeşitli PE dosyalarından tek bir PE dosyası oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.

Bunu yapmak için kullanımını birleştirilmiş *Ildasm.exe* ve *Ilasm.exe* varsayılan olarak, mümkün olduğunca doğru olarak derleyici kısa yazdığınız IL kaynaklarınızda uzun olanlarla kodlamalarınızı değil (veya başka bir derleyici tarafından yayınlanan). Kullanım **/ optimize** seçeneği kısa kodlamaları mümkün olduğu yerde değiştirin.

> [!NOTE]
> *Ildasm.exe* yalnızca diskteki dosyalar üzerinde çalışır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

IL grameri daha fazla bilgi için bkz: içindeki asmparse.grammar dosyasına [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="version-information"></a>Sürüm Bilgileri

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], aşağıdakine benzer kod kullanarak bir arabirim uygulamasına özel öznitelik ekleyebilirsiniz:

```
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bir rastgele sıralama BLOB'u (ikili büyük nesne) ham ikili temsilini kullanarak aşağıdaki kodda gösterildiği gibi belirtebilirsiniz:

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

IL grameri daha fazla bilgi için bkz: içindeki asmparse.grammar dosyasına [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="examples"></a>Örnekler

Aşağıdaki komutu IL dosyasını derler *myTestFile.il* ve yürütülebilir dosya üreten *myTestFile.exe*.

```console
ilasm myTestFile
```

Aşağıdaki komutu IL dosyasını derler *myTestFile.il* ve üretir *.dll* dosya *myTestFile.dll*.

```console
ilasm myTestFile /dll
```

Aşağıdaki komutu IL dosyasını derler *myTestFile.il* ve üretir *.dll* dosya *myNewTestFile.dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Aşağıdaki kod örneği, "Hello World!" görüntüleyen son derece basit bir uygulama gösterilmektedir. konsola. Bu kodu derlemek ve ardından [ *Ildasm.exe* ](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) aracı bir IL dosyası oluşturabilirsiniz.

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

Aşağıdaki IL kod örneği önceki C# kod örneğine karşılık gelir. Bu kod, IL derleyicisi Aracı'nı kullanarak bir derlemenin içine derleyebilirsiniz. Hem IL ve C# kod örnekleri, "Hello World!" görüntüle konsola.

```
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](../../../docs/framework/tools/index.md)
- [*Ildasm.exe* (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
- [Yönetilen Yürütme İşlemi](../../../docs/standard/managed-execution-process.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

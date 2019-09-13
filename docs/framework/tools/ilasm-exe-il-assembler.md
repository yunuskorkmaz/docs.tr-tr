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
ms.openlocfilehash: fcc9ba5e379897247f50175603b1002d5688d215
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894692"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Derleyici)

IL Derleyicisi ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur. (Il hakkında daha fazla bilgi için bkz. [yönetilen yürütme işlemi](../../standard/managed-execution-process.md).) IL ve gereken meta veriyi içeren elde edilen çalıştırılabilir dosyayı çalıştırarak IL'in beklendiği gibi çalışıp çalışmadığını belirleyebilirsiniz.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parametreler

| Bağımsız Değişken | Açıklama |
| -------- | ----------- |
|`filename`|.il kaynak dosyasının adı. Bu dosya meta veri bildirim yönergeleri ve simgesel IL yönergelerinden oluşur. *Ilasm. exe*ile tek bir PE dosyası oluşturmak için birden çok kaynak dosya bağımsız değişkeni sağlanabilir. **Not:** .il kaynak dosyasındaki son kod satırının bir boşluk karakteri veya satır sonu karakteri olduğundan emin olun.|

| Seçenek | Açıklama |
| ------ | ----------- |
|**/32bittercihli**|32 bit tercih edilen bir görüntü (PE32) oluşturur.|
|**/hizalaması:** `integer`|NT isteğe bağlı üstbilgisinde dosya hizalamasını belirtilen `integer` değere ayarlar. Eğer .alignment IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/APPCONTAINER**|Çıkış olarak Windows Uygulama kapsayıcısında çalışan bir *. dll* veya *. exe* dosyası üretir.|
|**/ARM**|Hedef işlemci olarak Gelişmiş RISC Makinesi (ARM) belirtir.<br /><br /> Hiçbir görüntü bit durumu belirtilmemişse, varsayılan olarak **/32bittercih**edilir.|
|**/Base:** `integer`|ImageBase 'i NT isteğe bağlı üst bilgisinde `integer` belirtilen değere ayarlar. Eğer .imagebase IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/Saat**|Belirtilen .il kaynak dosyası için aşağıdaki derleme sürelerini milisaniye cinsinden ölçer ve raporlar:<br /><br /> **Toplam çalıştırma**: İzleyen tüm belirli işlemleri gerçekleştirirken harcanan toplam süre.<br /><br /> **Başlangıç**: Dosya yükleniyor ve açılıyor.<br /><br /> **Md yayma**: Meta veriler yayıcı.<br /><br /> **Ref-def çözümleme**: Dosyadaki tanımlara yapılan başvurular çözümleniyor.<br /><br /> **Cee dosyası oluşturma**: Bellek içinde dosya görüntüsü oluşturuluyor.<br /><br /> **PE dosyasını yazma**: Görüntü bir PE dosyasına yazılıyor.|
|**/Debug** [:**Impl**&#124;**opt**]|Hata ayıklama bilgisi içerir (yerel değişken ve bağımsız değişken adları ve satır numaraları). Bir PDB dosyası oluşturur.<br /><br /> ek değer içermeyen **/Debug** JIT iyileştirmesini devre dışı bırakır ve pdb dosyasından sıra noktalarını kullanır.<br /><br /> **IMPL** JIT iyileştirmesini devre dışı bırakır ve örtük sıra noktaları kullanır.<br /><br /> **Opt** için JIT İyileştirmesi etkinleştirilir ve örtülü sıra noktalarını kullanır.|
|**/dll**|Çıktı olarak bir *. dll* dosyası üretir.|
|**/enc:** `file`|Belirtilen kaynak dosyasından Düzenle ve Devam Et deltaları oluşturur.<br /><br /> Bu bağımsız değişken yalnızca akademik amaçlıdır ve ticari kullanım için desteklenmez.|
|**/exe**|Çıktı olarak bir yürütülebilir dosya oluşturur. Bu varsayılandır.|
|**/Flags:** `integer`|ImageFlags öğesini ortak dil çalışma zamanı üst `integer` bilgisinde belirtilen değere ayarlar. Eğer .corflags IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar. *Tamsayı*için geçerli değerler listesi için bkz. CorHdr. h, COMIMAGE_FLAGS.|
|**/Katlama**|Eşdeğer metot gövdelerini tek bir gövde olarak katlar.|
|/**highentropyva**|Yüksek entropili adres alanı düzenini (ASLR) destekleyen bir çıktı çalıştırılabilir dosyası oluşturur. ( **/APPCONTAINER**için varsayılan.)|
|**/include:** `includePath`|İçinde yer alan `#include`dosyaları aramak için bir yol belirler.|
|**/Itanium**|Hedef işlemci olarak Intel Itanium belirtir.<br /><br /> Hiçbir görüntü bit durumu belirtilmemişse, varsayılan değer **/pe64**' dir.|
|**/Key:** `keyFile`|, `filename` İçinde`keyFile`bulunan özel anahtarı kullanarak güçlü bir imzayla derlenir.|
|**/Key** @`keySource`|`filename` Öğesinde`keySource`oluşturulan özel anahtarı kullanarak güçlü bir imzayla derlenir.|
|**/listeleme**|Standart çıktıda bir listeleme dosyası oluşturur. Eğer bu seçeneği koymazsanız, listeleme dosyası oluşturulmaz.<br /><br /> Bu parametre .NET Framework 2.0 ve sonrasında desteklenmez.|
|**/MDV:** `versionString`|Meta veri sürümü dizesini ayarlar.|
|**/MSV:** `major`.`minor`|Meta veri akışı sürümünü, burada `major` ve `minor` tamsayılar olarak ayarlar.|
|**/nooto Inherit**|Hiçbir temel sınıf belirtilmediğinde <xref:System.Object> varsayılan devralmayı devre dışı bırakır.|
|**/nocorstub**|CORExeMain taslağının oluşturulmasını bastırır.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/output:** `file.ext`|Çıktı dosyası adını ve uzantısını belirtir. Varsayılan olarak, çıktı dosyası adı ilk kaynak dosyasının adıyla aynıdır. Varsayılan uzantı *. exe*' dir. **/DLL** seçeneğini belirtirseniz, varsayılan uzantı *. dll*' dir. **Not:** **/Output**: dosyam. dll belirtildiğinde **/DLL** seçeneği ayarlanmadı. **/DLL**belirtmezseniz, sonuç *Dosyam. dll*adlı yürütülebilir bir dosya olur.|
|**/optimize**|Uzun yönergeleri kısa olarak iyileştirir. Örneğin, `br`. `br.s`|
|**/pe64**|64 bitlik bir görüntü oluşturur (PE32+).<br /><br /> Hedef işlemci belirtilmemişse, varsayılan olur `/itanium`.|
|**/pdb**|Hata ayıklama bilgisi izlemeyi etkinleştirmeden bir PDB dosyası oluşturur.|
|**/quiet**|Sessiz modu belirtir; hiçbir derleme ilerlemesini bildirmez.|
|**/Kaynak:** `file.res`|Elde edilen \* *. exe* veya *. dll* dosyasında belirtilen kaynak dosyasını. res biçiminde içerir. **/Resource** seçeneğiyle yalnızca bir. res dosyası belirtilebilir.|
|**/ssver:** `int`.`int`|NT isteğe bağlı üst bilgisinde alt sistem sürümünü ayarlar. **/APPCONTAINER** ve **/ARM** için en düşük sürüm numarası 6,02 ' dir.|
|**/Stack:** `stackSize`|NT Isteğe bağlı üst bilgisindeki SizeOfStackReserve değerini olarak `stackSize`ayarlar.|
|**/çabapreloc**|Temel yeniden konumlandırmanın gerekmediğini belirtir.|
|**/Subsystem:** `integer`|Alt sistemi, NT isteğe bağlı üst `integer` bilgisinde tarafından belirtilen değere ayarlar. Eğer .subsystem IL yönergesi dosyada belirtiliyorsa, bu komut onu geçersiz kılar. İçin `integer`geçerli değerler listesi için bkz. Winnt. h, IMAGE_SUBSYSTEM.|
|**/x64**|Hedef işlemci olarak bir 64 bitlik AMD işlemci belirtir.<br /><br /> Hiçbir görüntü bit durumu belirtilmemişse, varsayılan değer **/pe64**' dir.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

> [!NOTE]
> *Ilasm. exe* ' nin tüm seçenekleri büyük/küçük harfe duyarlıdır ve ilk üç harf tarafından tanınır. Örneğin, **/Lis** , **/Listeleme** ve **/res**: myresfile. res ile eşdeğerdir. res, **/Resource**: myresfile. res ile eşdeğerdir. Bağımsız değişkenler belirten seçenekler, seçenek ve bağımsız değişken arasında ayıraç olarak ya iki nokta üst üste (:) ya da eşittir işaretini (=) kabul eder. Örneğin, **/output**:*File. ext* , **/output**=*File. ext*ile eşdeğerdir.

## <a name="remarks"></a>Açıklamalar

IL Derleyicisi araç satıcılarına IL oluşturucuları tasarlamaları ve uygulamaları için yardımcı olur. *Ilasm. exe*, araç ve derleyici GELIŞTIRICILERI, PE dosya biçiminde Il yayılmasından ENDIŞE duymadan Il ve meta veri oluşturmaya odaklanabilir.

C# Ve Visual Basic gibi çalışma zamanını hedefleyen diğer derleyicilere benzer şekilde, *Ilasm. exe* ara nesne dosyaları oluşturmaz ve bir PE dosyası oluşturmak için bağlama aşaması gerektirmez.

IL Derleyicisi, çalışma zamanını hedef alan programlama dillerinin tüm varolan meta veri ve IL özelliklerini ifade edebilir. Bu, bu programlama dillerinin herhangi birinde yazılan yönetilen kodun Il derleyiciden yeterince ifade edilmesi ve *Ilasm. exe*ile derlenmesi için izin verir.

> [!NOTE]
> Eğer .il kaynak dosyasının son kod satırında bir boşluk veya satır sonu karakteri yoksa derleme başarısız olabilir.

*Ilasm. exe* ' yi yardımcı aracı olan [*ıldadsm. exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)ile birlikte kullanabilirsiniz. *Ildadsm. exe* IL kodu IÇEREN bir PE dosyası alır ve *Ilasm. exe*' ye giriş olarak uygun bir metin dosyası oluşturur. Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kodu derleyip ve çıkış *ıldadsm. exe*aracılığıyla çalıştırdıktan sonra, elde edilen Il metin dosyası, eksik öznitelikleri eklemek için el ile düzenlenebilir. Ardından, son yürütülebilir bir dosya oluşturmak için bu metin dosyasını *Ilasm. exe* aracılığıyla çalıştırabilirsiniz.

Bu tekniği kullanarak ayrı derleyiciler tarafından üretilen çeşitli PE dosyalarından tek bir PE dosyası oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.

*Ildadsm. exe* ve *Ilasm. exe* ' nin bu birleştirilmiş kullanımını mümkün olduğunca doğru hale getirmek için, varsayılan olarak Assembler, Il kaynaklarınıza yazmış olabileceğiniz (veya başka bir derleyici tarafından yayılan) uzun sürelerle ilgili kısa kodlamalar yerine getirir. Mümkün olan yerlerde kısa kodlamaları yerine koymak için **/optimize** et seçeneğini kullanın.

> [!NOTE]
> *Ildadsm. exe* yalnızca diskteki dosyalar üzerinde çalışır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

Il 'nin dilbilgisini hakkında daha fazla bilgi için, Windows SDK The asmpari. Grammar dosyasına bakın.

## <a name="version-information"></a>Sürüm Bilgileri

4,5 .NET Framework başlayarak, aşağıdakine benzer bir kod kullanarak bir arabirim uygulamasına özel bir öznitelik ekleyebilirsiniz:

```il
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

4,5 .NET Framework başlayarak, aşağıdaki kodda gösterildiği gibi, ham ikili gösterimini kullanarak rastgele bir sıralama Blobu (ikili büyük nesne) belirtebilirsiniz:

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Il 'nin dilbilgisini hakkında daha fazla bilgi için, Windows SDK The asmpari. Grammar dosyasına bakın.

## <a name="examples"></a>Örnekler

Aşağıdaki komut, *MYTESTFILE.Il* Il dosyasını ayrıştırır ve *myTestFile. exe*yürütülebilir dosyasını oluşturur.

```console
ilasm myTestFile
```

Aşağıdaki komut, *MYTESTFILE.Il* Il dosyasını ayrıştırır ve *myTestFile. dll* *. dll* dosyasını oluşturur.

```console
ilasm myTestFile /dll
```

Aşağıdaki komut, *MYTESTFILE.Il* Il dosyasını ayrıştırır ve *. dll* dosyasını *mynewtestfile. dll*olarak oluşturur.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Aşağıdaki kod örneğinde, "Merhaba Dünya!" görüntüleyen son derece basit bir uygulama gösterilmektedir konsoluna gidin. Bu kodu derleyebilir ve ardından [*ıldadsm. exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) aracını kullanarak bir Il dosyası oluşturabilirsiniz.

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

Aşağıdaki IL kod örneği önceki C# kod örneğine karşılık gelir. Bu kodu Il assembler aracını kullanarak bir derlemede derleyebilirsiniz. Hem Il hem C# de kod örnekleri "Merhaba Dünya!" görüntüler konsoluna gidin.

```il
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
- [*Ildadsm. exe* (Il ayırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
- [Yönetilen Yürütme İşlemi](../../standard/managed-execution-process.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

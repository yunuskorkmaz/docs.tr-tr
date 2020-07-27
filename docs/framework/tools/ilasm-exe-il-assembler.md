---
title: Ilasm.exe (IL Derleyici)
description: Il assembler Ilasm.exe kullanmaya başlayın. Bu araç, ara dilden (IL) taşınabilir bir çalıştırılabilir (PE) dosyası oluşturur.
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
ms.openlocfilehash: 1a85b3bf9509ffba6c2331d14196a6bef2bfa080
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166976"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Derleyici)

IL Derleyicisi ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur. (Il hakkında daha fazla bilgi için bkz. [yönetilen yürütme işlemi](../../standard/managed-execution-process.md).) Il 'nin beklenen şekilde yapılıp yapılmayacağını anlamak için Il ve gerekli meta verileri içeren elde edilen yürütülebilir dosyayı çalıştırabilirsiniz.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Söz dizimi

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parametreler

| Bağımsız Değişken | Açıklama |
| -------- | ----------- |
|`filename`|.il kaynak dosyasının adı. Bu dosya meta veri bildirim yönergeleri ve simgesel IL yönergelerinden oluşur. *Ilasm.exe*ile tek bir PE dosyası oluşturmak için birden çok kaynak dosya bağımsız değişkeni sağlanabilir. **Note:** . Il kaynak dosyasındaki son kod satırının sonunda boşluk veya satır sonu karakteri bulunduğundan emin olun.|

| Seçenek | Açıklama |
| ------ | ----------- |
|**/32bittercihli**|32 bit tercih edilen bir görüntü (PE32) oluşturur.|
|**/hizalaması:**`integer`|NT Isteğe bağlı üstbilgisinde dosya hizalamasını belirtilen değere ayarlar `integer` . Eğer .alignment IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/APPCONTAINER**|Çıkış olarak Windows Uygulama kapsayıcısında çalışan bir *. dll* veya *. exe* dosyası üretir.|
|**/ARM**|Hedef işlemci olarak Gelişmiş RISC Makinesi (ARM) belirtir.<br /><br /> Hiçbir görüntü bit durumu belirtilmemişse, varsayılan olarak **/32bittercih**edilir.|
|**/Base:**`integer`|ImageBase 'i `integer` NT Isteğe bağlı üst bilgisinde belirtilen değere ayarlar. Eğer .imagebase IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/Saat**|Belirtilen .il kaynak dosyası için aşağıdaki derleme sürelerini milisaniye cinsinden ölçer ve raporlar:<br /><br /> **Toplam çalıştırma**: izleyen tüm belirli işlemleri gerçekleştirmek için harcanan toplam süre.<br /><br /> **Başlangıç**: dosyayı yükleme ve açma.<br /><br /> **Md 'Yi yayma**: meta verileri yayma.<br /><br /> **Ref-def çözümleme**: dosyadaki tanımlara başvuruları çözümleme.<br /><br /> **Cee dosyası oluşturma**: bellekte dosya görüntüsü oluşturuluyor.<br /><br /> **PE dosyası yazma**: görüntüyü bir pe dosyasına yazma.|
|**/Debug**[:**Impl**&#124;**opt**]|Hata ayıklama bilgisi içerir (yerel değişken ve bağımsız değişken adları ve satır numaraları). Bir PDB dosyası oluşturur.<br /><br /> ek değer içermeyen **/Debug** JIT iyileştirmesini devre dışı bırakır ve pdb dosyasından sıra noktalarını kullanır.<br /><br /> **IMPL** JIT iyileştirmesini devre dışı bırakır ve örtük sıra noktaları kullanır.<br /><br /> **Opt** için JIT İyileştirmesi etkinleştirilir ve örtülü sıra noktalarını kullanır.|
|**/dll**|Çıktı olarak bir *. dll* dosyası üretir.|
|**/enc:**`file`|Belirtilen kaynak dosyasından Düzenle ve Devam Et deltaları oluşturur.<br /><br /> Bu bağımsız değişken yalnızca akademik amaçlıdır ve ticari kullanım için desteklenmez.|
|**/exe**|Çıktı olarak bir yürütülebilir dosya oluşturur. Bu varsayılan seçenektir.|
|**/Flags:**`integer`|ImageFlags öğesini `integer` ortak dil çalışma zamanı üst bilgisinde belirtilen değere ayarlar. Eğer .corflags IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar. *Tamsayı*için geçerli değerler listesi için bkz. CorHdr. h, COMIMAGE_FLAGS.|
|**/Katlama**|Eşdeğer metot gövdelerini tek bir gövde olarak katlar.|
|/**highentropyva**|Yüksek entropili adres alanı düzenini (ASLR) destekleyen bir çıktı çalıştırılabilir dosyası oluşturur. ( **/APPCONTAINER**için varsayılan.)|
|**/include:**`includePath`|İçinde yer alan dosyaları aramak için bir yol belirler `#include` .|
|**/Itanium**|Hedef işlemci olarak Intel Itanium belirtir.<br /><br /> Hiçbir görüntü bit durumu belirtilmemişse, varsayılan değer **/pe64**' dir.|
|**/Key:**`keyFile`|`filename`, İçinde bulunan özel anahtarı kullanarak güçlü bir imzayla derlenir `keyFile` .|
|**/Key** @`keySource`|`filename`Öğesinde oluşturulan özel anahtarı kullanarak güçlü bir imzayla derlenir `keySource` .|
|**/listeleme**|Standart çıktıda bir listeleme dosyası oluşturur. Eğer bu seçeneği koymazsanız, listeleme dosyası oluşturulmaz.<br /><br /> Bu parametre .NET Framework 2.0 ve sonrasında desteklenmez.|
|**/MDV:**`versionString`|Meta veri sürümü dizesini ayarlar.|
|**/MSV:** `major` .`minor`|Meta veri akışı sürümünü, burada `major` ve tamsayılar olarak ayarlar `minor` .|
|**/nooto Inherit**|Hiçbir temel sınıf belirtilmediğinde varsayılan devralmayı devre dışı bırakır <xref:System.Object> .|
|**/nocorstub**|CORExeMain taslağının oluşturulmasını bastırır.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/output:**`file.ext`|Çıktı dosyası adını ve uzantısını belirtir. Varsayılan olarak, çıktı dosyası adı ilk kaynak dosyasının adıyla aynıdır. Varsayılan uzantı *. exe*' dir. **/DLL** seçeneğini belirtirseniz, varsayılan uzantı *. dll*' dir. **Note:** **/Output**:myfile.dll belirtildiğinde **/DLL** seçeneği ayarlanmadı. **/DLL**belirtmezseniz, sonuç *myfile.dll*adlı yürütülebilir bir dosya olur.|
|**/optimize**|Uzun yönergeleri kısa olarak iyileştirir. Örneğin, `br` `br.s` .|
|**/pe64**|64 bitlik bir görüntü oluşturur (PE32+).<br /><br /> Hedef işlemci belirtilmemişse, varsayılan olur `/itanium` .|
|**/pdb**|Hata ayıklama bilgisi izlemeyi etkinleştirmeden bir PDB dosyası oluşturur.|
|**/**|Sessiz modu belirtir; hiçbir derleme ilerlemesini bildirmez.|
|**/Kaynak:**`file.res`|\*Elde edilen *. exe* veya *. dll* dosyasında belirtilen kaynak dosyasını. res biçiminde içerir. **/Resource** seçeneğiyle yalnızca bir. res dosyası belirtilebilir.|
|**/ssver:** `int` .`int`|NT isteğe bağlı üst bilgisinde alt sistem sürümünü ayarlar. **/APPCONTAINER** ve **/ARM** için en düşük sürüm numarası 6,02 ' dir.|
|**/Stack:**`stackSize`|NT Isteğe bağlı üst bilgisindeki SizeOfStackReserve değerini olarak ayarlar `stackSize` .|
|**/çabapreloc**|Temel yeniden konumlandırmanın gerekmediğini belirtir.|
|**/Subsystem:**`integer`|Alt sistemi `integer` , NT Isteğe bağlı üst bilgisinde tarafından belirtilen değere ayarlar. Eğer .subsystem IL yönergesi dosyada belirtiliyorsa, bu komut onu geçersiz kılar. İçin geçerli değerler listesi için bkz. Winnt. h, IMAGE_SUBSYSTEM `integer` .|
|**/x64**|Hedef işlemci olarak bir 64 bitlik AMD işlemci belirtir.<br /><br /> Hiçbir görüntü bit durumu belirtilmemişse, varsayılan değer **/pe64**' dir.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

> [!NOTE]
> Tüm *Ilasm.exe* seçenekleri büyük/küçük harfe duyarlıdır ve ilk üç harf tarafından tanınır. Örneğin, **/Lis** , **/Listeleme** ve **/res**: myresfile. res ile eşdeğerdir. res, **/Resource**: myresfile. res ile eşdeğerdir. Bağımsız değişkenleri belirten seçenekler iki nokta işaretini kabul eder (:) ya da bir eşittir işareti (=), seçeneği ve bağımsız değişkeni arasında ayırıcı olarak. Örneğin, **/output**:*File. ext* , **/output** = *File. ext*ile eşdeğerdir.

## <a name="remarks"></a>Açıklamalar

IL Derleyicisi araç satıcılarına IL oluşturucuları tasarlamaları ve uygulamaları için yardımcı olur. *Ilasm.exe*, araç ve derleyici GELIŞTIRICILERI, PE dosya biçiminde Il yayılmasından ENDIŞE duymadan Il ve meta veri oluşturmaya odaklanabilir.

C# ve Visual Basic gibi çalışma zamanını hedefleyen diğer derleyicilere benzer şekilde, *Ilasm.exe* ara nesne dosyalarını oluşturmaz ve bir PE dosyası oluşturmak için bağlama aşamasına gerek yoktur.

IL Derleyicisi, çalışma zamanını hedef alan programlama dillerinin tüm varolan meta veri ve IL özelliklerini ifade edebilir. Bu, bu programlama dillerinde yazılan yönetilen kodun Il derleyiciden yeterince ifade edilmesi ve *Ilasm.exe*ile derlenmesi için izin verir.

> [!NOTE]
> Eğer .il kaynak dosyasının son kod satırında bir boşluk veya satır sonu karakteri yoksa derleme başarısız olabilir.

[*Ildasm.exe*](ildasm-exe-il-disassembler.md)yardımcı aracı ile birlikte *Ilasm.exe* kullanabilirsiniz. *Ildasm.exe* IL kodu IÇEREN bir PE dosyasını alır ve *Ilasm.exe*giriş olarak uygun bir metin dosyası oluşturur. Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kodu derleyip ve çıktıyı *Ildasm.exe*aracılığıyla çalıştırdıktan sonra, elde edilen Il metin dosyası, eksik öznitelikleri eklemek için el ile düzenlenebilir. Ardından, son yürütülebilir bir dosya oluşturmak için bu metin dosyasını *Ilasm.exe* aracılığıyla çalıştırabilirsiniz.

Bu tekniği kullanarak ayrı derleyiciler tarafından üretilen çeşitli PE dosyalarından tek bir PE dosyası oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.

Bu *Ildasm.exe* ve *Ilasm.exe* mümkün olduğunca doğru şekilde kullanmasını sağlamak için, varsayılan olarak Assembler, Il kaynaklarınıza yazmış olabileceğiniz (veya başka bir derleyici tarafından yayılan) uzun sürelerle ilgili kısa kodlamalar yerine getirir. Mümkün olan yerlerde kısa kodlamaları yerine koymak için **/optimize** et seçeneğini kullanın.

> [!NOTE]
> *Ildasm.exe* yalnızca diskteki dosyalar üzerinde çalışır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

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

Aşağıdaki komut, *MYTESTFILE.Il* Il dosyasını ayrıştırır ve çalıştırılabilir *myTestFile.exe*üretir.

```console
ilasm myTestFile
```

Aşağıdaki komut, *MYTESTFILE.Il* Il dosyasını ayrıştırır ve *. dll* dosyasını *myTestFile.dll*üretir.

```console
ilasm myTestFile /dll
```

Aşağıdaki komut, *MYTESTFILE.Il* Il dosyasını ayrıştırır ve *. dll* dosyasını *myNewTestFile.dll*üretir.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Aşağıdaki kod örneğinde, "Merhaba Dünya!" görüntüleyen son derece basit bir uygulama gösterilmektedir metnini görüntülemelidir. Bu kodu derleyebilir ve ardından [*Ildasm.exe*](ildasm-exe-il-disassembler.md) ARACıNı kullanarak Il dosyası oluşturabilirsiniz.

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

Aşağıdaki IL kod örneği önceki C# kod örneğine karşılık gelir. Bu kodu Il assembler aracını kullanarak bir derlemede derleyebilirsiniz. Hem Il hem de C# kod örnekleri "Merhaba Dünya!" görüntüler metnini görüntülemelidir.

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

- [Araçlar](index.md)
- [*Ildasm.exe* (Il ayırıcı)](ildasm-exe-il-disassembler.md)
- [Yönetilen yürütme Işlemi](../../standard/managed-execution-process.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)

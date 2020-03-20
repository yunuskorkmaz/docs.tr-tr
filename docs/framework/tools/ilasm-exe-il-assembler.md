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
ms.openlocfilehash: cb995e78e534048043886070536ef0dd0a45c057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105099"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Derleyici)

IL Derleyicisi ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur. (IL hakkında daha fazla bilgi için yönetilen [yürütme işlemi](../../standard/managed-execution-process.md)ne bakın.) IL'nin beklendiği gibi çalışıp çalışmadığını belirlemek için IL ve gerekli meta verileri içeren ortaya çıkan yürütülebilir çalıştırılabilir çalıştırabilirsiniz.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parametreler

| Bağımsız Değişken | Açıklama |
| -------- | ----------- |
|`filename`|.il kaynak dosyasının adı. Bu dosya meta veri bildirim yönergeleri ve simgesel IL yönergelerinden oluşur. Birden çok kaynak dosya bağımsız değişkenleri *Ilasm.exe*ile tek bir PE dosyası üretmek için sağlanabilir. **Not:** .il kaynak dosyasındaki son kod satırının beyaz boşluk veya satır sonu karakterinin gerisinde olduğundan emin olun.|

| Seçenek | Açıklama |
| ------ | ----------- |
|**/32bittercih**|32 bit tercih edilen bir görüntü (PE32) oluşturur.|
|**/hizalama:**`integer`|FileAlignment'ı NT `integer` İsteğe Bağlı üstbilgide belirtilen değere ayarlar. Eğer .alignment IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/appcontainer**|Çıktı olarak Windows uygulama kapsayıcısında çalışan bir *.dll* veya *.exe* dosyası üretir.|
|**/kol**|Hedef işlemci olarak Gelişmiş RISC Makinesi (ARM) belirtir.<br /><br /> Görüntü bitliği belirtilmemişse, varsayılan **değer /32bitpreferred.**|
|**/taban:**`integer`|ImageBase'i NT `integer` İsteğe Bağlı üstbilgide belirtilen değere ayarlar. Eğer .imagebase IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/saat**|Belirtilen .il kaynak dosyası için aşağıdaki derleme sürelerini milisaniye cinsinden ölçer ve raporlar:<br /><br /> **Toplam Çalıştırma**: Takip eden tüm belirli işlemleri gerçekleştirmek için harcanan toplam süre.<br /><br /> **Başlangıç**: Dosyayı yükleme ve açma.<br /><br /> **Yayan MD**: Meta veri yayan.<br /><br /> **Ref to Def Resolution**: Dosyadaki tanımlara yapılan başvuruların çözülmesi.<br /><br /> **CEE Dosya Oluşturma**: Bellekte dosya görüntüsü oluşturma.<br /><br /> **PE Dosya Yazma**: Resmin PE dosyasına yazılması.|
|**/hata ayıklama**[:**IMPL**&#124;**OPT**]|Hata ayıklama bilgisi içerir (yerel değişken ve bağımsız değişken adları ve satır numaraları). Bir PDB dosyası oluşturur.<br /><br /> **/debug** hiçbir ek değeri ile JIT optimizasyonu devre dışı ve PDB dosyasından sıra noktaları kullanır.<br /><br /> **IMPL,** JIT optimizasyonunu devre dışı kılabilir ve örtük sıra noktalarını kullanır.<br /><br /> **OPT,** JIT optimizasyonunu sağlar ve örtük sıra noktalarını kullanır.|
|**/dll**|Çıktı olarak *bir .dll* dosyası üretir.|
|**/enc:**`file`|Belirtilen kaynak dosyasından Düzenle ve Devam Et deltaları oluşturur.<br /><br /> Bu bağımsız değişken yalnızca akademik amaçlıdır ve ticari kullanım için desteklenmez.|
|**/exe**|Çıktı olarak bir yürütülebilir dosya oluşturur. Bu varsayılandır.|
|**/bayraklar:**`integer`|ImageFlags'i ortak dil `integer` çalışma zamanı üstbilgisinde belirtilen değere ayarlar. Eğer .corflags IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar. Tamsayı için geçerli değerlerin listesi için COMIMAGE_FLAGS *integer*CorHdr.h'ye bakın.|
|**/kat**|Eşdeğer metot gövdelerini tek bir gövde olarak katlar.|
|/**highentropyva**|Yüksek entropili adres alanı düzenini (ASLR) destekleyen bir çıktı çalıştırılabilir dosyası oluşturur. (Varsayılan **/appcontainer**.)|
|**/dahil:**`includePath`|'ye `#include`dahil olan dosyaları aramak için bir yol ayarlar.|
|**/itanium**|Hedef işlemci olarak Intel Itanium belirtir.<br /><br /> Görüntü bitliği belirtilmemişse, varsayılan değer **/pe64'dür.**|
|**/tuşu:**`keyFile`|'de `filename` `keyFile`bulunan özel anahtarı kullanarak güçlü bir imza ile derler.|
|**/tuşu:** @`keySource`|Üretilen `filename` özel anahtarı kullanarak güçlü bir `keySource`imza ile derler.|
|**/listeleme**|Standart çıktıda bir listeleme dosyası oluşturur. Eğer bu seçeneği koymazsanız, listeleme dosyası oluşturulmaz.<br /><br /> Bu parametre .NET Framework 2.0 ve sonrasında desteklenmez.|
|**/mdv:**`versionString`|Meta veri sürümü dizesini ayarlar.|
|**/msv:** `major`.`minor`|Meta veri akışı sürümünü, `major` `minor` nerede ve tamsayılar olarak ayarlar.|
|**/noautoinherit**|Temel sınıf belirtilmediğinde varsayılan <xref:System.Object> kalıtım devre dışı bırakır.|
|**/nocorstub**|CORExeMain taslağının oluşturulmasını bastırır.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/çıkış:**`file.ext`|Çıktı dosyası adını ve uzantısını belirtir. Varsayılan olarak, çıktı dosyası adı ilk kaynak dosyasının adıyla aynıdır. Varsayılan uzantı *.exe'dir.* **/dll** seçeneğini belirtirseniz, varsayılan uzantı *.dll'dir.* **Not:** Belirtilmesi **/output**:myfile.dll **/dll** seçeneğini ayarlamaz. **/dll**belirtmezseniz, sonuç *myfile.dll*adlı yürütülebilir bir dosya olacaktır.|
|**/optimize etmek**|Uzun yönergeleri kısa olarak iyileştirir. Örneğin, `br` `br.s`.|
|**/pe64**|64 bitlik bir görüntü oluşturur (PE32+).<br /><br /> Hedef işlemci belirtilmemişse, `/itanium`varsayılan değer.|
|**/pdb**|Hata ayıklama bilgisi izlemeyi etkinleştirmeden bir PDB dosyası oluşturur.|
|**/sessiz**|Sessiz modu belirtir; hiçbir derleme ilerlemesini bildirmez.|
|**/kaynak:**`file.res`|Belirtilen kaynak dosyasını \*.res biçiminde ortaya çıkan *.exe* veya *.dll* dosyasında içerir. Sadece bir .res dosyası **/kaynak** seçeneği ile belirtilebilir.|
|**/ssver:** `int`.`int`|NT isteğe bağlı üst bilgisinde alt sistem sürümünü ayarlar. **/appcontainer** ve **/arm** için minimum sürüm numarası 6.02'dir.|
|**/yığın:**`stackSize`|NT İsteğe Bağlı üstbilgideki SizeOfStackReserve değerini `stackSize`ayarlar.|
|**/stripreloc**|Temel yeniden konumlandırmanın gerekmediğini belirtir.|
|**/alt sistem:**`integer`|Alt sistemi NT İsteğe Bağlı `integer` üstbilgide belirtilen değere ayarlar. Eğer .subsystem IL yönergesi dosyada belirtiliyorsa, bu komut onu geçersiz kılar. Winnt.h için geçerli değerlerin listesi için `integer`IMAGE_SUBSYSTEM bakın.|
|**/x64**|Hedef işlemci olarak bir 64 bitlik AMD işlemci belirtir.<br /><br /> Görüntü bitliği belirtilmemişse, varsayılan değer **/pe64'dür.**|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

> [!NOTE]
> *Ilasm.exe* için tüm seçenekler büyük/küçük harf duyarsız ve ilk üç harf tarafından tanınan. Örneğin, **/lis** **/listing** ve **/res**:myresfile.res eşdeğerdir **/kaynak**:myresfile.res. Bağımsız değişkenleri belirten seçenekler iki nokta üst üste kabul eder (:) veya seçenek ve bağımsız değişken arasındaki ayırıcı olarak eşit bir işaret (=) olur. Örneğin, **/output**:*file.ext* **/output**=*file.ext'e*eşdeğerdir.

## <a name="remarks"></a>Açıklamalar

IL Derleyicisi araç satıcılarına IL oluşturucuları tasarlamaları ve uygulamaları için yardımcı olur. *Ilasm.exe*kullanarak, araç ve derleyici geliştiriciler IL ve meta veri üretimi pe dosya biçiminde IL yayan ile ilgili olmadan konsantre olabilir.

C# ve Visual Basic gibi çalışma süresini hedefleyen diğer derleyicilere benzer şekilde, *Ilasm.exe* ara nesne dosyaları üretmez ve PE dosyası oluşturmak için bağlama aşaması gerektirmez.

IL Derleyicisi, çalışma zamanını hedef alan programlama dillerinin tüm varolan meta veri ve IL özelliklerini ifade edebilir. Bu, bu programlama dillerinden herhangi birinde yazılmış yönetilen kodun IL Assembler'da yeterince ifade edilmesine ve *Ilasm.exe*ile derlenmesine olanak sağlar.

> [!NOTE]
> Eğer .il kaynak dosyasının son kod satırında bir boşluk veya satır sonu karakteri yoksa derleme başarısız olabilir.

Onun arkadaşı aracı, [*Ildasm.exe*](ildasm-exe-il-disassembler.md)ile birlikte *Ilasm.exe* kullanabilirsiniz. *Ildasm.exe* IL kodu içeren bir PE dosyası alır ve *Ilasm.exe*girişi olarak uygun bir metin dosyası oluşturur. Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kodu derleyip çıktıyı *Ildasm.exe*üzerinden çalıştırdıktan sonra, ortaya çıkan IL metin dosyası eksik öznitelikleri eklemek için elle düzenlenebilir. Daha sonra son yürütülebilir dosyayı oluşturmak için bu metin dosyasını *Ilasm.exe* üzerinden çalıştırabilirsiniz.

Bu tekniği kullanarak ayrı derleyiciler tarafından üretilen çeşitli PE dosyalarından tek bir PE dosyası oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.

*Ildasm.exe* ve *Ilasm.exe'nin* bu birleşik kullanımını mümkün olduğunca doğru hale getirmek için, varsayılan olarak assembler IL kaynaklarınızda yazmış olabileceğiniz (veya başka bir derleyici tarafından yayılmış olabilecek) uzun kodlamaları yerine almaz. Mümkün olan her yerde kısa kodlamaların yerine **/optimize** seçeneğini kullanın.

> [!NOTE]
> *Ildasm.exe* sadece diskteki dosyalarda çalışır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

IL dilbilgisi hakkında daha fazla bilgi için Windows SDK'daki asmparse.grammar dosyasına bakın.

## <a name="version-information"></a>Sürüm Bilgileri

.NET Framework 4.5 ile başlayarak, aşağıdakilere benzer bir kod kullanarak arabirim uygulamasına özel bir öznitelik ekleyebilirsiniz:

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

.NET Framework 4.5 ile başlayarak, aşağıdaki kodda gösterildiği gibi ham ikili gösterimini kullanarak rasgele bir mareşal BLOB (ikili büyük nesne) belirtebilirsiniz:

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

IL dilbilgisi hakkında daha fazla bilgi için Windows SDK'daki asmparse.grammar dosyasına bakın.

## <a name="examples"></a>Örnekler

Aşağıdaki komut IL dosyasını *myTestFile.il* toplar ve çalıştırılabilir *myTestFile.exe'yi*üretir.

```console
ilasm myTestFile
```

Aşağıdaki komut IL dosyasını *myTestFile.il* toplar ve *.dll* dosya *myTestFile.dll*üretir.

```console
ilasm myTestFile /dll
```

Aşağıdaki komut IL dosyasını *myTestFile.il* toplar ve *.dll* dosya *myNewTestFile.dll*üretir.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Aşağıdaki kod örneği "Merhaba Dünya!" gösteren son derece basit bir uygulama gösterir. metnini görüntülemelidir. Bu kodu derleyebilir ve il dosyası oluşturmak için [*Ildasm.exe*](ildasm-exe-il-disassembler.md) aracını kullanabilirsiniz.

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

Aşağıdaki IL kod örneği önceki C# kod örneğine karşılık gelir. Bu kodu IL Assembler aracını kullanarak bir derlemeye ekleyebilirsiniz. Hem IL hem de C# kod örnekleri "Hello World!" metnini görüntülemelidir.

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
- [*Ildasm.exe* (IL Desassembler)](ildasm-exe-il-disassembler.md)
- [Yönetilen Yürütme İşlemi](../../standard/managed-execution-process.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)

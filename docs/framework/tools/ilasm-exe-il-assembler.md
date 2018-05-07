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
ms.openlocfilehash: 4009fe4910af81c685ee015c7801b040a90c25aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Derleyici)

IL Derleyicisi ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur. (IL hakkında daha fazla bilgi için bkz: [yönetilen yürütme işlemi](../../../docs/standard/managed-execution-process.md).) IL ve gereken meta veriyi içeren elde edilen çalıştırılabilir dosyayı çalıştırarak IL'in beklendiği gibi çalışıp çalışmadığını belirleyebilirsiniz.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
ilasm [options] filename [[options]filename...]
```

#### <a name="parameters"></a>Parametreler

| Bağımsız Değişken | Açıklama |
| -------- | ----------- |
|`filename`|.il kaynak dosyasının adı. Bu dosya meta veri bildirim yönergeleri ve simgesel IL yönergelerinden oluşur. Birden çok kaynak dosya bağımsız değişkenleri ile tek bir PE dosyası üretmek için sağlanan *Ilasm.exe*. **Not:** kodunu .il kaynak dosyasında son satırının sonunda boşluk veya satır sonu karakteri sahip olduğundan emin olun.|

| Seçenek | Açıklama |
| ------ | ----------- |
|**/32bitpreferred**|32 bit tercih edilen bir görüntü (PE32) oluşturur.|
|**/ alignment:** `integer`|FileAlignment tarafından belirtilen değere ayarlar `integer` NT isteğe bağlı üstbilgisinde. Eğer .alignment IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/appcontainer**|Üreten bir *.dll* veya *.exe* Windows uygulama kapsayıcısında çıktı olarak çalışan dosya.|
|**/ARM**|Hedef işlemci olarak Gelişmiş RISC Makinesi (ARM) belirtir.<br /><br /> Hiçbir görüntü verileri belirtilmezse, varsayılan değer **/32bitpreferred**.|
|**/Base:** `integer`|ImageBase tarafından belirtilen değere ayarlar `integer` NT isteğe bağlı üstbilgisinde. Eğer .imagebase IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.|
|**/Clock**|Belirtilen .il kaynak dosyası için aşağıdaki derleme sürelerini milisaniye cinsinden ölçer ve raporlar:<br /><br /> **Toplam çalışma**: harcanan toplam zamanı izleyin belirli işlemlerini gerçekleştirme.<br /><br /> **Başlangıç**: yükleme ve dosyayı açma.<br /><br /> **MD yayma**: meta veri yayma.<br /><br /> **Ref Def çözümleme**: dosya tanımlarında başvuruları çözümleme.<br /><br /> **CEE dosyası oluşturma**: bellekte dosya görüntüsü oluşturuluyor.<br /><br /> **PE dosya yazma**: görüntünün PE dosyaya yazma.|
|**/ debug**[:**IMPL**&#124;**OPT**]|Hata ayıklama bilgisi içerir (yerel değişken ve bağımsız değişken adları ve satır numaraları). Bir PDB dosyası oluşturur.<br /><br /> **/ debug** JIT iyileştirmesi hiçbir ek değerle devre dışı bırakır ve sıralama noktaları PDB dosyasından kullanır.<br /><br /> **IMPL** JIT iyileştirmesi devre dışı bırakır ve örtük sıralama noktaları kullanır.<br /><br /> **OPT** JIT iyileştirmesi sağlar ve örtük sıralama noktaları kullanır.|
|**/ dll**|Üreten bir *.dll* çıktı olarak dosya.|
|**/ENC:** `file`|Belirtilen kaynak dosyasından Düzenle ve Devam Et deltaları oluşturur.<br /><br /> Bu bağımsız değişken yalnızca akademik amaçlıdır ve ticari kullanım için desteklenmez.|
|**/ exe**|Çıktı olarak bir yürütülebilir dosya oluşturur. Bu varsayılandır.|
|**/ Flags:** `integer`|ImageFlags tarafından belirtilen değere ayarlar `integer` ortak dil çalışma zamanı üst bilgisindeki. Eğer .corflags IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar. CorHdr.h, COMIMAGE_FLAGS için geçerli değerler listesi için bkz: *tamsayı*.|
|**/fold**|Eşdeğer metot gövdelerini tek bir gövde olarak katlar.|
|/**hıghentropyva**|Yüksek entropili adres alanı düzenini (ASLR) destekleyen bir çıktı çalıştırılabilir dosyası oluşturur. (İçin varsayılan **/appcontainer**.)|
|**/ içerir:** `includePath`|Bulunan dosyalar aramak için bir yol ayarlar `#include`.|
|**/itanium**|Hedef işlemci olarak Intel Itanium belirtir.<br /><br /> Hiçbir görüntü verileri belirtilmezse, varsayılan değer **/pe64**.|
|**/Key:** `keyFile`|Derlenen `filename` bulunan özel anahtar kullanarak güçlü bir imza ile `keyFile`.|
|**/Key:** @`keySource`|Derlenen `filename` üretilen en güçlü bir imza ile özel anahtarını kullanarak `keySource`.|
|**/ listeleme**|Standart çıktıda bir listeleme dosyası oluşturur. Eğer bu seçeneği koymazsanız, listeleme dosyası oluşturulmaz.<br /><br /> Bu parametre .NET Framework 2.0 ve sonrasında desteklenmez.|
|**/MDV:** `versionString`|Meta veri sürümü dizesini ayarlar.|
|**/msv:** `major`.`minor`|Meta veri akışı sürümü ayarlar nerede `major` ve `minor` tamsayı olduğunu.|
|**/noautoinherit**|Devre dışı bırakır varsayılan devralmadan <xref:System.Object> hiçbir temel sınıf belirtildiğinde.|
|**/nocorstub**|CORExeMain taslağının oluşturulmasını bastırır.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/ Output:** `file.ext`|Çıktı dosyası adını ve uzantısını belirtir. Varsayılan olarak, çıktı dosyası adı ilk kaynak dosyasının adıyla aynıdır. Varsayılan uzantısı *.exe*. Belirtirseniz **/dll** seçeneği, varsayılan uzantısıdır *.dll*. **Not:** belirtme **/çıkış**: dosyam.dll ayarlı değil **/dll** seçeneği. Belirtmezseniz, **/dll**, sonucu adlı bir yürütülebilir dosya olacaktır *dosyam.dll*.|
|**/optimize**|Uzun yönergeleri kısa olarak iyileştirir. Örneğin, `br` için `br.s`.|
|**/pe64**|64 bitlik bir görüntü oluşturur (PE32+).<br /><br /> Hiçbir hedef işlemci belirtilmezse, varsayılan değer `/itanium`.|
|**/ pdb**|Hata ayıklama bilgisi izlemeyi etkinleştirmeden bir PDB dosyası oluşturur.|
|**/quiet**|Sessiz modu belirtir; hiçbir derleme ilerlemesini bildirmez.|
|**/ Resource:** `file.res`|Belirtilen kaynak dosyası içeren \*elde edilen içinde .res biçimi *.exe* veya *.dll* dosya. Yalnızca bir .res dosyası ile belirtilebilir **/Resource** seçeneği.|
|**/ssver:** `int`.`int`|NT isteğe bağlı üst bilgisinde alt sistem sürümünü ayarlar. İçin **/appcontainer** ve **/arm** 6.02 en düşük sürüm numarasıdır.|
|**/Stack:** `stackSize`|NT isteğe bağlı üstbilgi SizeOfStackReserve değeri ayarlar `stackSize`.|
|**/stripreloc**|Temel yeniden konumlandırmanın gerekmediğini belirtir.|
|**/Subsystem:** `integer`|Alt sistemi tarafından belirtilen değere ayarlar `integer` NT isteğe bağlı üstbilgisinde. Eğer .subsystem IL yönergesi dosyada belirtiliyorsa, bu komut onu geçersiz kılar. Winnt.h, IMAGE_SUBSYSTEM için geçerli değerler listesi için bkz: `integer`.|
|**/x64**|Hedef işlemci olarak bir 64 bitlik AMD işlemci belirtir.<br /><br /> Hiçbir görüntü verileri belirtilmezse, varsayılan değer **/pe64**.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

> [!NOTE]
> Tüm seçenekler için *Ilasm.exe* büyük küçük harf duyarsız ve ilk üç harf tarafından tanınan. Örneğin, **/lis** eşdeğerdir **/listeleme** ve **/res**: myresfile.res eşdeğerdir **/Resource**: myresfile.res. Bağımsız değişkenler belirten seçenekler, seçenek ve bağımsız değişken arasında ayıraç olarak ya iki nokta üst üste (:) ya da eşittir işaretini (=) kabul eder. Örneğin, **/çıkış**:*file.ext* eşdeğerdir **/çıkış**=*file.ext*.

## <a name="remarks"></a>Açıklamalar

IL Derleyicisi araç satıcılarına IL oluşturucuları tasarlamaları ve uygulamaları için yardımcı olur. Kullanarak *Ilasm.exe*, aracı ve derleyici geliştiricileri yoğunlaşabilirsiniz üzerinde IL ve meta veri oluşturma IL PE dosya biçimi'nde yayma ile ilgili olmadan.

C# ve Visual Basic gibi çalışma zamanı hedef diğer derleyiciler benzer *Ilasm.exe* Ara nesne dosyaları üretmez ve bir PE dosyası oluşturmak için bir bağlama aşama gerektirmez.

IL Derleyicisi, çalışma zamanını hedef alan programlama dillerinin tüm varolan meta veri ve IL özelliklerini ifade edebilir. Böylece, herhangi bir IL derleyici yeterli ifade bu programlama dillerini yazılır ve ile derlenmiş yönetilen kod *Ilasm.exe*.

> [!NOTE]
> Eğer .il kaynak dosyasının son kod satırında bir boşluk veya satır sonu karakteri yoksa derleme başarısız olabilir.

Kullanabileceğiniz *Ilasm.exe* kendi yardımcı aracı ile birlikte [ *Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). *Ildasm.exe* alır giriş IL kodu içerir ve bir metin dosyası olarak uygun oluşturan bir PE dosyası *Ilasm.exe*. Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır. Kod derleme ve çıktı çalıştıran sonra *Ildasm.exe*, el ile düzenleyebilirsiniz eksik öznitelikler eklemek için sonuçta elde edilen IL metin dosyası olabilir. Sonra bu metin dosyasını çalıştırabilirsiniz *Ilasm.exe* son bir yürütülebilir dosya oluşturmak için.

Bu tekniği kullanarak ayrı derleyiciler tarafından üretilen çeşitli PE dosyalarından tek bir PE dosyası oluşturabilirsiniz.

> [!NOTE]
> Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.

Bunu yapmak için kullanımını birleştirilmiş *Ildasm.exe* ve *Ilasm.exe* varsayılan olarak, mümkün olduğunca doğru assembler yazdığınız IL kaynaklarınızı uzun olanlar için kısa Kodlamalar yerine değil (veya başka bir derleyici tarafından yayınlaması). Kullanım **/ optimize** mümkün olduğunda kısa Kodlamalar yerine seçeneği.

> [!NOTE]
> *Ildasm.exe* yalnızca disk dosyaları çalıştırır. Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.

IL dilbilgisi hakkında daha fazla bilgi için bkz: asmparse.grammar dosyasında [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="version-information"></a>Sürüm Bilgileri

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], aşağıdakine benzer bir kod kullanarak bir arabirim uygulaması için özel bir öznitelik ekleyebilirsiniz:

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

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], size rastgele bir sıralama BLOB (ikili büyük nesne) kendi ham ikili gösterim kullanarak aşağıdaki kodda gösterildiği gibi belirtebilirsiniz:

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

IL dilbilgisi hakkında daha fazla bilgi için bkz: asmparse.grammar dosyasında [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="examples"></a>Örnekler

Aşağıdaki komutu IL dosyasını derler *myTestFile.il* ve yürütülebilir üretir *myTestFile.exe*.

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

Aşağıdaki kod örneğinde "Hello World!" görüntüler oldukça basit bir uygulama gösterir konsola. Bu kodu derleyin ve ardından [ *Ildasm.exe* ](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) aracı bir IL dosyası oluşturun.

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

Aşağıdaki IL kod örneği önceki C# kod örneğine karşılık gelir. Bu kod IL derleyici aracını kullanarak bir derlemeye derleyebilirsiniz. "Hello World!" IL hem C# kod örnekleri görüntüle konsola.

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

[Araçlar](../../../docs/framework/tools/index.md)  
[*Ildasm.exe* (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
[Yönetilen Yürütme İşlemi](../../../docs/standard/managed-execution-process.md)  
[Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

---
title: 'Nasıl yapılı: Derleme içeriğini görüntüleme'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187382"
---
# <a name="how-to-view-assembly-contents"></a>Nasıl yapılı: Derleme içeriğini görüntüleme

Bir dosyada Microsoft ara dili (MSIL) bilgilerini görüntülemek için [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz. İncelenen dosya bir derleme ise, bu bilgiler derlemenin özniteliklerini ve diğer modüllere ve derlemelere yapılan başvuruları içerebilir. Bu bilgiler, bir dosyanın derleme mi yoksa derlemenin bir parçası mı olduğunu ve dosyanın diğer modüllere veya derlemelere başvurup göndermeler göndermediğini belirlemede yararlı olabilir.

*Ildasm.exe*kullanarak bir derlemenin içeriğini görüntülemek için komut istemine **ildasm \<derleme adı>** girin. Örneğin, aşağıdaki komut *Hello.exe* derlemesini söker.

```cmd
ildasm Hello.exe
```

Derleme bildirimi bilgilerini görüntülemek için, MSIL Sökme penceresindeki **Manifest** simgesini çift tıklatın.

## <a name="example"></a>Örnek

Aşağıdaki örnek temel bir "Hello World" programı ile başlar. Programı derledikten *sonra, Hello.exe* derlemesini sökmek ve derleme bildirimini görüntülemek için *Ildasm.exe'yi* kullanın.

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

*Hello.exe* derlemesinde *ildasm.exe* komutunu çalıştırmak ve MSIL Desassembler **penceresindeki Manifest** simgesine çift tıklayarak aşağıdaki çıktıyı üretir:

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

Aşağıdaki tabloda, örnekte kullanılan *Hello.exe* derlemesinin derleme bildirimindeki her bir yönerge açıklanmaktadır:

|Yönergesi|Açıklama|
|---------------|-----------------|
|**.assembly extern \<montaj adı>**|Geçerli modül tarafından başvurulan öğeleri içeren başka bir derleme `mscorlib`belirtir (bu örnekte).|
|**.publickeytoken \<belirteci>**|Başvurulan derlemenin gerçek anahtarının belirteci.|
|**.ver \<sürüm numarası>**|Başvurulan derlemenin sürüm numarasını belirtir.|
|**.montaj \<montaj adı>**|Derleme adını belirtir.|
|**.hash \<algoritmainin int32 değeri>**|Kullanılan karma algoritmayı belirtir.|
|**.ver \<sürüm numarası>**|Derlemenin sürüm numarasını belirtir.|
|**.module \<dosya adı>**|Montajı oluşturan modüllerin adını belirtir. Bu örnekte, derleme yalnızca bir dosyadan oluşur.|
|**.alt \<sistem değeri>**|Program için gerekli olan uygulama ortamını belirtir. Bu örnekte, 3 değeri bu yürütülebilir bir konsoldan çalıştırılır gösterir.|
|**.corflags**|Şu anda meta verilerde ayrılmış bir alan.|

Derleme bildirimi, derlemenin içeriğine bağlı olarak bir dizi farklı yönerge içerebilir. Derleme bildirimindeki yönergelerin kapsamlı bir listesi için, ecma belgelerine, özellikle "Bölüm II: Meta veri tanımı ve anlam bilimi" ve "Bölüm III: CIL Yönerge Seti"ne bakın:

- [ECMA C# ve Ortak Dil Altyapı standartları](../components.md#applicable-standards)
- [Standart ECMA-335 - Ortak Dil Altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Etki Alanları ve derlemeler](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Uygulama etki alanları ve derlemeler nasıl konu edilir](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (IL Ayrıştırıcı)](../../framework/tools/ildasm-exe-il-disassembler.md)

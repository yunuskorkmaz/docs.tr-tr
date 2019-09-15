---
title: -moduleassemblyname (C# derleyici seçeneği)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 7562c0609d61b2388f5063bc480a4dfc715155db
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970082"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname (C# derleyici seçeneği)
Genel olmayan türleri bir. netmodule 'nin erişebileceği bir derlemeyi belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
 `assembly_name`  
 Genel olmayan türleri. netmodule 'nin erişebileceği derlemenin adı.  
  
## <a name="remarks"></a>Açıklamalar  
 **-moduleassemblyname** bir. netmodule oluştururken ve aşağıdaki koşulların doğru olduğu durumlarda kullanılmalıdır:  
  
- . Netmodule, mevcut bir derlemede ortak olmayan türlere erişim gerektirir.  
  
- . Netmodule 'nin derolacağı derlemenin adını bilirsiniz.  
  
- Mevcut bütünleştirilmiş kod,. netmodule 'nin derolacağı derlemeye arkadaş derleme erişimi verdi.  
  
 . Netmodule oluşturma hakkında daha fazla bilgi için bkz. [-target: Module (C# derleyici seçenekleri)](./target-module-compiler-option.md).  
  
 Friend derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).  
  
 Bu seçenek geliştirme ortamının içinden kullanılamaz; yalnızca komut satırından derlerken kullanılabilir.  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Bu örnek, özel bir türü olan ve csman_an_assembly adlı bir derlemeye arkadaş derleme erişimi veren bir derleme oluşturur.  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, moduleassemblyname_1. dll derlemesinde genel olmayan bir türe erişen. netmodule 'yi oluşturur. Bu. netmodule 'nin csman_an_assembly adlı bir derlemede derlenip,. netmodule 'nin csman_an_ 'e arkadaş derleme erişimi veren bir derlemede genel olmayan türlere erişmesine izin vererek **-moduleassemblyname**belirtemez. derleme.  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a>Örnek  
 Bu kod örneği, önceden derlenmiş derleme ve. netmodule 'e başvurarak derleme csman_an_assembly oluşturur.  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
**An_Internal_Class. test çağrıldı**

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

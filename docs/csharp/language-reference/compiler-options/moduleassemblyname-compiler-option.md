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
ms.openlocfilehash: 7d39840f3b12df621a0e8d5fae5725065c295e59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662679"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname (C# derleyici seçeneği)
Genel olmayan türler .netmodule erişebilmeniz için bir derleme belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
 `assembly_name`  
 .netmodule, genel olmayan türleri derlemenin adını erişebilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 **-moduleassemblyname** .netmodule oluştururken ve aşağıdaki koşullar doğru olduğunda kullanılmalıdır:  
  
- .netmodule var olan bir derlemede ortak olmayan türlere erişmesi gerekir.  
  
- Bildiğiniz .netmodule derlenecek olan derlemenin adı.  
  
- Mevcut bütünleştirilmiş kodu .netmodule derlenecek olan derlemeye arkadaş derleme erişim verildi.  
  
 .Netmodule derleme hakkında daha fazla bilgi için bkz. [-target: module (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 Arkadaş bütünleştirilmiş kodları hakkında daha fazla bilgi için bkz. [arkadaş derlemeleri](../../../standard/assembly/friend-assemblies.md).  
  
 Bu seçenek geliştirme ortamı içinden erişilebilir değildir; Yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
 Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir özel tür sahip bir derleme oluşturur ve bu csman_an_assembly adlı bir derlemeye arkadaş derleme erişim sağlar.  
  
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
 Bu örnek, bir derleme moduleassemblyname_1.dll genel olmayan türde erişen bir .netmodule oluşturur. Bu .netmodule csman_an_assembly adı verilen bir derlemeye oluşturulacak bilirseniz, biz belirtebilirsiniz **- moduleassemblyname**, .netmodule arkadaş derleme verilmiş bir derlemede ortak olmayan türlere erişmek izin verme için csman_an_assembly erişin.  
  
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
 Bu kod örneği, .netmodule ve daha önce oluşturulan derlemeyi başvuran derlemenin csman_an_assembly oluşturur.  
  
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
  
**An_Internal_Class.test**

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

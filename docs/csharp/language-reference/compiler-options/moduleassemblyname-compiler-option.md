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
ms.openlocfilehash: 2c6467434b56d624c42aaf54219959228e068ffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname (C# derleyici seçeneği)
Ortak olmayan türlere bir .netmodule erişebileceği bir derleme belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
 `assembly_name`  
 .netmodule, genel türleri derlemenin adını erişebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 **-moduleassemblyname** bir .netmodule oluştururken ve aşağıdaki koşullar doğru olduğunda kullanılmalıdır:  
  
-   .netmodule mevcut bir derlemede ortak olmayan türlere erişimi olmalıdır.  
  
-   İçine .netmodule oluşturulacak derleme adını öğrenin.  
  
-   Varolan derleme içine .netmodule oluşturulacak derlemeye arkadaş derleme erişimi verildi.  
  
 Bir .netmodule oluşturma hakkında daha fazla bilgi için bkz: [-target: module (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 Arkadaş derlemeler hakkında daha fazla bilgi için bkz: [arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
 Bu seçenek geliştirme ortamında kullanılamaz; Yalnızca komut satırından derlerken kullanılabilir.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Bu örnek özel türüne sahip bir derleme oluşturur ve csman_an_assembly adlı bir derlemeye arkadaş derleme erişim sağlar.  
  
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
 Bu örnek bir genel türünde derleme moduleassemblyname_1.dll erişen bir .netmodule oluşturur. Bu .netmodule csman_an_assembly adlı bir derlemeye oluşturulacak öğrenerek biz belirtebilirsiniz **- moduleassemblyname**, ortak olmayan türlere derlemedeki derlemeyi verildi erişmek .netmodule izin verme için csman_an_assembly erişin.  
  
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
 Bu kod örneği daha önce oluşturulmuş derlemeyi ve .netmodule başvuran derlemenin csman_an_assembly oluşturur.  
  
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
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

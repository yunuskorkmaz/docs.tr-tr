---
title: -moduleassemblyname (C# Derleyici Seçeneği)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 1477eeb0f2e16e18cb86009739bc8e7d9dee2ac0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173724"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname (C# Derleyici Seçeneği)
Ortak olmayan türleri bir .netmodule erişebileceği bir derleme belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `assembly_name`  
 .netmodülünün erişebileceği genel olmayan türleri olan derlemenin adı.  
  
## <a name="remarks"></a>Açıklamalar  
 **-moduleassemblyname** bir .netmodule inşa ederken kullanılmalıdır ve aşağıdaki koşullar doğru:  
  
- .netmodülü, varolan bir derlemede genel olmayan türlere erişmeye ihtiyaç duyar.  
  
- .netmodülünün oluşturulacağı derlemenin adını biliyorsunuz.  
  
- Varolan derleme, .net modülünün oluşturulacağı derlemeye arkadaş derleme erişimi verdi.  
  
 .netmodule oluşturma hakkında daha fazla bilgi için bkz: [-target:module (C# Derleyici Seçenekleri)](./target-module-compiler-option.md).  
  
 Arkadaş derlemeleri hakkında daha fazla bilgi için [Arkadaş Derlemeleri'ne](../../../standard/assembly/friend.md)bakın.  
  
 Bu seçenek geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Bu örnek, özel türü olan bir derleme oluşturur ve arkadaş derlemesi csman_an_assembly adlı bir derlemeye erişim sağlar.  
  
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
 Bu örnek, derleme moduleassemblyname_1.dll'de genel olmayan bir türe erişen bir .netmodülü oluşturur. Bu .netmodule'ın csman_an_assembly adlı bir derlemede oluşturulacağını bilerek, .netmodülün csman_an_assembly arkadaş derlemesi erişimi sağlayan bir derlemede genel olmayan türlere erişmesine izin vererek **-moduleassemblyname'yi**belirtebiliriz.  
  
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
 Bu kod örneği, daha önce oluşturulmuş derleme ve .netmodule başvurarak, csman_an_assembly derleme oluşturur.  
  
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
  
**An_Internal_Class.Test adlı**

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

---
title: -hedef (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: ea5481810e629d911c4d5aba62e60c98d0783f34
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644352"
---
# <a name="-target-c-compiler-options"></a>-hedef (C# Derleyici Seçenekleri)
**-hedef** derleyici seçeneği dört formdan birinde belirtilebilir:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Windows 8.x Store uygulamaları için bir .exe dosyası oluşturmak için.  
  
 [-target:exe](./target-exe-compiler-option.md)  
 Bir .exe dosyası oluşturmak için.  
  
 [-target:library](./target-library-compiler-option.md)  
 Kod kitaplığı oluşturmak için.  
  
 [-target:module](./target-module-compiler-option.md)  
 Bir modül oluşturmak için.  
  
 [-target:winexe](./target-winexe-compiler-option.md)  
 Bir Windows programı oluşturmak için.  
  
 [-target:winmdobj](./target-winmdobj-compiler-option.md)  
 Bir ara .winmdobj dosyası oluşturmak için.  
  
 **-target:module**, -target belirtmediğiniz sürece **hedef,** bir çıktı dosyasına bir .NET Framework derleme bildiriminin yerleştirilmesine neden olur. Daha fazla bilgi için .NET ve [Ortak Özniteliklerdeki](../attributes/global.md) [Derlemeler'e](../../../standard/assembly/index.md) bakın.  
  
 Derleme bildirimi derlemedeki ilk .exe çıktı dosyasına veya .exe çıktı dosyası yoksa ilk DLL'ye yerleştirilir. Örneğin, aşağıdaki komut satırında, bildirim `1.exe`yerleştirilir:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Derleyici derleme başına yalnızca bir derleme bildirimi oluşturur. Derlemedeki tüm dosyalar la ilgili bilgiler derleme manifestosuna yerleştirilir. **-target:module** ile oluşturulanlar dışındaki tüm çıktı dosyaları bir derleme bildirimi içerebilir. Komut satırında birden çok çıktı dosyası oluşturulurken, yalnızca bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıktı dosyasına geçmesi gerekir. İlk çıktı dosyası ne olursa olsun (**-hedef:exe**, **-target:winexe**, **-target:library** veya **-target:module**), aynı derlemede üretilen diğer çıktı dosyaları modüller olmalıdır (**-target:module**).  
  
 Bir derleme oluşturursanız, kodunuzun tamamının veya bir kısmının ÖZnitelikile <xref:System.CLSCompliantAttribute> CLS uyumlu olduğunu belirtebilirsiniz.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Bu derleyici seçeneğini programlı olarak ayarlama <xref:VSLangProj80.ProjectProperties3.OutputType%2A>hakkında daha fazla bilgi için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [-alt sistem versiyonu (C# Derleyici Seçenekleri)](./subsystemversion-compiler-option.md)

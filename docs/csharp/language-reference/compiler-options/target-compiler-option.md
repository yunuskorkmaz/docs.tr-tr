---
title: -target (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204512"
---
# <a name="-target-c-compiler-options"></a>-target (C# derleyici seçenekleri)
**-Target** derleyici seçeneği dört formdan birinde belirtilebilir:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Windows 8. x Mağazası uygulamaları için bir. exe dosyası oluşturmak için.  
  
 [-target:exe](./target-exe-compiler-option.md)  
 Bir. exe dosyası oluşturmak için.  
  
 [-target:library](./target-library-compiler-option.md)  
 Bir kod kitaplığı oluşturun.  
  
 [-target:module](./target-module-compiler-option.md)  
 Bir modül oluşturmak için.  
  
 [-target:winexe](./target-winexe-compiler-option.md)  
 Bir Windows programı oluşturmak için.  
  
 [-target:winmdobj](./target-winmdobj-compiler-option.md)  
 Ara. winmdobj dosyası oluşturmak için.  
  
 **-Target: Module**belirtmediğiniz takdirde **-target** bir .NET Framework derleme bildiriminin bir çıkış dosyasına yerleştirilmesine neden olur. Daha fazla bilgi için bkz. .NET ve [ortak özniteliklerde](../../programming-guide/concepts/attributes/common-attributes.md) [derlemeler](../../../standard/assembly/index.md) .  
  
 Derleme bildirimi, derleme içindeki ilk. exe çıkış dosyasına veya. exe çıkış dosyası yoksa ilk DLL 'de yerleştirilir. Örneğin, aşağıdaki komut satırında, bildirim `1.exe`yerleştirilecek:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Derleyici, derleme başına yalnızca bir derleme bildirimi oluşturur. Bir derlemedeki tüm dosyalar hakkındaki bilgiler, derleme bildirimine yerleştirilir. **-Target: Module** ile oluşturulanlar hariç tüm çıkış dosyaları bir derleme bildirimi içerebilir. Komut satırında birden çok çıkış dosyası üretilirken, yalnızca bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıkış dosyasına gitmelidir. İlk çıkış dosyasının ne olduğuna bakılmaksızın ( **-target: exe**, **-target: winexe**, **-target: Library** veya **-target: Module**), aynı derlemede üretilen diğer çıkış dosyaları modüller olmalıdır ( **-target: Module**).  
  
 Bir derleme oluşturursanız, kodunuzun tümünün veya bir kısmının <xref:System.CLSCompliantAttribute> özniteliğiyle CLS uyumlu olduğunu belirtebilirsiniz.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (C# derleyici seçenekleri)](./subsystemversion-compiler-option.md)

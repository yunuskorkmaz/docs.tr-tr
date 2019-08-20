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
ms.openlocfilehash: 0630639433aed4c8dfddbf0144e9802ed3f4ee73
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606442"
---
# <a name="-target-c-compiler-options"></a>-target (C# derleyici seçenekleri)
**-Target** derleyici seçeneği dört formdan birinde belirtilebilir:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Uygulamalar için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] bir. exe dosyası oluşturmak için.  
  
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
  
 **-Target: Module**belirtmediğiniz takdirde **-target** bir .NET Framework derleme bildiriminin bir çıkış dosyasına yerleştirilmesine neden olur. Daha fazla bilgi için bkz. [ortak dil çalışma zamanı](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) ve [ortak özniteliklerdeki](../../programming-guide/concepts/attributes/common-attributes.md)derlemeler.  
  
 Derleme bildirimi, derleme içindeki ilk. exe çıkış dosyasına veya. exe çıkış dosyası yoksa ilk DLL 'de yerleştirilir. Örneğin, aşağıdaki komut satırında bildirim yerleştirilecek `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Derleyici, derleme başına yalnızca bir derleme bildirimi oluşturur. Bir derlemedeki tüm dosyalar hakkındaki bilgiler, derleme bildirimine yerleştirilir. **-Target: Module** ile oluşturulanlar hariç tüm çıkış dosyaları bir derleme bildirimi içerebilir. Komut satırında birden çok çıkış dosyası üretilirken, yalnızca bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıkış dosyasına gitmelidir. İlk çıkış dosyasının ne olduğuna bakılmaksızın ( **-target: exe**, **-target: winexe**, **-target: Library** veya **-target: Module**), aynı derlemede üretilen diğer çıkış dosyaları modüller olmalıdır ( **-target: Module**).  
  
 Bir derleme oluşturursanız, kodunuzun tümünün veya bir kısmının <xref:System.CLSCompliantAttribute> öznitelik ile CLS uyumlu olduğunu belirtebilirsiniz.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için <xref:VSLangProj80.ProjectProperties3.OutputType%2A>bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (C# derleyici seçenekleri)](./subsystemversion-compiler-option.md)

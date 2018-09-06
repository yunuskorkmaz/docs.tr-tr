---
title: -target (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: a337ecbc614ff40eda42fc5263dbb52aa92b905f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874133"
---
# <a name="-target-c-compiler-options"></a>-target (C# Derleyici Seçenekleri)
**-Hedef** derleyici seçeneği dört biçimlerden birinde belirtilebilir:  
  
 [-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Bir .exe dosyası oluşturmak için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulamalar.  
  
 [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 Bir .exe dosyası oluşturmak için.  
  
 [-target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 Bir kod kitaplığı oluşturmak için.  
  
 [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Bir modül oluşturmak için  
  
 [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Bir Windows programı oluşturmak için.  
  
 [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Bir ara .winmdobj dosyası oluşturmak için.  
  
 Siz belirtmediğiniz sürece **-target: module**, **-hedef** bir .NET Framework derleme bildirimi bir çıkış dosyası yerleştirilmesine neden olur. Daha fazla bilgi için [ortak dil çalışma zamanı derlemeleri](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) ve [ortak öznitelikleri](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 .Exe çıkış dosyası yoksa derleme bildirimi ilk .exe çıkış dosyası derleme veya ilk DLL yerleştirilir. Örneğin, aşağıdaki komut satırında bildirim yerleştirileceği `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Derleyici, derleme başına yalnızca bir derleme bildirimi oluşturur. Bir derlemede tüm dosyaları hakkında bilgi, derleme bildirimine yerleştirilir. Tüm dosyaları ile oluşturulanlar dışındaki çıktı **-target: module** bir derleme bildirimi içerebilir. Komut satırında birden çok çıkış dosyaları üreten, tek bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıktı dosyası içine gitmeniz gerekir. Hangi ilk çıktı dosyası ne olursa olsun (**-target: exe**, **-target: winexe**, **-target: library** veya **-target: module**), diğer aynı derlemede üretilen Çıkış dosyalarını modülleri olmalıdır (**-target: module**).  
  
 Bir derlemeyi oluşturursanız, kodunuzun bir kısmını veya tamamını CLS ile uyumlu olduğunu gösterebilir <xref:System.CLSCompliantAttribute> özniteliği.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Bu derleyici seçeneğini programlama yoluyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
- [-subsystemversion (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)

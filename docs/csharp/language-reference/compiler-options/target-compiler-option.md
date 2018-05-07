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
ms.openlocfilehash: 7736b8850a7b09f7212e83e05acf0e1994bce0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-target-c-compiler-options"></a>-target (C# Derleyici Seçenekleri)
**-Hedef** derleyici seçeneği dört forms biri belirtilebilir:  
  
 [-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Bir .exe dosyası oluşturmak için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulamalar.  
  
 [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 Bir .exe dosyası oluşturmak için.  
  
 [-target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 Bir kod kitaplığı oluşturmak için.  
  
 [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Bir modül oluşturmak için.  
  
 [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Bir Windows programı oluşturmak için.  
  
 [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Bir ara .winmdobj dosyası oluşturmak için.  
  
 Belirtmediğiniz sürece **-target: module**, **-hedef** bir çıktı dosyasına yerleştirilecek bir .NET Framework derleme bildirimi neden olur. Daha fazla bilgi için bkz: [ortak dil çalışma zamanı derlemeleri](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) ve [ortak öznitelikler](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 .Exe çıktı dosyası yoksa ilk .exe çıktı dosyası derleme veya ilk DLL derleme bildirimi yerleştirilir. Örneğin, aşağıdaki komut satırında bildirim yerleştirilecek `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Derleyici derleme işlemi başına yalnızca bir derleme bildirimi oluşturur. Bir derleme içindeki tüm dosyalar hakkında bilgi derleme bildiriminde yerleştirilir. Tüm dosyaları ile oluşturulanlar dışındaki çıktı **-target: module** bir derleme bildirimi içerebilir. Komut satırında birden çok çıktı dosyaları üretirken, yalnızca bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıktı dosyasına gitmeniz gerekir. Hangi ilk çıktı dosyası olsun (**-target: exe**, **-target: winexe**, **-target: library** veya **-target: module**), diğer Çıkış dosyaları aynı derlemede üretilen modülleri olmalıdır (**-target: module**).  
  
 Bir derlemeyi oluşturursanız, kodunuzun bir bölümünü veya tümünü CLS ile uyumlu olduğunu gösterebilir <xref:System.CLSCompliantAttribute> özniteliği.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Bu derleyici seçeneği programlı olarak ayarlama hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
 [-subsystemversion (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)

---
title: extern (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 996888a585f8355bdda14e09b6bb9544257ae824
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172299"
---
# <a name="extern-c-reference"></a>extern (C# Başvurusu)
`extern` Değiştiricisi harici olarak uygulanan bir yöntem bildirmek için kullanılır. Yaygın kullanımı `extern` değiştiricisi durumdayken `DllImport` yönetilmeyen koda çağırmak için birlikte çalışma hizmetleri kullanırken özniteliği. Bu durumda, yöntem de olarak bildirilmelidir `static`, aşağıdaki örnekte gösterildiği gibi:  
  
```csharp  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 `extern` Anahtar sözcüğü de tek bir derleme içinde aynı bileşenin farklı sürümlerini başvuru mümkün kılan bir dış derleme diğer ad tanımlayın. Daha fazla bilgi için bkz: [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).  
  
 Kullanmak için bir hata olduğunu [soyut](../../../csharp/language-reference/keywords/abstract.md) ve `extern` değiştiricileri birlikte aynı üye değiştirin. Kullanarak `extern` değiştiricisi anlamına gelir C# kodu dışında uygulanan yöntemi kullanarak ancak `abstract` değiştiricisi anlamına gelir yöntem uygulaması sınıfında sağlanmadı.  
  
 extern anahtar sözcüğünün kullanımları, C++'a göre C#'de daha fazladır. C# anahtar sözcüğünü C++ anahtar sözcüğüyle karşılaştırmak için, C++ Dilinde Bağlantı Belirtmek için extern Kullanma Başvurusu'na bakın.  
  
## <a name="example"></a>Örnek  
 **Örnek 1.** Bu örnekte, kullanıcıdan bir dize alır ve program içinde bir ileti kutusu görüntüler. Program kullanan `MessageBox` yöntemi User32.dll kitaplığından içeri aktarıldı.  
  
 [!code-csharp[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]  
  
## <a name="example"></a>Örnek  
 **Örnek 2.** Bu örnekte, bir C Kitaplığı'na (yerel DLL) çağıran bir C# programı gösterilmektedir.  
  
 1. Aşağıdaki C dosyası oluşturun ve adlandırın `cmdll.c`:  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a>Örnek  
 2. Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel Araçları Komut İstemi penceresi açın ve derleme `cmdll.c` yazarak dosya **cl /LD cmdll.c** komut isteminde.  
  
 3. Aynı dizinde aşağıdaki C# dosyası oluşturun ve adlandırın `cm.cs`:  
  
```csharp  
// cm.cs  
using System;  
using System.Runtime.InteropServices;  
public class MainClass   
{  
   [DllImport("Cmdll.dll")]  
   public static extern int SampleMethod(int x);  
  
   static void Main()   
   {  
      Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));  
   }  
}  
```  
  
## <a name="example"></a>Örnek  
 3. Visual Studio yükleme dizininden bir Visual Studio x64 (veya x32) yerel Araçları Komut İstemi penceresi açın ve derleme `cm.cs` yazarak dosyası:  
  
> **CSC cm.cs** (x64 için komut istemi)   
>  —veya—  
> **CSC /platform:x 86 cm.cs** (x32 için komut istemi)  
  
 Bu yürütülebilir dosya oluşturacak `cm.exe`.  
  
 4. Çalıştırma `cm.exe`. `SampleMethod` Yöntemi tarafından 10 çarpılan değeri döndürür DLL dosyasının 5 değerini iletir.  Program şu çıkışı üretir:  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)

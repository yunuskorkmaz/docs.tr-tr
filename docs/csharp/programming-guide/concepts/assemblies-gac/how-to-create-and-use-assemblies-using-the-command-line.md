---
title: "Nasıl yapılır: komut satırını (C#) kullanarak derlemeler oluşturma ve kullanma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d59988ec4899b4115d8d0fd7172e0c8ff8802378
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Nasıl yapılır: komut satırını (C#) kullanarak derlemeler oluşturma ve kullanma
Bir derlemeyi ya da dinamik bağlantı kitaplığı (DLL) programınıza çalışma zamanında bağlanır. Derleme ve DLL kullanarak göstermek için aşağıdaki senaryoyu göz önünde bulundurun:  
  
-   `MathLibrary.DLL`: Çalışma zamanında çağrılacak yöntem içerir kitaplık dosyası. Bu örnekte, iki yöntem DLL içeren `Add` ve `Multiply`.  
  
-   `Add`: Yöntem içerir kaynak dosya `Add`. Bunu parametrelerinin toplamını döndürür. Sınıf `AddClass` yöntemi içeren `Add` ad üyesi `UtilityMethods`.  
  
-   `Mult`: Yöntem içerir kaynak kodu `Multiply`. Bunu parametrelerinin çarpımını döndürür. Sınıf `MultiplyClass` yöntemi içeren `Multiply` de ad alanının bir üyesidir `UtilityMethods`.  
  
-   `TestCode`: İçerir dosya `Main` yöntemi. Yöntemleri, toplam ve çalışma zamanı değişkenleri Ürün hesaplamak için DLL dosyasını kullanır.  
  
## <a name="example"></a>Örnek  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 Bu dosya DLL yöntemleri tarafından kullanılan algoritmasını içerir `Add` ve `Multiply`. Komut satırından girilen bağımsız değişkenlerini ayrıştırma ile başlayan `num1` ve `num2`. Kullanarak toplamı hesaplar sonra `Add` yöntemi `AddClass` sınıfını ve ürünü kullanarak `Multiply` yöntemi `MultiplyClass` sınıfı.  
  
 Dikkat `using` yönergesi dosyasının başında DLL yöntemleri derleme zamanında şu şekilde başvurmak için nitelenmemiş sınıf adları kullanabilmenizi sağlar:  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 Aksi halde, tam olarak nitelenmiş adlar aşağıdaki gibi kullanmak zorunda:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Yürütme  
 Programı çalıştırmak için iki numaralarına göre aşağıdaki gibi ardından EXE dosyasının adını girin:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Dosyasını oluşturmak için `MathLibrary.DLL`, iki dosyalarını derlemek `Add` ve `Mult` aşağıdaki komut satırını kullanarak.  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 [/Target: library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) derleyici seçeneği bir EXE dosyası yerine bir DLL çıktısını almak için derleyici söyler. [/Out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) dosya adından derleyici seçeneği DLL dosya adı belirtmek için kullanılır. Aksi durumda, ilk dosya derleyici kullanır (`Add.cs`) DLL adından farklı.  
  
 Yürütülebilir dosyasını oluşturmak için `TestCode.exe`, aşağıdaki komut satırını kullanın:  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 **/Out** derleyici seçeneği çıkış bir EXE dosyası bildirir ve çıktı dosyası adını belirtir (`TestCode.exe`). Bu derleyici seçeneği isteğe bağlıdır. [/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneği DLL dosyası ya da, bu programın kullandığı dosyalarını belirtir. Daha fazla bilgi için bkz: [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırı derleme ile csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Derlemeler ve Genel Derleme Önbelleği (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [DLL işlevleri için bir sınıf oluşturma](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)

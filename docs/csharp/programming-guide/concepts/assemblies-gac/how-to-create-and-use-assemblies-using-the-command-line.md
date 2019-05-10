---
title: 'Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 76243034b4291142efa5ac78c21f65333e1378e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599864"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma (C#)
Bir derleme veya dinamik bağlantı kitaplığı (DLL), programınız için çalışma zamanında bağlıdır. Oluşturma ve bir DLL kullanarak göstermek için aşağıdaki senaryoyu göz önünde bulundurun:  
  
- `MathLibrary.DLL`: Çalışma zamanında çağrılabilir yöntemleri içeren kitaplık dosyası. Bu örnekte, iki yöntem, DLL içeren `Add` ve `Multiply`.  
  
- `Add`: Yöntemi içeren kaynak dosyayı `Add`. Parametrelerini toplamını döndürür. Sınıf `AddClass` yöntemi içeren `Add` ad alanının bir üyesidir `UtilityMethods`.  
  
- `Mult`: Yöntemi içeren kaynak kodu `Multiply`. Parametrelerini çarpımını döndürür. Sınıf `MultiplyClass` yöntemi içeren `Multiply` ayrıca ad alanının bir üyesidir `UtilityMethods`.  
  
- `TestCode`: İçeren dosyayı `Main` yöntemi. Yöntemleri, toplam ve çalışma zamanı bağımsız değişken ürününü hesaplar için DLL dosyası içinde kullanır.  
  
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
  
 Bu dosyayı içeren DLL yöntemleri kullanan algoritma `Add` ve `Multiply`. Girilen komut satırından bağımsız değişkenlerini ayrıştırma ile başlayan `num1` ve `num2`. Kullanarak toplamı hesaplar `Add` metodunda `AddClass` sınıfını ve ürünü kullanarak `Multiply` metodunda `MultiplyClass` sınıfı.  
  
 Dikkat `using` dosyasının başında yönergesi DLL yöntemleri gibi derleme zamanında başvurmak için nitelenmemiş sınıf adları kullanmanıza olanak sağlar:  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 Aksi takdirde, tam olarak nitelenmiş adlar kullanacak şekilde gerekir:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Yürütme  
 Programı çalıştırmak için iki sayı, aşağıdaki gibi yazın, bir EXE dosyasının adını girin:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Dosyayı oluşturmak için `MathLibrary.DLL`, iki dosya derleme `Add` ve `Mult` şu komut satırını kullanarak.  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 [/Target: library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) derleyici seçeneği, derleyicinin çıktısını bir EXE dosyası yerine bir DLL söyler. [/Out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) dosya adından önce gelen derleyici seçeneği, DLL dosya adı belirtmek için kullanılır. Aksi halde, derleyici ilk dosyayı kullanır (`Add.cs`) olarak DLL'in adı.  
  
 Yürütülebilir dosyayı oluşturmak için `TestCode.exe`, şu komut satırını kullanın:  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 **/Out** derleyici seçeneği, derleyiciye bir EXE dosyası çıkış ve çıktı dosyası adını belirtir (`TestCode.exe`). Bu derleyici seçeneğini isteğe bağlıdır. [/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneği, DLL dosyasının veya bu programın kullandığı dosyaları belirtir. Daha fazla bilgi için [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Komut satırından oluşturma hakkında daha fazla bilgi için bkz. [oluşturma ile komut satırı csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
- [DLL İşlevleri için bir Sınıf Oluşturma](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)

---
title: 'Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 0a8db22a05d834d15f6e6b7f049f59f86bc1fe1d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595972"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma (C#)
Bir derleme veya dinamik bağlantı kitaplığı (DLL), çalışma zamanında programınıza bağlanır. Bir DLL oluşturmayı ve kullanmayı göstermek için aşağıdaki senaryoyu göz önünde bulundurun:  
  
- `MathLibrary.DLL`: Çalışma zamanında çağrılacak yöntemleri içeren kitaplık dosyası. Bu örnekte, DLL iki yöntem `Add` içerir ve. `Multiply`  
  
- `Add`: Yöntemini `Add`içeren kaynak dosya. Parametrelerinin toplamını döndürür. `UtilityMethods`Yöntemi `AddClass` içeren`Add` sınıf, ad alanının bir üyesidir.  
  
- `Mult`: Yöntemini `Multiply`içeren kaynak kodu. Kendi parametrelerinin çarpımını döndürür. `UtilityMethods`Yöntemi `MultiplyClass` içeren`Multiply` sınıf ayrıca ad alanının bir üyesidir.  
  
- `TestCode`: `Main` Yöntemini içeren dosya. Çalışma zamanı bağımsız değişkenlerinin toplamını ve çarpımını hesaplamak için DLL dosyasındaki yöntemleri kullanır.  
  
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
  
 Bu dosya, dll yöntemlerini ve `Add` `Multiply`' ı kullanan algoritmayı içerir. Komut satırından `num1` girilen bağımsız değişkenlerin ayrıştırılmasından başlar ve `num2`. Daha sonra, `Add` sınıfındaki yöntemini kullanarak ve `AddClass` `Multiply` `MultiplyClass` sınıfındaki yöntemi kullanarak toplamı hesaplar.  
  
 Dosyanın başındaki yönerge, derleme zamanında DLL yöntemlerine başvurmak için, nitelenmemiş sınıf adlarını şu şekilde kullanmanıza olanak sağlar: `using`  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 Aksi takdirde, aşağıdaki gibi tam nitelikli adları kullanmanız gerekir:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Yürütme  
 Programı çalıştırmak için, EXE dosyasının adını ve ardından iki sayıyı aşağıdaki şekilde girin:  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../index.md)
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
- [DLL İşlevleri için bir Sınıf Oluşturma](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)

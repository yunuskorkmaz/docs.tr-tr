---
title: 'Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma'
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
ms.openlocfilehash: eefb6ccfabdb7897874ae4e5a8abc8c2d9cc8e35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534780"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma
Bir derleme veya dinamik bağlantı kitaplığı (DLL), programınız için çalışma zamanında bağlıdır. Oluşturma ve bir DLL kullanarak göstermek için aşağıdaki senaryoyu göz önünde bulundurun:  
  
-   `MathLibrary.DLL`: Çalışma zamanında çağrılabilir yöntemleri içeren kitaplık dosyası. Bu örnekte, iki yöntem, DLL içeren `Add` ve `Multiply`.  
  
-   `Add`: Yöntemi içeren kaynak dosyayı `Add`. Parametrelerini toplamını döndürür. Sınıf `AddClass` yöntemi içeren `Add` ad alanının bir üyesidir `UtilityMethods`.  
  
-   `Mult`: Yöntemi içeren kaynak kodu `Multiply`. Parametrelerini çarpımını döndürür. Sınıf `MultiplyClass` yöntemi içeren `Multiply` ayrıca ad alanının bir üyesidir `UtilityMethods`.  
  
-   `TestCode`: İçeren dosyayı `Main` yöntemi. Yöntemleri, toplam ve çalışma zamanı bağımsız değişken ürününü hesaplar için DLL dosyası içinde kullanır.  
  
## <a name="example"></a>Örnek  
  
```vb  
' File: Add.vb   
Namespace UtilityMethods  
    Public Class AddClass  
        Public Shared Function Add(ByVal i As Long, ByVal j As Long) As Long  
            Return i + j  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: Mult.vb  
Namespace UtilityMethods  
    Public Class MultiplyClass  
        Public Shared Function Multiply(ByVal x As Long, ByVal y As Long) As Long  
            Return x * y  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: TestCode.vb  
  
Imports UtilityMethods  
  
Module Test  
  
    Sub Main(ByVal args As String())  
  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:")  
  
        If args.Length <> 2 Then  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>")  
            Return  
        End If  
  
        Dim num1 As Long = Long.Parse(args(0))  
        Dim num2 As Long = Long.Parse(args(1))  
  
        Dim sum As Long = AddClass.Add(num1, num2)  
        Dim product As Long = MultiplyClass.Multiply(num1, num2)  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum)  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product)  
  
    End Sub  
  
End Module  
  
' Output (assuming 1234 and 5678 are entered as command-line arguments):  
' Calling methods from MathLibrary.DLL:  
' 1234 + 5678 = 6912  
' 1234 * 5678 = 7006652  
```  
  
 Bu dosyayı içeren DLL yöntemleri kullanan algoritma `Add` ve `Multiply`. Girilen komut satırından bağımsız değişkenlerini ayrıştırma ile başlayan `num1` ve `num2`. Kullanarak toplamı hesaplar `Add` metodunda `AddClass` sınıfını ve ürünü kullanarak `Multiply` metodunda `MultiplyClass` sınıfı.  
  
 Dikkat `Imports` dosyasının başında deyimi DLL yöntemleri gibi derleme zamanında başvurmak için nitelenmemiş sınıf adları kullanmanıza olanak sağlar:  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 Aksi takdirde, tam olarak nitelenmiş adlar kullanacak şekilde gerekir:  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>Yürütme  
 Programı çalıştırmak için iki sayı, aşağıdaki gibi yazın, bir EXE dosyasının adını girin:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Dosyayı oluşturmak için `MathLibrary.DLL`, iki dosya derleme `Add` ve `Mult` şu komut satırını kullanarak.  
  
```console  
vbc -target:library -out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 [-Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) derleyici seçeneği, derleyicinin çıktısını bir EXE dosyası yerine bir DLL söyler. [-Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) dosya adından önce gelen derleyici seçeneği, DLL dosya adı belirtmek için kullanılır. Aksi halde, derleyici ilk dosyayı kullanır (`Add.vb`) olarak DLL'in adı.  
  
 Yürütülebilir dosyayı oluşturmak için `TestCode.exe`, şu komut satırını kullanın:  
  
```console  
vbc -out:TestCode.exe -reference:MathLibrary.DLL TestCode.vb  
```  
  
 **-Out** derleyici seçeneği, derleyiciye bir EXE dosyası çıkış ve çıktı dosyası adını belirtir (`TestCode.exe`). Bu derleyici seçeneğini isteğe bağlıdır. [-Başvuru (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) derleyici seçeneği, DLL dosyasının veya bu programın kullandığı dosyaları belirtir.  
  
 Komut satırından oluşturma hakkında daha fazla bilgi için bkz ve [komut satırından derleme](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)
- [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [DLL İşlevleri için bir Sınıf Oluşturma](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)

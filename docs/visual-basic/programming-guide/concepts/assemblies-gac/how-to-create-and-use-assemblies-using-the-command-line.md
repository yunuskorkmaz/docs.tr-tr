---
title: "Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72f3e91f9fb88019f937dcd281aa14ab4e887daf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma
Bir derlemeyi ya da dinamik bağlantı kitaplığı (DLL) programınıza çalışma zamanında bağlanır. Derleme ve DLL kullanarak göstermek için aşağıdaki senaryoyu göz önünde bulundurun:  
  
-   `MathLibrary.DLL`: Çalışma zamanında çağrılacak yöntem içerir kitaplık dosyası. Bu örnekte, iki yöntem DLL içeren `Add` ve `Multiply`.  
  
-   `Add`: Yöntem içerir kaynak dosya `Add`. Bunu parametrelerinin toplamını döndürür. Sınıf `AddClass` yöntemi içeren `Add` ad üyesi `UtilityMethods`.  
  
-   `Mult`: Yöntem içerir kaynak kodu `Multiply`. Bunu parametrelerinin çarpımını döndürür. Sınıf `MultiplyClass` yöntemi içeren `Multiply` de ad alanının bir üyesidir `UtilityMethods`.  
  
-   `TestCode`: İçerir dosya `Main` yöntemi. Yöntemleri, toplam ve çalışma zamanı değişkenleri Ürün hesaplamak için DLL dosyasını kullanır.  
  
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
  
 Bu dosya DLL yöntemleri tarafından kullanılan algoritmasını içerir `Add` ve `Multiply`. Komut satırından girilen bağımsız değişkenlerini ayrıştırma ile başlayan `num1` ve `num2`. Kullanarak toplamı hesaplar sonra `Add` yöntemi `AddClass` sınıfını ve ürünü kullanarak `Multiply` yöntemi `MultiplyClass` sınıfı.  
  
 Dikkat `Imports` dosyasının başında deyimi DLL yöntemleri derleme zamanında şu şekilde başvurmak için nitelenmemiş sınıf adları kullanabilmenizi sağlar:  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 Aksi halde, tam olarak nitelenmiş adlar aşağıdaki gibi kullanmak zorunda:  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>Yürütme  
 Programı çalıştırmak için iki numaralarına göre aşağıdaki gibi ardından EXE dosyasının adını girin:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Dosyasını oluşturmak için `MathLibrary.DLL`, iki dosyalarını derlemek `Add` ve `Mult` aşağıdaki komut satırını kullanarak.  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 [/Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) derleyici seçeneği bir EXE dosyası yerine bir DLL çıktısını almak için derleyici söyler. [/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) dosya adından derleyici seçeneği DLL dosya adı belirtmek için kullanılır. Aksi durumda, ilk dosya derleyici kullanır (`Add.vb`) DLL adından farklı.  
  
 Yürütülebilir dosyasını oluşturmak için `TestCode.exe`, aşağıdaki komut satırını kullanın:  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 **/Out** derleyici seçeneği çıkış bir EXE dosyası bildirir ve çıktı dosyası adını belirtir (`TestCode.exe`). Bu derleyici seçeneği isteğe bağlıdır. [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) derleyici seçeneği DLL dosyası ya da, bu programın kullandığı dosyalarını belirtir.  
  
 Komut satırından oluşturma hakkında daha fazla bilgi için bkz: ve [komut satırından derleme](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [DLL işlevleri için bir sınıf oluşturma](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)

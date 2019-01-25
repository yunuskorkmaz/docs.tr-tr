---
title: Visual Basic'de Ana Yordam
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: b84bf20acaaa912e47102973b0484d635f1aa244
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679428"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic'de Ana Yordam
Her Visual Basic uygulama çağrılan yordam içermelidir `Main`. Bu yordamı başlangıç noktası ve uygulamanız için genel denetimi olarak işlev görür. .NET Framework çağrıları, `Main` uygulamanızı yüklendikten ve denetim geçirmeye hazır olduğunda yordamı. Bir Windows Forms uygulaması oluşturmakta olduğunuz sürece, yazmanız gereken `Main` yordamı kendi çalışan uygulamalar için.  
  
 `Main` ilk olarak çalışan kodu içerir. İçinde `Main`, hangi formun program başladığında önce yüklenmesi gereken belirlemek, uygulamanızı bir kopyasını zaten sistemde çalışıp çalışmadığını öğrenmek, uygulamanız için bir dizi değişkenlerini kurmak veya uygulamanın gerek duyduğu bir veritabanı.  
  
## <a name="requirements-for-the-main-procedure"></a>Main yordamı için gereksinimleri  
 (Genellikle ile uzantısı .exe) kendi çalıştığı bir dosya içermelidir bir `Main` yordamı. Bir kitaplık (örneğin ile .dll uzantısı) kendi çalıştırılmaz ve gerekli olmayan bir `Main` yordamı. Oluşturabileceğiniz farklı türde projelere gereksinimleri aşağıdaki gibidir:  
  
-   Konsol uygulamalarının çalıştığı kendi ve en az bir sağlamalısınız `Main` yordamı. biçimindeki telefon numarasıdır.  
  
-   Windows Forms uygulamaları kendi çalıştırın. Ancak, Visual Basic Derleyicisi otomatik olarak oluşturduğu bir `Main` gibi bir yordamda bir uygulama ve zorunda kalmadan bir yazma.  
  
-   Sınıf kitaplıkları gerekli olmayan bir `Main` yordamı. Bunlar, Windows Denetim Kitaplığı ve Web denetimi kitaplıkları içerir. Web uygulamaları, sınıf kitaplıkları dağıtılır.  
  
## <a name="declaring-the-main-procedure"></a>Main yordamı bildirme  
 Bildirmek için dört yolla `Main` yordamı. Veya bağımsız değişken alabilir ve bir değer veya döndürebilir.  
  
> [!NOTE]
>  Bildirirseniz `Main` bir sınıfta kullanmalısınız `Shared` anahtar sözcüğü. Bir modüldeki `Main` olması gerekmez `Shared`.  
  
-   Bildirmek için en kolay yolu olan bir `Sub` bağımsız değişken almaz veya bir değer döndüren yordam.  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main` Ayrıca döndürebilir bir `Integer` programınız için çıkış kodu işletim sisteminin kullandığı değer. Diğer programları, Windows ERRORLEVEL değeri inceleyerek bu kodu test edebilirsiniz. Çıkış kodu döndürülecek bildirmelisiniz `Main` olarak bir `Function` yerine yordam bir `Sub` yordamı.  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   `Main` Ayrıca gerçekleştirebileceğiniz bir `String` bağımsız değişken olarak bir dizi. Dizideki her bir dizenin programınızı çağırmak için kullanılan komut satırı bağımsız değişkenlerden biri içerir. Değerlerine bağlı olarak farklı eylemleri gerçekleştirebilirsiniz.  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   Bildirebilirsiniz `Main` bir çıkış kodu gibi döndürmediğine ancak komut satırı bağımsız değişkenlerini inceleyin.  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Visual Basic programının yapısı](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [String Veri Türü](../../../visual-basic/language-reference/data-types/string-data-type.md)

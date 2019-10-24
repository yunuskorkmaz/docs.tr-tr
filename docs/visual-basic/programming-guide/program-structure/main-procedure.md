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
ms.openlocfilehash: 1c76e3ade0b383727c3241fdaf5ae44b677559c8
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775689"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic'de Ana Yordam
Her Visual Basic uygulaması `Main` adlı bir yordam içermelidir. Bu yordam, uygulamanız için başlangıç noktası ve genel denetim görevi görür. .NET Framework, uygulamanızı yüklemiş ve denetimi geçirmeye hazırsa `Main` yordamınız çağrılır. Bir Windows Forms uygulaması oluşturmadıkça, kendi kendilerine çalışan uygulamalar için `Main` yordamını yazmanız gerekir.

 `Main` ilk olarak çalışan kodu içerir. @No__t_0, program başlatıldığında ilk olarak hangi formun yükleneceğini belirleyebilirsiniz, uygulamanızın bir kopyasının sistemde zaten çalışmakta olup olmadığını bulabilir, uygulamanız için bir dizi değişken oluşturabilir veya uygulamanın gerektirdiği bir veritabanını açabilirsiniz.

## <a name="requirements-for-the-main-procedure"></a>Ana yordamın gereksinimleri
 Kendi üzerinde çalışan bir dosya (genellikle uzantısı. exe) bir `Main` yordamı içermelidir. Bir kitaplık (örneğin,. dll uzantılı) kendi üzerinde çalışmaz ve `Main` yordamı gerektirmez. Oluşturabileceğiniz farklı proje türleri için gereksinimler şunlardır:

- Konsol uygulamaları kendi üzerinde çalışır ve en az bir `Main` yordamı sağlamanız gerekir.

- Windows Forms uygulamalar kendi kendilerine çalışır. Ancak, Visual Basic derleyici bu uygulama için otomatik olarak bir `Main` yordamı oluşturur ve bir tane yazmanız gerekmez.

- Sınıf kitaplıkları `Main` yordam gerektirmez. Bunlar Windows Denetim kitaplıklarını ve Web denetim kitaplıklarını içerir. Web uygulamaları, sınıf kitaplıkları olarak dağıtılır.

## <a name="declaring-the-main-procedure"></a>Ana yordamı bildirme
 @No__t_0 yordamı belirtmenin dört yolu vardır. Bağımsız değişkenler alabilir veya içermez ve bir değer döndürebilir.

> [!NOTE]
> Bir sınıfta `Main` bildirirseniz `Shared` anahtar sözcüğünü kullanmanız gerekir. Bir modülde, `Main` `Shared` olması gerekmez.

- En basit yol, bağımsız değişken almaz veya bir değer döndürmemelidir `Sub` yordamı bildirmenin bir yoludur.

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main`, işletim sisteminin programınız için çıkış kodu olarak kullandığı bir `Integer` değeri de döndürebilir. Diğer programlar Windows ERRORLEVEL değerini inceleyerek bu kodu test edebilir. Çıkış kodu döndürmek için, `Main` `Sub` yordamı yerine `Function` yordamı olarak bildirmeniz gerekir.

    ```vb
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

- `Main`, bir `String` dizisini bağımsız değişken olarak da alabilir. Dizideki her dize, programınızı çağırmak için kullanılan komut satırı bağımsız değişkenlerinden birini içerir. Değerlerine bağlı olarak farklı eylemler gerçekleştirebilirsiniz.

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
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

- Komut satırı bağımsız değişkenlerini incelemek için `Main` bildirebilirsiniz, ancak aşağıdaki gibi bir çıkış kodu döndürmez.

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
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
- [Visual Basic programın yapısı](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [String Veri Türü](../../../visual-basic/language-reference/data-types/string-data-type.md)

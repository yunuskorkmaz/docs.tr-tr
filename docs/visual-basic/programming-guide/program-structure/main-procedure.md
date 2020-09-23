---
title: Main Yordamı
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: d6708ee13963aaae43a73b159032f64f0fffac10
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072216"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic'de Ana Yordam

Her Visual Basic uygulamasının adlı bir yordam içermesi gerekir `Main` . Bu yordam, uygulamanız için başlangıç noktası ve genel denetim görevi görür. .NET Framework, `Main` uygulamanızı yüklemiş ve denetimi geçirmeye hazırsa, yordamınız çağrılır. Windows Forms uygulaması oluşturmadığınız takdirde, `Main` kendi üzerinde çalışan uygulamalar için yordamı yazmanız gerekir.

 `Main` İlk olarak çalışan kodu içerir. İçinde `Main` , program başlatıldığında önce hangi formun yükleneceğini belirleyebilirsiniz, uygulamanızın bir kopyasının sistemde zaten çalışmakta olup olmadığını bulabilir, uygulamanız için bir dizi değişken oluşturun veya uygulamanın gerektirdiği bir veritabanını açın.

## <a name="requirements-for-the-main-procedure"></a>Ana yordamın gereksinimleri

 Kendi üzerinde çalışan bir dosya (genellikle uzantısı. exe) bir `Main` yordam içermelidir. Bir kitaplık (örneğin,. dll uzantılı) kendi üzerinde çalışmaz ve bir `Main` yordam gerektirmez. Oluşturabileceğiniz farklı proje türleri için gereksinimler şunlardır:

- Konsol uygulamaları kendi üzerinde çalışır ve en az bir yordam sağlamanız gerekir `Main` .

- Windows Forms uygulamalar kendi kendilerine çalışır. Ancak, Visual Basic derleyici `Main` Bu uygulama için otomatik olarak bir yordam oluşturur ve bir tane yazmanız gerekmez.

- Sınıf kitaplıkları bir `Main` yordam gerektirmez. Bunlar Windows Denetim kitaplıklarını ve Web denetim kitaplıklarını içerir. Web uygulamaları, sınıf kitaplıkları olarak dağıtılır.

## <a name="declaring-the-main-procedure"></a>Ana yordamı bildirme

 Yordamı belirtmenin dört yolu vardır `Main` . Bağımsız değişkenler alabilir veya içermez ve bir değer döndürebilir.

> [!NOTE]
> `Main`Bir sınıfında bildirirseniz `Shared` anahtar sözcüğünü kullanmanız gerekir. Bir modülde `Main` olması gerekmez `Shared` .

- En basit yol, `Sub` bağımsız değişken olmayan veya bir değer döndüren bir yordam bildirmenin bir yoludur.

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main``Integer`, işletim sisteminin programınız için çıkış kodu olarak kullandığı bir değer de döndürebilir. Diğer programlar Windows ERRORLEVEL değerini inceleyerek bu kodu test edebilir. Çıkış kodu döndürmek için, `Main` yordam yerine bir yordam olarak bildirmeniz gerekir `Function` `Sub` .

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

- `Main` , bir `String` dizi bağımsız değişken olarak da alabilir. Dizideki her dize, programınızı çağırmak için kullanılan komut satırı bağımsız değişkenlerinden birini içerir. Değerlerine bağlı olarak farklı eylemler gerçekleştirebilirsiniz.

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

- `Main`Komut satırı bağımsız değişkenlerini incelemek için, ancak aşağıdaki gibi bir çıkış kodu döndürmezsiniz.

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
- [Bir Visual Basic Programının Yapısı](structure-of-a-visual-basic-program.md)
- [-main](../../reference/command-line-compiler/main.md)
- [Shared](../../language-reference/modifiers/shared.md)
- [Sub Deyimi](../../language-reference/statements/sub-statement.md)
- [Function Deyimi](../../language-reference/statements/function-statement.md)
- [Integer Veri Türü](../../language-reference/data-types/integer-data-type.md)
- [Dize Veri Türü](../../language-reference/data-types/string-data-type.md)

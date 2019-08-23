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
ms.openlocfilehash: 19c6fcb04a373d782db3deafc732f69bf20e7f0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962768"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic'de Ana Yordam
Her Visual Basic uygulamasının adlı `Main`bir yordam içermesi gerekir. Bu yordam, uygulamanız için başlangıç noktası ve genel denetim görevi görür. .NET Framework, uygulamanızı yüklemiş `Main` ve denetimi geçirmeye hazırsa, yordamınız çağrılır. Windows Forms uygulaması oluşturmadığınız takdirde, kendi üzerinde çalışan uygulamalar için `Main` yordamı yazmanız gerekir.

 `Main`İlk olarak çalışan kodu içerir. İçinde `Main`, program başlatıldığında önce hangi formun yükleneceğini belirleyebilirsiniz, uygulamanızın bir kopyasının sistemde zaten çalışmakta olup olmadığını bulabilir, uygulamanız için bir dizi değişken oluşturun veya uygulamanın gerektirdiği bir veritabanını açın.

## <a name="requirements-for-the-main-procedure"></a>Ana yordamın gereksinimleri
 Kendi üzerinde çalışan bir dosya (genellikle uzantısı. exe) bir `Main` yordam içermelidir. Bir kitaplık (örneğin,. dll uzantılı) kendi üzerinde çalışmaz ve bir `Main` yordam gerektirmez. Oluşturabileceğiniz farklı proje türleri için gereksinimler şunlardır:

- Konsol uygulamaları kendi üzerinde çalışır ve en az bir `Main` yordam sağlamanız gerekir.

- Windows Forms uygulamalar kendi kendilerine çalışır. Ancak, Visual Basic derleyici bu uygulama için otomatik `Main` olarak bir yordam oluşturur ve bir tane yazmanız gerekmez.

- Sınıf kitaplıkları bir `Main` yordam gerektirmez. Bunlar Windows Denetim kitaplıklarını ve Web denetim kitaplıklarını içerir. Web uygulamaları, sınıf kitaplıkları olarak dağıtılır.

## <a name="declaring-the-main-procedure"></a>Ana yordamı bildirme
 `Main` Yordamı belirtmenin dört yolu vardır. Bağımsız değişkenler alabilir veya içermez ve bir değer döndürebilir.

> [!NOTE]
> Bir sınıfında bildirirseniz `Main` `Shared` anahtar sözcüğünü kullanmanız gerekir. Bir modülde `Main` olması `Shared`gerekmez.

- En basit yol, bağımsız değişken olmayan `Sub` veya bir değer döndüren bir yordam bildirmenin bir yoludur.

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main`, işletim sisteminin programınız `Integer` için çıkış kodu olarak kullandığı bir değer de döndürebilir. Diğer programlar Windows ERRORLEVEL değerini inceleyerek bu kodu test edebilir. Çıkış kodu döndürmek için, `Main` `Sub` yordam yerine bir `Function` yordam olarak bildirmeniz gerekir.

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

- `Main`, bir `String` dizi bağımsız değişken olarak da alabilir. Dizideki her dize, programınızı çağırmak için kullanılan komut satırı bağımsız değişkenlerinden birini içerir. Değerlerine bağlı olarak farklı eylemler gerçekleştirebilirsiniz.

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

- Komut satırı bağımsız değişkenlerini incelemek için,ancakaşağıdakigibibirçıkışkodudöndürmezsiniz.`Main`

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
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [String Veri Türü](../../../visual-basic/language-reference/data-types/string-data-type.md)

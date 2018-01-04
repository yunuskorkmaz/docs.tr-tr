---
title: Visual Basic'de Ana Yordam
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6de98ad4e470cd0becaf25f5a9a00c8095e44b15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic'de Ana Yordam
Her Visual Basic uygulama çağrılan bir yordam içermelidir `Main`. Bu yordam görevi görür, başlangıç noktası ve genel olarak, uygulamanız için Denetim aynıdır. .NET Framework çağrıları, `Main` uygulamanızı yükledi ve denetim geçirmeye hazır olduğunda yordamı. Bir Windows Forms uygulaması oluşturmakta olduğunuz sürece yazmalısınız `Main` yordamı kendi çalışan uygulamalar için.  
  
 `Main`ilk çalışan bir kod içerir. İçinde `Main`, hangi formda bir program başlatıldığında önce yüklenmesi gereken belirlemek, uygulamanızı bir kopyası zaten sistemde çalışıp çalışmadığını öğrenmek, uygulamanız için değişkenleri kümesinin kurmak veya uygulama gerektiren bir veritabanını açın.  
  
## <a name="requirements-for-the-main-procedure"></a>Main yordamı için gereksinimleri  
 (Genellikle ile .exe uzantılı) kendi üzerinde çalıştığı bir dosyanın içermesi gereken bir `Main` yordamı. Bir kitaplıkla (örneğin uzantısı .dll) kendi çalıştırılmaz ve gerekli olmadığı bir `Main` yordamı. Oluşturabileceğiniz farklı proje türleri için gereksinimleri aşağıdaki gibidir:  
  
-   Konsol uygulamaları çalıştıracağınız kendi ve en az bir sağlamalısınız `Main` yordamı. biçimindeki telefon numarasıdır.  
  
-   Windows Forms uygulamaları kendi çalıştırın. Ancak, Visual Basic derleyici otomatik olarak oluşturan bir `Main` gibi yordamda bir uygulama ve gerekmez bir yazma.  
  
-   Sınıf kitaplıkları gerekli olmadığı bir `Main` yordamı. Bunlar, Windows Denetim kitaplıklar ve Web denetimi kitaplıkları içerir. Web uygulamaları sınıf kitaplıkları dağıtılır.  
  
## <a name="declaring-the-main-procedure"></a>Main yordamı bildirme  
 Bildirmek için dört yolla `Main` yordamı. Bağımsız değişkenler veya alabilir ve bir değer veya döndürebilir.  
  
> [!NOTE]
>  Bildirirseniz `Main` bir sınıfta kullanmalısınız `Shared` anahtar sözcüğü. Bir modüldeki `Main` olması gerekmez `Shared`.  
  
-   En basit yolu bildirmektir bir `Sub` olmayan bağımsız değişkenler almayan veya bir değer döndüren bir yordam.  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main`Ayrıca dönebilirsiniz bir `Integer` işletim sistemi çıkış kodu programınızın kullanır. değer. Diğer programları Windows ERRORLEVEL değerini inceleyerek bu kodu test edebilirsiniz. Bir çıkış kodu döndürülecek bildirmelisiniz `Main` olarak bir `Function` yordamı yerine bir `Sub` yordamı.  
  
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
  
-   `Main`Ayrıca gerçekleştirebileceğiniz bir `String` bağımsız değişken olarak bir dizi. Dizideki her dize programınızı çağırmak için kullanılan komut satırı bağımsız değişkenleri birini içerir. Değerlerine bağlı olarak farklı işlemler yapabilirsiniz.  
  
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
  
-   Bildirebilirsiniz `Main` komut satırı bağımsız değişkenleri inceleyin, ancak bir çıkış kodu gibi iade değil.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [Visual Basic programının yapısı](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [String Veri Türü](../../../visual-basic/language-reference/data-types/string-data-type.md)

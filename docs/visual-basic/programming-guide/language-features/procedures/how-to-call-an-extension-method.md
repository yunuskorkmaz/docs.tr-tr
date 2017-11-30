---
title: "Nasıl yapılır: Uzantı Metodu Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25b5a86af15694e6f64f96a5d5d645a01f8f1f12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="5fdaf-102">Nasıl yapılır: Uzantı Metodu Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fdaf-102">How to: Call an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="5fdaf-103">Genişletme yöntemleri, varolan bir sınıfa yöntemleri eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="5fdaf-104">Bir genişletme yöntemi bildirilen ve kapsam içine alındıktan sonra onu genişleyen türü gibi bir örnek yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="5fdaf-105">Uzantı metodu yazma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uzantı yöntemi yazma](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="5fdaf-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>  
  
 <span data-ttu-id="5fdaf-106">Genişletme yöntemi aşağıdaki yönergelere bakın `PrintAndPunctuate`, hangi, ne olursa olsun değer tarafından izlenen çağırır string örneği görüntüler için ikinci parametresi, gönderildiği `punc`.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="5fdaf-107">Bunu çağrıldığında yöntemi kapsamında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-107">The method must be in scope when it is called.</span></span>  
  
### <a name="to-call-an-extension-method"></a><span data-ttu-id="5fdaf-108">Bir genişletme yöntemi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="5fdaf-108">To call an extension method</span></span>  
  
1.  <span data-ttu-id="5fdaf-109">Uzantı yönteminin ilk parametresinin veri türüne sahip bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="5fdaf-110">İçin `PrintAndPunctuate`, gereksinim duyduğunuz bir <xref:System.String> değişkeni:</span><span class="sxs-lookup"><span data-stu-id="5fdaf-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  <span data-ttu-id="5fdaf-111">Değişkeni genişletme yöntemi çağırmak ve değeri ilk parametre olarak bağlanmıştır `aString`.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="5fdaf-112">Aşağıdaki arama deyimini görüntüler `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-112">The following calling statement will display `Ready?`.</span></span>  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     <span data-ttu-id="5fdaf-113">Bu uzantı yöntem çağrısı yalnızca görünen bildirim ister herhangi biri için bir çağrı <xref:System.String> örnek bir parametre gerekli yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="5fdaf-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  <span data-ttu-id="5fdaf-114">Başka bir dize değişkeni bildirme ve yeniden ile herhangi bir dize çalıştığını görmek için yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-114">Declare another string variable and call the method again to see that it works with any string.</span></span>  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     <span data-ttu-id="5fdaf-115">Bu süre sonucudur: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-115">The result this time is: `or not!!!`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fdaf-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fdaf-116">Example</span></span>  
 <span data-ttu-id="5fdaf-117">Aşağıdaki kod, tam bir örnek oluşturma ve basit genişletme yöntemi kullanımını ' dir.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports ConsoleApplication1.StringExtensions  
  
Module Module1  
  
    Sub Main()  
  
        Dim example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
        Dim example2 = "Goodbye"  
        example2.PrintAndPunctuate("?")  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
End Module  
  
' Output:  
' Hello.  
' Hello!!!!  
' Goodbye?  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fdaf-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fdaf-118">See Also</span></span>  
 [<span data-ttu-id="5fdaf-119">Nasıl yapılır: uzantı yöntemi yazma</span><span class="sxs-lookup"><span data-stu-id="5fdaf-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)  
 [<span data-ttu-id="5fdaf-120">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="5fdaf-120">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="5fdaf-121">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="5fdaf-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

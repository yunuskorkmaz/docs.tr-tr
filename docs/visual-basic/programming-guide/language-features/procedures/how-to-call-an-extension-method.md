---
title: 'Nasıl yapılır: Bir genişletme yöntemi çağırın (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: f2058162ab939d2619d7255c884d88c35ee63715
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512669"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="29c34-102">Nasıl yapılır: Bir genişletme yöntemi çağırın (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29c34-102">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="29c34-103">Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="29c34-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="29c34-104">Bir uzantı yöntemi bildirilip, kapsama getirildikten sonra, onu genişlettiği türün örnek yöntemi gibi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29c34-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="29c34-105">Uzantı yöntemi yazma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir genişletme yöntemi](./how-to-write-an-extension-method.md)yazın.</span><span class="sxs-lookup"><span data-stu-id="29c34-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="29c34-106">Aşağıdaki yönergeler, onu çağıran dize örneğini `PrintAndPunctuate`görüntüleyen ve ikinci `punc`parametresi için ' de gönderilen değer tarafından izlenen uzantı yöntemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="29c34-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

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

<span data-ttu-id="29c34-107">Yöntem çağrıldığında kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29c34-107">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="29c34-108">Bir genişletme yöntemini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="29c34-108">To call an extension method</span></span>

1. <span data-ttu-id="29c34-109">Uzantı yönteminin ilk parametresinin veri türüne sahip bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="29c34-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="29c34-110">İçin `PrintAndPunctuate` bir<xref:System.String> değişkene ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="29c34-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="29c34-111">Bu değişken, genişletme yöntemini çağıracaktır ve değeri ilk parametreye `aString`bağlanır.</span><span class="sxs-lookup"><span data-stu-id="29c34-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="29c34-112">Aşağıdaki çağırma deyimleri görüntülenecektir `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="29c34-112">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="29c34-113">Bu uzantı yöntemine yapılan çağrının, tek bir parametre gerektiren <xref:System.String> örnek metotlarından herhangi birine bir çağrı gibi göründüğünü unutmayın:</span><span class="sxs-lookup"><span data-stu-id="29c34-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="29c34-114">Başka bir dize değişkeni bildirin ve herhangi bir dizeyle çalıştığını görmek için yöntemi yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="29c34-114">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="29c34-115">Sonuç bu zaman: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="29c34-115">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="29c34-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="29c34-116">Example</span></span>
 <span data-ttu-id="29c34-117">Aşağıdaki kod, basit bir genişletme yönteminin oluşturulması ve kullanılması için bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="29c34-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="29c34-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29c34-118">See also</span></span>

- [<span data-ttu-id="29c34-119">Nasıl yapılır: Uzantı yöntemi yazma</span><span class="sxs-lookup"><span data-stu-id="29c34-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="29c34-120">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="29c34-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="29c34-121">Visual Basic kapsam</span><span class="sxs-lookup"><span data-stu-id="29c34-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

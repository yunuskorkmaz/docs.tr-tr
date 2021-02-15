---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: uzantı yöntemi çağırma (Visual Basic)'
title: 'Nasıl yapılır: Uzantı Yöntemi Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: ec5217526eb0cb28d172ab917df08a8bfe87fe95
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471389"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="e878e-103">Nasıl yapılır: Uzantı Metodu Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e878e-103">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="e878e-104">Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e878e-104">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="e878e-105">Bir uzantı yöntemi bildirilip, kapsama getirildikten sonra, onu genişlettiği türün örnek yöntemi gibi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e878e-105">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="e878e-106">Uzantı yöntemi yazma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzantı yöntemi yazma](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="e878e-106">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="e878e-107">Aşağıdaki yönergeler, `PrintAndPunctuate` onu çağıran dize örneğini görüntüleyen ve ikinci parametresi için ' de gönderilen değer tarafından izlenen uzantı yöntemini ifade eder `punc` .</span><span class="sxs-lookup"><span data-stu-id="e878e-107">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

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

<span data-ttu-id="e878e-108">Yöntem çağrıldığında kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e878e-108">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="e878e-109">Bir genişletme yöntemini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="e878e-109">To call an extension method</span></span>

1. <span data-ttu-id="e878e-110">Uzantı yönteminin ilk parametresinin veri türüne sahip bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="e878e-110">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="e878e-111">İçin `PrintAndPunctuate` bir değişkene ihtiyacınız vardır <xref:System.String> :</span><span class="sxs-lookup"><span data-stu-id="e878e-111">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="e878e-112">Bu değişken, genişletme yöntemini çağıracaktır ve değeri ilk parametreye bağlanır `aString` .</span><span class="sxs-lookup"><span data-stu-id="e878e-112">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="e878e-113">Aşağıdaki çağırma deyimleri görüntülenecektir `Ready?` .</span><span class="sxs-lookup"><span data-stu-id="e878e-113">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="e878e-114">Bu uzantı yöntemine yapılan çağrının, <xref:System.String> tek bir parametre gerektiren örnek metotlarından herhangi birine bir çağrı gibi göründüğünü unutmayın:</span><span class="sxs-lookup"><span data-stu-id="e878e-114">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="e878e-115">Başka bir dize değişkeni bildirin ve herhangi bir dizeyle çalıştığını görmek için yöntemi yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="e878e-115">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="e878e-116">Sonuç bu zaman: `or not!!!` .</span><span class="sxs-lookup"><span data-stu-id="e878e-116">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="e878e-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e878e-117">Example</span></span>

 <span data-ttu-id="e878e-118">Aşağıdaki kod, basit bir genişletme yönteminin oluşturulması ve kullanılması için bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e878e-118">The following code is a complete example of the creation and use of a simple extension method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e878e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e878e-119">See also</span></span>

- [<span data-ttu-id="e878e-120">Nasıl yapılır: Genişletme Yöntemi Yazma</span><span class="sxs-lookup"><span data-stu-id="e878e-120">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="e878e-121">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="e878e-121">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="e878e-122">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="e878e-122">Scope in Visual Basic</span></span>](../declared-elements/scope.md)

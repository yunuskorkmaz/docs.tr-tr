---
title: 'Nasıl yapılır: Uzantı metodu yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 31ccb18e0e6d1569764ec2a67201d7f758129425
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332756"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="e9e7c-102">Nasıl yapılır: Uzantı metodu yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9e7c-102">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="e9e7c-103">Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="e9e7c-104">Genişletme yöntemi, bu sınıfın bir örneği gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="e9e7c-105">Bir genişletme yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="e9e7c-105">To define an extension method</span></span>

1. <span data-ttu-id="e9e7c-106">Visual Studio 'da yeni veya mevcut bir Visual Basic uygulaması açın.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="e9e7c-107">Uzantı yöntemi tanımlamak istediğiniz dosyanın en üstünde, aşağıdaki içeri aktarma ifadesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e9e7c-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="e9e7c-108">Yeni veya mevcut uygulamanızdaki bir modül içinde, yöntem tanımını uzantı özniteliğiyle başlatın:</span><span class="sxs-lookup"><span data-stu-id="e9e7c-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>

    ```vb
    <Extension()>
    ```

4. <span data-ttu-id="e9e7c-109">Yöntemi sıradan bir şekilde bildirin, ancak ilk parametre türü genişletmek istediğiniz veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="e9e7c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9e7c-110">Example</span></span>

 <span data-ttu-id="e9e7c-111">Aşağıdaki örnek, `StringExtensions` modülünde bir genişletme yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="e9e7c-112">İkinci bir modül olan `Module1`, `StringExtensions` içeri aktarır ve yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="e9e7c-113">Uzantı yöntemi çağrıldığında kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="e9e7c-114">@No__t-0 uzantı metodu, <xref:System.String> sınıfını, dize örneğini görüntüleyen ve ardından parametre olarak gönderilen bir noktalama sembolleri dizesi olan bir yöntemle genişletir.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1
  
    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub
    
End Module
```
  
 <span data-ttu-id="e9e7c-115">Yöntemin iki parametre ile tanımlandığından ve yalnızca bir ile çağırdığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="e9e7c-116">Yöntem tanımındaki `aString` olan ilk parametre, yöntemi çağıran `String` örneği olan `example` ' e bağlanır.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="e9e7c-117">Örneğin çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e9e7c-117">The output of the example is as follows:</span></span>
  
 ```console
 Hello?
 Hello!!!!
 ```
  
## <a name="see-also"></a><span data-ttu-id="e9e7c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9e7c-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="e9e7c-119">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e9e7c-119">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="e9e7c-120">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="e9e7c-120">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="e9e7c-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e9e7c-121">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e9e7c-122">Visual Basic kapsam</span><span class="sxs-lookup"><span data-stu-id="e9e7c-122">Scope in Visual Basic</span></span>](../declared-elements/scope.md)

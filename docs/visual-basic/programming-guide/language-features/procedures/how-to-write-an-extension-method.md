---
title: 'Nasıl yapılır: Uzantı metodu yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631026"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="91f10-102">Nasıl yapılır: Uzantı metodu yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91f10-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="91f10-103">Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="91f10-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="91f10-104">Genişletme yöntemi, bu sınıfın bir örneği gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="91f10-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="91f10-105">Bir genişletme yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="91f10-105">To define an extension method</span></span>

1. <span data-ttu-id="91f10-106">Visual Studio 'da yeni veya mevcut bir Visual Basic uygulaması açın.</span><span class="sxs-lookup"><span data-stu-id="91f10-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="91f10-107">Uzantı yöntemi tanımlamak istediğiniz dosyanın en üstünde, aşağıdaki içeri aktarma ifadesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="91f10-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="91f10-108">Yeni veya mevcut uygulamanızdaki bir modül içinde, yöntem tanımını uzantı özniteliğiyle başlatın:</span><span class="sxs-lookup"><span data-stu-id="91f10-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>

    ```vb
    <Extension()>
    ```

4. <span data-ttu-id="91f10-109">Yöntemi sıradan bir şekilde bildirin, ancak ilk parametre türü genişletmek istediğiniz veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91f10-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="91f10-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="91f10-110">Example</span></span>
 <span data-ttu-id="91f10-111">Aşağıdaki örnek, modülünde `StringExtensions`bir genişletme yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="91f10-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="91f10-112">İkinci bir modül, `Module1`yöntemini içeri `StringExtensions` aktarır ve çağırır.</span><span class="sxs-lookup"><span data-stu-id="91f10-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="91f10-113">Uzantı yöntemi çağrıldığında kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91f10-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="91f10-114">Genişletme yöntemi `PrintAndPunctuate` , <xref:System.String> sınıfını bir parametre olarak gönderilen bir noktalama sembolleri dizesi gelen dize örneğini görüntüleyen bir yöntemle genişletir.</span><span class="sxs-lookup"><span data-stu-id="91f10-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
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
  
 <span data-ttu-id="91f10-115">Yöntemin iki parametre ile tanımlandığından ve yalnızca bir ile çağırdığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="91f10-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="91f10-116">Yöntem tanımındaki ilk parametre `aString`, yöntemini çağıran örneği `String` olan öğesine `example`bağlanır.</span><span class="sxs-lookup"><span data-stu-id="91f10-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="91f10-117">Örneğin çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="91f10-117">The output of the example is as follows:</span></span>
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="91f10-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91f10-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="91f10-119">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="91f10-119">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="91f10-120">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="91f10-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="91f10-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="91f10-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="91f10-122">Visual Basic kapsam</span><span class="sxs-lookup"><span data-stu-id="91f10-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

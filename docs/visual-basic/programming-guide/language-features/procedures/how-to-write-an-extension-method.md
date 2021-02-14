---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: uzantı yöntemi yazma (Visual Basic)'
title: 'Nasıl yapılır: Uzantı Metodu Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 4c5d88976e55288ccb350ab82d459db0a23f468e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476195"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="fb745-103">Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb745-103">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="fb745-104">Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb745-104">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="fb745-105">Genişletme yöntemi, bu sınıfın bir örneği gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="fb745-105">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="fb745-106">Bir genişletme yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="fb745-106">To define an extension method</span></span>

1. <span data-ttu-id="fb745-107">Visual Studio 'da yeni veya mevcut bir Visual Basic uygulaması açın.</span><span class="sxs-lookup"><span data-stu-id="fb745-107">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="fb745-108">Uzantı yöntemi tanımlamak istediğiniz dosyanın en üstünde, aşağıdaki içeri aktarma ifadesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fb745-108">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="fb745-109">Yeni veya mevcut uygulamanızdaki bir modül içinde, yöntem tanımını [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) özniteliğiyle başlatın:</span><span class="sxs-lookup"><span data-stu-id="fb745-109">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```

    <span data-ttu-id="fb745-110">`Extension`Özniteliğinin yalnızca bir Visual Basic modülündeki bir yönteme ( `Sub` veya `Function` yordama) uygulanabileceğini unutmayın. [](../../../language-reference/statements/module-statement.md)</span><span class="sxs-lookup"><span data-stu-id="fb745-110">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="fb745-111">Bunu bir veya a içindeki bir yönteme uygularsanız, `Class` `Structure` Visual Basic Derleyicisi Hata [BC36551](../../../misc/bc36551.md)oluşturuyor, "uzantı yöntemleri yalnızca modüllerde tanımlanabilir."</span><span class="sxs-lookup"><span data-stu-id="fb745-111">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="fb745-112">Yöntemi sıradan bir şekilde bildirin, ancak ilk parametre türü genişletmek istediğiniz veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb745-112">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="fb745-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb745-113">Example</span></span>

<span data-ttu-id="fb745-114">Aşağıdaki örnek, modülünde bir genişletme yöntemi bildirir `StringExtensions` .</span><span class="sxs-lookup"><span data-stu-id="fb745-114">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="fb745-115">İkinci bir modül, `Module1` yöntemini içeri aktarır `StringExtensions` ve çağırır.</span><span class="sxs-lookup"><span data-stu-id="fb745-115">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="fb745-116">Uzantı yöntemi çağrıldığında kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb745-116">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="fb745-117">Genişletme yöntemi `PrintAndPunctuate` , <xref:System.String> sınıfını bir parametre olarak gönderilen bir noktalama sembolleri dizesi gelen dize örneğini görüntüleyen bir yöntemle genişletir.</span><span class="sxs-lookup"><span data-stu-id="fb745-117">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>

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

<span data-ttu-id="fb745-118">Yöntemin iki parametre ile tanımlandığından ve yalnızca bir ile çağırdığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fb745-118">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="fb745-119">Yöntem tanımındaki ilk parametre, `aString` `example` `String` yöntemini çağıran örneği olan öğesine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="fb745-119">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="fb745-120">Örneğin çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fb745-120">The output of the example is as follows:</span></span>

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a><span data-ttu-id="fb745-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb745-121">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="fb745-122">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="fb745-122">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="fb745-123">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="fb745-123">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="fb745-124">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="fb745-124">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fb745-125">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="fb745-125">Scope in Visual Basic</span></span>](../declared-elements/scope.md)

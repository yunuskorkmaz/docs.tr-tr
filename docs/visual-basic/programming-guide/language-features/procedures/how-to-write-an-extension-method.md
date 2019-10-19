---
title: 'Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 4671728330614f0f3da23fd90f5e635ddcf46578
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581151"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="df39c-102">Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df39c-102">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="df39c-103">Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="df39c-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="df39c-104">Genişletme yöntemi, bu sınıfın bir örneği gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="df39c-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="df39c-105">Bir genişletme yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="df39c-105">To define an extension method</span></span>

1. <span data-ttu-id="df39c-106">Visual Studio 'da yeni veya mevcut bir Visual Basic uygulaması açın.</span><span class="sxs-lookup"><span data-stu-id="df39c-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="df39c-107">Uzantı yöntemi tanımlamak istediğiniz dosyanın en üstünde, aşağıdaki içeri aktarma ifadesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="df39c-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="df39c-108">Yeni veya mevcut uygulamanızdaki bir modül içinde [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) özniteliğiyle yöntem tanımını başlatın:</span><span class="sxs-lookup"><span data-stu-id="df39c-108">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```

    <span data-ttu-id="df39c-109">@No__t_0 özniteliğinin bir Visual Basic [modülünde](../../../language-reference/statements/module-statement.md)yalnızca bir yönteme (bir `Sub` veya `Function` yordamına) uygulanabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="df39c-109">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="df39c-110">Bunu bir `Class` veya `Structure` ' deki bir yönteme uygularsanız, Visual Basic Derleyicisi Hata [BC36551](../../../misc/bc36551.md)oluşturuyor, "uzantı yöntemleri yalnızca modüllerde tanımlanabilir."</span><span class="sxs-lookup"><span data-stu-id="df39c-110">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="df39c-111">Yöntemi sıradan bir şekilde bildirin, ancak ilk parametre türü genişletmek istediğiniz veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df39c-111">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="df39c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="df39c-112">Example</span></span>

<span data-ttu-id="df39c-113">Aşağıdaki örnek, `StringExtensions` modülünde bir genişletme yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="df39c-113">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="df39c-114">İkinci bir modül olan `Module1`, `StringExtensions` içeri aktarır ve yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="df39c-114">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="df39c-115">Uzantı yöntemi çağrıldığında kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df39c-115">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="df39c-116">Genişletme yöntemi `PrintAndPunctuate` <xref:System.String> sınıfını bir parametre olarak gönderilen bir noktalama sembolleri dizesi tarafından izlenen bir yöntem ile genişletir.</span><span class="sxs-lookup"><span data-stu-id="df39c-116">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>

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

<span data-ttu-id="df39c-117">Yöntemin iki parametre ile tanımlandığından ve yalnızca bir ile çağırdığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="df39c-117">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="df39c-118">Yöntem tanımındaki `aString` olan ilk parametre, yöntemi çağıran `String` örneği olan `example` ' e bağlanır.</span><span class="sxs-lookup"><span data-stu-id="df39c-118">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="df39c-119">Örneğin çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="df39c-119">The output of the example is as follows:</span></span>

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a><span data-ttu-id="df39c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df39c-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="df39c-121">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="df39c-121">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="df39c-122">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="df39c-122">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="df39c-123">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="df39c-123">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="df39c-124">Visual Basic kapsam</span><span class="sxs-lookup"><span data-stu-id="df39c-124">Scope in Visual Basic</span></span>](../declared-elements/scope.md)

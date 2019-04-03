---
title: 'Nasıl yapılır: (Visual Basic) uzantı metodu yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: d6f8b85945bd400d1f4b54a50260d72c750add8b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819126"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="cc28b-102">Nasıl yapılır: (Visual Basic) uzantı metodu yazma</span><span class="sxs-lookup"><span data-stu-id="cc28b-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="cc28b-103">Genişletme yöntemleri varolan bir sınıfa yöntemler eklemenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="cc28b-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="cc28b-104">Bu sınıfın bir örneğini değilmiş gibi uzantı metodu volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="cc28b-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="cc28b-105">Bir genişletme yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="cc28b-105">To define an extension method</span></span>  
  
1.  <span data-ttu-id="cc28b-106">Yeni veya mevcut bir Visual Basic uygulamaları Visual Studio'da açın.</span><span class="sxs-lookup"><span data-stu-id="cc28b-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="cc28b-107">Bir genişletme yöntemi tanımlamak istediğiniz dosyasının en üstüne aşağıdaki içeri aktarma deyimi içerir:</span><span class="sxs-lookup"><span data-stu-id="cc28b-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  <span data-ttu-id="cc28b-108">İçinde bir modül, yeni veya mevcut uygulamanızda uzantı özniteliğine sahip yöntem tanımını başlayın:</span><span class="sxs-lookup"><span data-stu-id="cc28b-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4.  <span data-ttu-id="cc28b-109">Dışında ilk parametresinin türü genişletmek istediğiniz veri türünde olmalıdır, yöntemi normal şekilde bildirin.</span><span class="sxs-lookup"><span data-stu-id="cc28b-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="cc28b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc28b-110">Example</span></span>  
 <span data-ttu-id="cc28b-111">Aşağıdaki örnek, bir genişletme yöntemi modülünde bildirir `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="cc28b-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="cc28b-112">İkinci bir modül `Module1`, aktarır `StringExtensions` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="cc28b-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="cc28b-113">Genişletme yöntemi, çağrıldığı zaman kapsamda olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc28b-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="cc28b-114">Genişletme yöntemi `PrintAndPunctuate` genişletir <xref:System.String> sınıfı dize örneğinde görüntüleyen bir yöntem ile ardından noktalama simgeleri parametre olarak gönderilen bir dize.</span><span class="sxs-lookup"><span data-stu-id="cc28b-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
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
  
 <span data-ttu-id="cc28b-115">Yöntemi iki parametre ile tanımlanmıştır ve yalnızca bir adı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cc28b-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="cc28b-116">İlk parametre `aString`, yöntem tanımını bağlı `example`, örneğini `String` yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="cc28b-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="cc28b-117">Örnek çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="cc28b-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="cc28b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc28b-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="cc28b-119">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="cc28b-119">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="cc28b-120">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="cc28b-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="cc28b-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cc28b-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cc28b-122">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="cc28b-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

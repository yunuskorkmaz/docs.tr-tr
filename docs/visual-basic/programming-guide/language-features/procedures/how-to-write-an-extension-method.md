---
title: "Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cdabf59886e7457a327ee9cde968a6a73f2280
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="f7d7b-102">Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7d7b-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="f7d7b-103">Genişletme yöntemleri, varolan bir sınıfa yöntemleri eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="f7d7b-104">Bu sınıfın örneğini değilmiş gibi genişletme yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="f7d7b-105">Bir genişletme yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="f7d7b-105">To define an extension method</span></span>  
  
1.  <span data-ttu-id="f7d7b-106">Yeni veya varolan bir Visual Basic uygulama Visual Studio'da açın.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f7d7b-107">Bir genişletme yöntemi tanımlamak istediğiniz dosyanın üst kısmında, aşağıdaki içeri aktarma deyimini şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f7d7b-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  <span data-ttu-id="f7d7b-108">Yeni veya var olan uygulamanızı modülde içinde uzantısı özniteliği yöntemi tanımıyla başlayın:</span><span class="sxs-lookup"><span data-stu-id="f7d7b-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4.  <span data-ttu-id="f7d7b-109">İlk parametre türü, genişletmek istediğiniz veri türü olmalıdır dışında yönteminizi normal şekilde bildirin.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="f7d7b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7d7b-110">Example</span></span>  
 <span data-ttu-id="f7d7b-111">Aşağıdaki örnekte bir genişletme yöntemi modülünde bildirir `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="f7d7b-112">İkinci bir modül `Module1`, alır `StringExtensions` ve yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="f7d7b-113">Bunu çağrıldığında genişletme yöntemi kapsamında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="f7d7b-114">Genişletme yöntemi `PrintAndPunctuate` genişletir <xref:System.String> noktalama simge parametre olarak gönderilen bir dize arkasından sınıfı string örneği görüntüleyen bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
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
  
 <span data-ttu-id="f7d7b-115">Yöntemi iki parametre ile tanımlanan ve yalnızca biriyle adlı dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="f7d7b-116">İlk parametre `aString`, yönteminde tanımı bağlı `example`, örneğinin `String` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="f7d7b-117">Örnek çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f7d7b-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="f7d7b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7d7b-118">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [<span data-ttu-id="f7d7b-119">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="f7d7b-119">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="f7d7b-120">Module deyimi</span><span class="sxs-lookup"><span data-stu-id="f7d7b-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="f7d7b-121">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="f7d7b-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="f7d7b-122">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="f7d7b-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

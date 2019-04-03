---
title: 'Nasıl yapılır: (Visual Basic) uzantı metodu çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 2543694e6bf8da5b67ecaccc92633a8448154063
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837144"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="018ef-102">Nasıl yapılır: (Visual Basic) uzantı metodu çağırma</span><span class="sxs-lookup"><span data-stu-id="018ef-102">How to: Call an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="018ef-103">Genişletme yöntemleri varolan bir sınıfa yöntemler eklemenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="018ef-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="018ef-104">Bir genişletme yöntemi bildirildi ve kapsama alınır sonra bunu genişleten türü gibi bir örnek yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="018ef-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="018ef-105">Uzantı metodu yazma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Uzantı metodu yazma](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="018ef-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>  
  
 <span data-ttu-id="018ef-106">Genişletme yöntemi için aşağıdaki yönergelere bakın `PrintAndPunctuate`, hangi değere göre ve ardından onu çağıran dize örneğinde görüntüler, ikinci parametresi, gönderildiği `punc`.</span><span class="sxs-lookup"><span data-stu-id="018ef-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>  
  
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
  
 <span data-ttu-id="018ef-107">Çağrıldığında, yöntemi kapsam içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="018ef-107">The method must be in scope when it is called.</span></span>  
  
### <a name="to-call-an-extension-method"></a><span data-ttu-id="018ef-108">Bir uzantı yöntemini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="018ef-108">To call an extension method</span></span>  
  
1.  <span data-ttu-id="018ef-109">Genişletme yönteminin ilk parametresi için veri türüne sahip bir değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="018ef-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="018ef-110">İçin `PrintAndPunctuate`, gereksinim duyduğunuz bir <xref:System.String> değişkeni:</span><span class="sxs-lookup"><span data-stu-id="018ef-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  <span data-ttu-id="018ef-111">Değişkeni genişletme yöntemini çağırmak ve değeri ilk parametre olarak bağlı `aString`.</span><span class="sxs-lookup"><span data-stu-id="018ef-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="018ef-112">Aşağıdaki deyim çağırma görüntüler `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="018ef-112">The following calling statement will display `Ready?`.</span></span>  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     <span data-ttu-id="018ef-113">Bu uzantı yöntemine çağrı yalnızca görünen bildirim ister bir çağrı herhangi birine <xref:System.String> örneği bir parametre gerektiren yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="018ef-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  <span data-ttu-id="018ef-114">Başka bir dize değişkeni bildirme ve yeniden herhangi bir dize ile çalışır durumda olduğunu görmek için yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="018ef-114">Declare another string variable and call the method again to see that it works with any string.</span></span>  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     <span data-ttu-id="018ef-115">Bu süre sonucudur: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="018ef-115">The result this time is: `or not!!!`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="018ef-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="018ef-116">Example</span></span>  
 <span data-ttu-id="018ef-117">Aşağıdaki kod, tam bir örnek oluşturma ve basit bir uzantı yönteminin kullanılmasını ' dir.</span><span class="sxs-lookup"><span data-stu-id="018ef-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="018ef-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="018ef-118">See also</span></span>

- [<span data-ttu-id="018ef-119">Nasıl yapılır: Uzantı metodu yazma</span><span class="sxs-lookup"><span data-stu-id="018ef-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="018ef-120">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="018ef-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="018ef-121">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="018ef-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

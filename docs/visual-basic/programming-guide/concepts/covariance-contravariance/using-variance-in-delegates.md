---
title: Temsilcilerde varyans (Visual Basic) kullanma
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: c2390d95bd6bab9f5625c6ec08c374f469f1fc55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644140"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="2a09d-102">Temsilcilerde varyans (Visual Basic) kullanma</span><span class="sxs-lookup"><span data-stu-id="2a09d-102">Using Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="2a09d-103">Bir temsilci için bir yöntem atadığınızda *Kovaryans* ve *değişken karşıtı* yöntemi imza bir temsilci türüyle eşleştirmek için esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a09d-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="2a09d-104">Kovaryans temsilci içinde tanımlanan daha fazla türetilmiş dönüş türüne sahip bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="2a09d-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="2a09d-105">Değişken karşıtı temsilci türü olandan daha az türetilmiş parametre türleri içeren bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="2a09d-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="2a09d-106">Örnek 1: kovaryansı</span><span class="sxs-lookup"><span data-stu-id="2a09d-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="2a09d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a09d-107">Description</span></span>  
 <span data-ttu-id="2a09d-108">Bu örnek, temsilci imza dönüş türden türetilmiş dönüş türlerine sahip yöntemleriyle temsilciler'ın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a09d-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="2a09d-109">Tarafından döndürülen veri türünü `DogsHandler` türü `Dogs`, den türetilen `Mammals` temsilci tanımlanan türü.</span><span class="sxs-lookup"><span data-stu-id="2a09d-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2a09d-110">Kod</span><span class="sxs-lookup"><span data-stu-id="2a09d-110">Code</span></span>  
  
```vb  
Class Mammals  
End Class  
  
Class Dogs  
    Inherits Mammals  
End Class  
Class Test  
    Public Delegate Function HandlerMethod() As Mammals  
    Public Shared Function MammalsHandler() As Mammals  
        Return Nothing  
    End Function  
    Public Shared Function DogsHandler() As Dogs  
        Return Nothing  
    End Function  
    Sub Test()  
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler  
        ' Covariance enables this assignment.  
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler  
    End Sub  
End Class  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="2a09d-111">Örnek 2: değişken karşıtı</span><span class="sxs-lookup"><span data-stu-id="2a09d-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="2a09d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a09d-112">Description</span></span>  
 <span data-ttu-id="2a09d-113">Bu örnek temsilciler türünün temel türleri temsilci imza parametre türü parametrelerine sahip yöntemleriyle nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a09d-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="2a09d-114">Değişken karşıtı ile bir olay işleyicisi yerine ayrı işleyicileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a09d-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="2a09d-115">Örneğin, kabul eden olay işleyicisi oluşturabilirsiniz bir `EventArgs` giriş parametresi ve onunla kullanmak bir `Button.MouseClick` gönderir olay bir `MouseEventArgs` türünü bir parametre olarak ve ile bir `TextBox.KeyDown` gönderir olay bir `KeyEventArgs` parametresi.</span><span class="sxs-lookup"><span data-stu-id="2a09d-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2a09d-116">Kod</span><span class="sxs-lookup"><span data-stu-id="2a09d-116">Code</span></span>  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
Private Sub MultiHandler(ByVal sender As Object,  
                         ByVal e As System.EventArgs)  
    Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Form1_Load(ByVal sender As System.Object,  
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
    ' You can use a method that has an EventArgs parameter,  
    ' although the event expects the KeyEventArgs parameter.  
    AddHandler Button1.KeyDown, AddressOf MultiHandler  
  
    ' You can use the same method   
    ' for the event that expects the MouseEventArgs parameter.  
    AddHandler Button1.MouseClick, AddressOf MultiHandler  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a09d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a09d-117">See Also</span></span>  
 [<span data-ttu-id="2a09d-118">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a09d-118">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [<span data-ttu-id="2a09d-119">İşlev ve eylem genel temsilciler (Visual Basic) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="2a09d-119">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)

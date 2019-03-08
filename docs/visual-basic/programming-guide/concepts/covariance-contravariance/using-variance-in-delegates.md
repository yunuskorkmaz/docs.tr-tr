---
title: Temsilcilerde varyans (Visual Basic) kullanma
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 19eb3070c1b8359a4eb050e7cf2f16622f66ebe9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679802"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="10360-102">Temsilcilerde varyans (Visual Basic) kullanma</span><span class="sxs-lookup"><span data-stu-id="10360-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="10360-103">Bir temsilci için bir yöntem atadığınızda *Kovaryans* ve *kontravaryans* yöntem imzasını bir temsilci türüyle eşleştirmek için esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="10360-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="10360-104">Kovaryans Temsilcide tanımlanan daha fazla türetilmiş dönüş türüne sahip bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="10360-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="10360-105">Kontravaryans, temsilci türü olanlardan daha az türetilmiş parametre türleri olan bir yönteme izin verir.</span><span class="sxs-lookup"><span data-stu-id="10360-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="10360-106">Örnek 1: Kovaryans</span><span class="sxs-lookup"><span data-stu-id="10360-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="10360-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10360-107">Description</span></span>

<span data-ttu-id="10360-108">Bu örnekte, temsilci imzasında dönüş türünden türetilmiş dönüş türlerine sahip yöntemler ile temsilciler'ın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="10360-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="10360-109">Tarafından döndürülen veri türünü `DogsHandler` türünde `Dogs`, öğesinden türetildiğini `Mammals` Temsilcide tanımlanan tür.</span><span class="sxs-lookup"><span data-stu-id="10360-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="10360-110">Kod</span><span class="sxs-lookup"><span data-stu-id="10360-110">Code</span></span>

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

## <a name="example-2-contravariance"></a><span data-ttu-id="10360-111">Örnek 2: Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="10360-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="10360-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10360-112">Description</span></span>

<span data-ttu-id="10360-113">Bu örnek, bir türün temsilci imzası parametre türü temel tür parametreleri olan yöntemler ile temsilciler nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="10360-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="10360-114">Kontravaryans ile ayrı işleyicileri yerine bir olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10360-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="10360-115">Kabul eden bir olay işleyicisi oluşturma gibi bir `EventArgs` giriş parametresi ve kullanılmakta olan bir `Button.MouseClick` gönderen olay bir `MouseEventArgs` türü bir parametre olarak ve ile bir `TextBox.KeyDown` gönderen olay bir `KeyEventArgs` parametresi.</span><span class="sxs-lookup"><span data-stu-id="10360-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>

### <a name="code"></a><span data-ttu-id="10360-116">Kod</span><span class="sxs-lookup"><span data-stu-id="10360-116">Code</span></span>

```vb
' Event handler that accepts a parameter of the EventArgs type.
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

## <a name="see-also"></a><span data-ttu-id="10360-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10360-117">See also</span></span>

- [<span data-ttu-id="10360-118">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10360-118">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="10360-119">İşlev ve eylem genel temsilcileri (Visual Basic) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="10360-119">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)

---
title: Temsilcilerde varyans kullanma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: ebba7e862e1b4677d9438aa301ef2b713fba3712
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169076"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="46689-102">Temsilcilerde varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46689-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="46689-103">Bir temsilciye bir yöntem atadığınızda, *Kovaryans* ve *değişken varyans* , bir temsilci türünü Yöntem imzasıyla eşleştirmek için esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="46689-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="46689-104">Kovaryans, bir metodun, temsilde tanımlı olandan daha fazla türetilmiş dönüş türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="46689-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="46689-105">Değişken Varyans, temsilci türünden daha az türetilmiş parametre türlerine sahip bir yönteme izin verir.</span><span class="sxs-lookup"><span data-stu-id="46689-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="46689-106">Örnek 1: Ko</span><span class="sxs-lookup"><span data-stu-id="46689-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="46689-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46689-107">Description</span></span>

<span data-ttu-id="46689-108">Bu örnek, temsilci imzasında dönüş türünden türetilmiş dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46689-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="46689-109">Tarafından `DogsHandler` döndürülen veri `Dogs` türü`Mammals` , temsilde tanımlanan türden türetilen türüdür.</span><span class="sxs-lookup"><span data-stu-id="46689-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="46689-110">Kod</span><span class="sxs-lookup"><span data-stu-id="46689-110">Code</span></span>

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

## <a name="example-2-contravariance"></a><span data-ttu-id="46689-111">Örnek 2: Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="46689-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="46689-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46689-112">Description</span></span>

<span data-ttu-id="46689-113">Bu örnek, temsilci imza parametre türünün temel türleri olan parametrelere sahip Yöntemler ile temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46689-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="46689-114">Değişken varyans ile ayrı işleyiciler yerine bir olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46689-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="46689-115">Aşağıdaki örnek iki temsilcinin kullanımını sağlar:</span><span class="sxs-lookup"><span data-stu-id="46689-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="46689-116"><xref:System.Windows.Forms.KeyEventHandler> [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) olayının imzasını tanımlayan bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="46689-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="46689-117">İmzası:</span><span class="sxs-lookup"><span data-stu-id="46689-117">Its signature is:</span></span>

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- <span data-ttu-id="46689-118"><xref:System.Windows.Forms.MouseEventHandler> [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) olayının imzasını tanımlayan bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="46689-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="46689-119">İmzası:</span><span class="sxs-lookup"><span data-stu-id="46689-119">Its signature is:</span></span>

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

<span data-ttu-id="46689-120">Örnek, <xref:System.EventArgs> parametresiyle bir olay işleyicisini tanımlar ve `Button.KeyDown` hem hem de `Button.MouseClick` olaylarını işlemek için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="46689-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="46689-121">Bu <xref:System.EventArgs> <xref:System.Windows.Forms.KeyEventArgs> ,<xref:System.Windows.Forms.MouseEventArgs>hem hem de temel türü olduğundan bunu yapabilir.</span><span class="sxs-lookup"><span data-stu-id="46689-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>

### <a name="code"></a><span data-ttu-id="46689-122">Kod</span><span class="sxs-lookup"><span data-stu-id="46689-122">Code</span></span>

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

## <a name="see-also"></a><span data-ttu-id="46689-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46689-123">See also</span></span>

- [<span data-ttu-id="46689-124">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46689-124">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="46689-125">Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46689-125">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)

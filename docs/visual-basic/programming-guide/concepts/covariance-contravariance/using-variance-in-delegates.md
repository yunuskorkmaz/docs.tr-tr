---
title: Temsilcilerde Varyans Kullanma
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 9c2aad0e4b9408939600938412fe5c3e73b5bf15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349025"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="b0043-102">Temsilcilerde varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0043-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="b0043-103">Bir temsilciye bir yöntem atadığınızda, *Kovaryans* ve *değişken varyans* , bir temsilci türünü Yöntem imzasıyla eşleştirmek için esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0043-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="b0043-104">Kovaryans, bir metodun, temsilde tanımlı olandan daha fazla türetilmiş dönüş türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0043-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="b0043-105">Değişken Varyans, temsilci türünden daha az türetilmiş parametre türlerine sahip bir yönteme izin verir.</span><span class="sxs-lookup"><span data-stu-id="b0043-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="b0043-106">Örnek 1: Kovaryans</span><span class="sxs-lookup"><span data-stu-id="b0043-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="b0043-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0043-107">Description</span></span>

<span data-ttu-id="b0043-108">Bu örnek, temsilci imzasında dönüş türünden türetilmiş dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0043-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="b0043-109">`DogsHandler` tarafından döndürülen veri türü, temsilde tanımlanan `Mammals` türünden türetilen `Dogs`türüdür.</span><span class="sxs-lookup"><span data-stu-id="b0043-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="b0043-110">Kod</span><span class="sxs-lookup"><span data-stu-id="b0043-110">Code</span></span>

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

## <a name="example-2-contravariance"></a><span data-ttu-id="b0043-111">Örnek 2: değişken varyans</span><span class="sxs-lookup"><span data-stu-id="b0043-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="b0043-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0043-112">Description</span></span>

<span data-ttu-id="b0043-113">Bu örnek, temsilci imza parametre türünün temel türleri olan parametrelere sahip Yöntemler ile temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0043-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="b0043-114">Değişken varyans ile ayrı işleyiciler yerine bir olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0043-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="b0043-115">Aşağıdaki örnek iki temsilcinin kullanımını sağlar:</span><span class="sxs-lookup"><span data-stu-id="b0043-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="b0043-116">[Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) olayının imzasını tanımlayan bir <xref:System.Windows.Forms.KeyEventHandler> temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="b0043-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="b0043-117">İmzası:</span><span class="sxs-lookup"><span data-stu-id="b0043-117">Its signature is:</span></span>

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- <span data-ttu-id="b0043-118">[Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) olayının imzasını tanımlayan bir <xref:System.Windows.Forms.MouseEventHandler> temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="b0043-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="b0043-119">İmzası:</span><span class="sxs-lookup"><span data-stu-id="b0043-119">Its signature is:</span></span>

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

<span data-ttu-id="b0043-120">Örnek, <xref:System.EventArgs> parametresine sahip bir olay işleyicisini tanımlar ve `Button.KeyDown` ve `Button.MouseClick` olaylarını işlemek için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0043-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="b0043-121"><xref:System.EventArgs>, hem <xref:System.Windows.Forms.KeyEventArgs> hem de <xref:System.Windows.Forms.MouseEventArgs>temel türü olduğundan bunu yapabilir.</span><span class="sxs-lookup"><span data-stu-id="b0043-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>

### <a name="code"></a><span data-ttu-id="b0043-122">Kod</span><span class="sxs-lookup"><span data-stu-id="b0043-122">Code</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b0043-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0043-123">See also</span></span>

- [<span data-ttu-id="b0043-124">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0043-124">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="b0043-125">Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0043-125">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)

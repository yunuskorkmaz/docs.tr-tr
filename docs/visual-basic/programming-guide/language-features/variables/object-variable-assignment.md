---
title: Nesne Değişkeni Ataması
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 9ae1a307e8c886166d516140b7f100a411cedcfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410380"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="d3ac9-102">Nesne Değişkeni Ataması (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3ac9-102">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="d3ac9-103">Bir nesne değişkenine bir nesne atamak için normal atama ifadesini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="d3ac9-104">Aşağıdaki örnekte gösterildiği gibi bir nesne ifadesi veya [Nothing](../../../language-reference/nothing.md) anahtar sözcüğü atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-104">You can assign an object expression or the [Nothing](../../../language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="d3ac9-105">`Nothing`Şu anda değişkene atanmış bir nesne olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-105">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="d3ac9-106">Başlatma</span><span class="sxs-lookup"><span data-stu-id="d3ac9-106">Initialization</span></span>

<span data-ttu-id="d3ac9-107">Kodunuz çalışmaya başladığında, nesne değişkenleriniz olarak başlatılır `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="d3ac9-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="d3ac9-108">Bildirimleri başlatma dahil olanlar, bildirim deyimleri yürütüldüğünde belirttiğiniz değerlere yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="d3ac9-109">[Yeni](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü kullanarak bildirimindeki başlatmayı dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-109">You can include initialization in your declaration by using the [New](../../../language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="d3ac9-110">Aşağıdaki bildirim deyimleri, nesne değişkenlerini bildirir `testUri` ve `ver` bunlara belirli nesneler atar.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="d3ac9-111">Her biri, nesneyi başlatmak için uygun sınıfın aşırı yüklenmiş oluşturucularından birini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="d3ac9-112">Disassociation tamamlayamadı</span><span class="sxs-lookup"><span data-stu-id="d3ac9-112">Disassociation</span></span>

<span data-ttu-id="d3ac9-113">Bir nesne değişkenini `Nothing` , değişkenin ilişkilendirmesini belirli bir nesneyle devam ettirir şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="d3ac9-114">Bu, değişkeni değiştirerek nesneyi yanlışlıkla değiştirmenizi önler.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="d3ac9-115">Ayrıca, aşağıdaki örnekte gösterildiği gibi, nesne değişkeninin geçerli bir nesneye işaret edilip edilmeyeceğini test etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="d3ac9-116">Değişkeninizin başvurduğu nesne başka bir uygulamada ise, bu test uygulamanın sonlandırılıp sonlandırılmadığını veya yalnızca geçersiz kılınmadığını belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="d3ac9-117">Değerine sahip bir nesne değişkeni `Nothing` de *null başvuru*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="d3ac9-118">Geçerli örnek</span><span class="sxs-lookup"><span data-stu-id="d3ac9-118">Current Instance</span></span>

<span data-ttu-id="d3ac9-119">Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="d3ac9-120">Tüm kod bir yordam içinde yürütüldüğü için, geçerli örnek yordamın çağrıldığı bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="d3ac9-121">`Me`Anahtar sözcüğü, geçerli örneğe başvuran bir nesne değişkeni işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="d3ac9-122">Bir yordam [paylaşılmışsa](../../../language-reference/modifiers/shared.md), `Me` geçerli örneğe bir işaretçi almak için anahtar sözcüğünü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-122">If a procedure is not [Shared](../../../language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="d3ac9-123">Paylaşılan yordamlar bir sınıfın belirli bir örneğiyle ilişkilendirilemez.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="d3ac9-124">Kullanmak, `Me` özellikle geçerli örneği başka bir modüldeki yordama geçirmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="d3ac9-125">Örneğin, bir dizi XML belgeniz olduğunu ve bunlara bazı standart metinler ekleneceğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="d3ac9-126">Aşağıdaki örnek bunu yapmak için bir yordam tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-126">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="d3ac9-127">Her XML belge nesnesi, yordamı çağırabilir ve geçerli örneğini bir bağımsız değişken olarak geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="d3ac9-128">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-128">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="d3ac9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3ac9-129">See also</span></span>

- [<span data-ttu-id="d3ac9-130">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="d3ac9-130">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="d3ac9-131">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="d3ac9-131">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="d3ac9-132">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="d3ac9-132">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="d3ac9-133">Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama</span><span class="sxs-lookup"><span data-stu-id="d3ac9-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="d3ac9-134">Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama</span><span class="sxs-lookup"><span data-stu-id="d3ac9-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="d3ac9-135">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="d3ac9-135">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)

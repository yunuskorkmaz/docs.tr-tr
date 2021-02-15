---
description: 'Daha fazla bilgi edinin: nesne değişkeni ataması (Visual Basic)'
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
ms.openlocfilehash: ac5e534a03d651a23e651e1049477b2bd0769b82
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481655"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="ef0b7-103">Nesne Değişkeni Ataması (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef0b7-103">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="ef0b7-104">Bir nesne değişkenine bir nesne atamak için normal atama ifadesini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-104">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="ef0b7-105">Aşağıdaki örnekte gösterildiği gibi bir nesne ifadesi veya [Nothing](../../../language-reference/nothing.md) anahtar sözcüğü atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-105">You can assign an object expression or the [Nothing](../../../language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="ef0b7-106">`Nothing` Şu anda değişkene atanmış bir nesne olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-106">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="ef0b7-107">Başlatma</span><span class="sxs-lookup"><span data-stu-id="ef0b7-107">Initialization</span></span>

<span data-ttu-id="ef0b7-108">Kodunuz çalışmaya başladığında, nesne değişkenleriniz olarak başlatılır `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="ef0b7-108">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="ef0b7-109">Bildirimleri başlatma dahil olanlar, bildirim deyimleri yürütüldüğünde belirttiğiniz değerlere yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-109">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="ef0b7-110">[Yeni](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü kullanarak bildirimindeki başlatmayı dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-110">You can include initialization in your declaration by using the [New](../../../language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="ef0b7-111">Aşağıdaki bildirim deyimleri, nesne değişkenlerini bildirir `testUri` ve `ver` bunlara belirli nesneler atar.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-111">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="ef0b7-112">Her biri, nesneyi başlatmak için uygun sınıfın aşırı yüklenmiş oluşturucularından birini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-112">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="ef0b7-113">Disassociation tamamlayamadı</span><span class="sxs-lookup"><span data-stu-id="ef0b7-113">Disassociation</span></span>

<span data-ttu-id="ef0b7-114">Bir nesne değişkenini `Nothing` , değişkenin ilişkilendirmesini belirli bir nesneyle devam ettirir şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-114">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="ef0b7-115">Bu, değişkeni değiştirerek nesneyi yanlışlıkla değiştirmenizi önler.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-115">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="ef0b7-116">Ayrıca, aşağıdaki örnekte gösterildiği gibi, nesne değişkeninin geçerli bir nesneye işaret edilip edilmeyeceğini test etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-116">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="ef0b7-117">Değişkeninizin başvurduğu nesne başka bir uygulamada ise, bu test uygulamanın sonlandırılıp sonlandırılmadığını veya yalnızca geçersiz kılınmadığını belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-117">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="ef0b7-118">Değerine sahip bir nesne değişkeni `Nothing` de *null başvuru* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-118">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="ef0b7-119">Geçerli örnek</span><span class="sxs-lookup"><span data-stu-id="ef0b7-119">Current Instance</span></span>

<span data-ttu-id="ef0b7-120">Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-120">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="ef0b7-121">Tüm kod bir yordam içinde yürütüldüğü için, geçerli örnek yordamın çağrıldığı bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-121">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="ef0b7-122">`Me`Anahtar sözcüğü, geçerli örneğe başvuran bir nesne değişkeni işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-122">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="ef0b7-123">Bir yordam [paylaşılmışsa](../../../language-reference/modifiers/shared.md), `Me` geçerli örneğe bir işaretçi almak için anahtar sözcüğünü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-123">If a procedure is not [Shared](../../../language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="ef0b7-124">Paylaşılan yordamlar bir sınıfın belirli bir örneğiyle ilişkilendirilemez.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-124">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="ef0b7-125">Kullanmak, `Me` özellikle geçerli örneği başka bir modüldeki yordama geçirmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-125">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="ef0b7-126">Örneğin, bir dizi XML belgeniz olduğunu ve bunlara bazı standart metinler ekleneceğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-126">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="ef0b7-127">Aşağıdaki örnek bunu yapmak için bir yordam tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-127">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="ef0b7-128">Her XML belge nesnesi, yordamı çağırabilir ve geçerli örneğini bir bağımsız değişken olarak geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-128">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="ef0b7-129">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-129">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="ef0b7-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef0b7-130">See also</span></span>

- [<span data-ttu-id="ef0b7-131">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ef0b7-131">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="ef0b7-132">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="ef0b7-132">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="ef0b7-133">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="ef0b7-133">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="ef0b7-134">Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama</span><span class="sxs-lookup"><span data-stu-id="ef0b7-134">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="ef0b7-135">Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama</span><span class="sxs-lookup"><span data-stu-id="ef0b7-135">How to: Make an Object Variable Not Refer to Any Instance</span></span>](how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="ef0b7-136">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="ef0b7-136">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)

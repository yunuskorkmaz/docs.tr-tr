---
title: Nesne Değişkeni Ataması (Visual Basic)
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
ms.openlocfilehash: dff1b9bb9e87f827663786cac3f33531db41b2c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840282"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="98e03-102">Nesne Değişkeni Ataması (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98e03-102">Object Variable Assignment (Visual Basic)</span></span>
<span data-ttu-id="98e03-103">Bir nesne bir nesne değişkenine atamak için bir normal atama ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="98e03-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="98e03-104">Bir nesne ifadesi atayabilirsiniz veya [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) anahtar sözcüğü, aşağıdaki örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="98e03-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 <span data-ttu-id="98e03-105">`Nothing` şu anda değişkenine atanan nesnesi yok anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="98e03-105">`Nothing` means there is no object currently assigned to the variable.</span></span>  
  
## <a name="initialization"></a><span data-ttu-id="98e03-106">Başlatma</span><span class="sxs-lookup"><span data-stu-id="98e03-106">Initialization</span></span>  
 <span data-ttu-id="98e03-107">Kodunuzu çalıştırmak, nesnenizin değişkenleri başlatıldığı başladığı `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="98e03-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="98e03-108">Bu başlatma, bildirimleri içeren bildirim deyimleri yürütüldüğünde, belirttiğiniz değerleri yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="98e03-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>  
  
 <span data-ttu-id="98e03-109">Başlatma kullanarak, bildiriminde dahil edebilirsiniz [yeni](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="98e03-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="98e03-110">Aşağıdaki bildirim deyimleri nesne değişkenlerini bildirme `testUri` ve `ver` ve belirli nesneleri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98e03-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="98e03-111">Her bir uygun sınıf aşırı yüklü oluşturucular nesneyi başlatmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="98e03-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>  
  
```  
Dim testUri As New System.Uri("https://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a><span data-ttu-id="98e03-112">İlişkisi kaldırma</span><span class="sxs-lookup"><span data-stu-id="98e03-112">Disassociation</span></span>  
 <span data-ttu-id="98e03-113">Bir nesne değişkeninin ayarını `Nothing` herhangi belirli bir nesne değişkeninin ilişkilendirmesini sona erdirir.</span><span class="sxs-lookup"><span data-stu-id="98e03-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="98e03-114">Bu, yanlışlıkla nesne değişkeni değiştirerek değiştirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="98e03-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="98e03-115">Ayrıca, nesne değişkenini aşağıdaki örnekte gösterildiği gibi geçerli bir nesneye işaret olup olmadığını sınamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="98e03-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 <span data-ttu-id="98e03-116">Değişkenin başvurduğu nesneyi başka bir uygulamada ise, bu test, uygulamanın sahip sonlandırıldı veya yalnızca nesne geçersiz kılınan belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="98e03-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>  
  
 <span data-ttu-id="98e03-117">Bir nesne değişkeninin değerini `Nothing` olarak da adlandırılan bir *null başvuru*.</span><span class="sxs-lookup"><span data-stu-id="98e03-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>  
  
## <a name="current-instance"></a><span data-ttu-id="98e03-118">Geçerli örnek</span><span class="sxs-lookup"><span data-stu-id="98e03-118">Current Instance</span></span>  
 <span data-ttu-id="98e03-119">*Geçerli örneğin* nesnenin hangi kod şu anda Yürütülüyor sertifikadır.</span><span class="sxs-lookup"><span data-stu-id="98e03-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="98e03-120">Tüm kod yürüten bir yordam içinde olduğundan, geçerli Örneğin, yordamı çağrıldı olur.</span><span class="sxs-lookup"><span data-stu-id="98e03-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>  
  
 <span data-ttu-id="98e03-121">`Me` Anahtar sözcüğü bir nesne değişkeninin geçerli örneğine başvurma olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="98e03-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="98e03-122">Bir yordam değilse [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), bunu `Me` geçerli örneğine bir işaretçi alma için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="98e03-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="98e03-123">Paylaşılan yordamlar, bir sınıfın belirli bir örneği ile ilişkilendirilemez.</span><span class="sxs-lookup"><span data-stu-id="98e03-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>  
  
 <span data-ttu-id="98e03-124">Kullanarak `Me` geçerli örneğin başka bir modül bir yordamda geçirmek özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="98e03-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="98e03-125">Örneğin, XML belgelerinin sahiptir ve bunların tümüne bazı standart metin eklemek istediğiniz varsayalım.</span><span class="sxs-lookup"><span data-stu-id="98e03-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="98e03-126">Aşağıdaki örnek bunu yapma yordamı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="98e03-126">The following example defines a procedure to do this.</span></span>  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 <span data-ttu-id="98e03-127">Her XML belge nesnesi, bir yordamı çağırma ve kendi geçerli örneğini bağımsız değişken geçirin.</span><span class="sxs-lookup"><span data-stu-id="98e03-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="98e03-128">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="98e03-128">The following example demonstrates this.</span></span>  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a><span data-ttu-id="98e03-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98e03-129">See also</span></span>

- [<span data-ttu-id="98e03-130">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="98e03-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="98e03-131">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="98e03-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="98e03-132">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="98e03-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="98e03-133">Nasıl yapılır: Bir nesne değişkeni bildirme ve Visual Basic'te bir nesne atama</span><span class="sxs-lookup"><span data-stu-id="98e03-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="98e03-134">Nasıl yapılır: Bir nesnenin değişken sağlamak için herhangi bir örneğine Başvurmamasını</span><span class="sxs-lookup"><span data-stu-id="98e03-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="98e03-135">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="98e03-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

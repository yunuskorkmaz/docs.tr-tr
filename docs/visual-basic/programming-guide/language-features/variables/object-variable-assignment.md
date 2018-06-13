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
ms.openlocfilehash: f20a03c4d9a0e33203629ae066686f4c9f25c105
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656064"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="bf1ad-102">Nesne Değişkeni Ataması (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf1ad-102">Object Variable Assignment (Visual Basic)</span></span>
<span data-ttu-id="bf1ad-103">Bir nesne bir nesne değişkenine atamak için normal atama deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="bf1ad-104">Bir nesne ifadesi atayabilir veya [hiçbir şey](../../../../visual-basic/language-reference/nothing.md) anahtar sözcüğü, aşağıdaki örnek olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 <span data-ttu-id="bf1ad-105">`Nothing` şu anda değişkenine atanan nesnesi yok anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-105">`Nothing` means there is no object currently assigned to the variable.</span></span>  
  
## <a name="initialization"></a><span data-ttu-id="bf1ad-106">Başlatma</span><span class="sxs-lookup"><span data-stu-id="bf1ad-106">Initialization</span></span>  
 <span data-ttu-id="bf1ad-107">Kodunuzu başladığı çalıştıran, değişkenleri için başlatılır nesnenizin `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="bf1ad-108">Bu, bildirimleri başlatma dahil bildirim deyimleri çalıştırıldığında belirttiğiniz değerleri yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>  
  
 <span data-ttu-id="bf1ad-109">Başlatma kullanarak, bildiriminde dahil edebilirsiniz [yeni](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="bf1ad-110">Aşağıdaki bildirim deyimleri nesne değişkenlerini bildirme `testUri` ve `ver` ve belirli nesneleri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="bf1ad-111">Her uygun sınıfının aşırı yüklenmiş oluşturuculardan birine nesneyi başlatmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a><span data-ttu-id="bf1ad-112">Disassociation</span><span class="sxs-lookup"><span data-stu-id="bf1ad-112">Disassociation</span></span>  
 <span data-ttu-id="bf1ad-113">Bir nesne değişkeni ayarını `Nothing` herhangi belirli bir nesne değişkeni ilişkilendirmesini sona erdirir.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="bf1ad-114">Bu, yanlışlıkla nesne değişkeni değiştirerek değiştirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="bf1ad-115">Ayrıca, nesne değişkeni aşağıdaki örnekte gösterildiği gibi geçerli bir nesneye işaret olup olmadığını sınamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 <span data-ttu-id="bf1ad-116">Değişkeniniz başvurduğu nesne başka bir uygulamada ise, bu test, uygulamanın veya sonlandırıldı yalnızca nesne geçersiz kılınan belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>  
  
 <span data-ttu-id="bf1ad-117">Bir nesne değişkeninin değerini `Nothing` olarak da adlandırılan bir *null başvuru*.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>  
  
## <a name="current-instance"></a><span data-ttu-id="bf1ad-118">Geçerli örnek</span><span class="sxs-lookup"><span data-stu-id="bf1ad-118">Current Instance</span></span>  
 <span data-ttu-id="bf1ad-119">*Geçerli örnek* hangi kod şu anda yürütülmekte olan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="bf1ad-120">Yordam içinde tüm kodu yürütür olduğundan, geçerli, yordamın çağrıldığı bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>  
  
 <span data-ttu-id="bf1ad-121">`Me` Anahtar sözcük, geçerli örneğine başvurma bir nesne değişkeni görür.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="bf1ad-122">Bir yordam değilse [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), kullanabileceği `Me` geçerli örneğini gösteren bir işaretçi almak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="bf1ad-123">Paylaşılan yordamları belirli bir sınıf örneği ile ilişkilendirilemez.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>  
  
 <span data-ttu-id="bf1ad-124">Kullanarak `Me` geçerli örneğini başka bir modül yordamda geçirilmesi özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="bf1ad-125">Örneğin, XML belgelerinin sahiptir ve bunların tümüne bazı standart metin eklemek istediğiniz varsayalım.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="bf1ad-126">Aşağıdaki örnek, bunu yapmak için bir yordam tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-126">The following example defines a procedure to do this.</span></span>  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 <span data-ttu-id="bf1ad-127">Her XML belge nesnesi, yordam çağrısı ve geçerli örnek bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="bf1ad-128">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-128">The following example demonstrates this.</span></span>  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf1ad-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf1ad-129">See Also</span></span>  
 [<span data-ttu-id="bf1ad-130">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bf1ad-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="bf1ad-131">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="bf1ad-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="bf1ad-132">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="bf1ad-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="bf1ad-133">Nasıl yapılır: bir nesne değişkeni bildirme ve Visual Basic'te bir nesneyi atayın</span><span class="sxs-lookup"><span data-stu-id="bf1ad-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [<span data-ttu-id="bf1ad-134">Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama</span><span class="sxs-lookup"><span data-stu-id="bf1ad-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [<span data-ttu-id="bf1ad-135">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="bf1ad-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

---
title: 'Nasıl yapılır: Erişim üyeleri bir nesnenin (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: de00e428cc3d9d7a5688e853b0ff4295fec5b3e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052137"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="bda02-102">Nasıl yapılır: Erişim üyeleri bir nesnenin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bda02-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="bda02-103">Bir nesneye başvuruda bulunan bir nesne değişkeni varsa, genellikle o nesnenin yöntemler, özellikler, alanlar ve olaylar gibi üyeleri birlikte çalışmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="bda02-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="bda02-104">Örneğin, bir kez oluşturduğunuz yeni bir <xref:System.Windows.Forms.Form> nesne ayarlamak isteyebilirsiniz, <xref:System.Windows.Forms.Control.Text%2A> özelliği veya çağrı kendi <xref:System.Windows.Forms.Control.Focus%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bda02-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="bda02-105">Üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="bda02-105">Accessing Members</span></span>  
 <span data-ttu-id="bda02-106">Bir nesnenin üyeleri, ona başvuran değişkeni aracılığıyla erişin.</span><span class="sxs-lookup"><span data-stu-id="bda02-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="bda02-107">Bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="bda02-107">To access members of an object</span></span>  
  
- <span data-ttu-id="bda02-108">Üye erişimi işlecini kullanın (`.`) üye adı arasındaki nesne değişkeni adı.</span><span class="sxs-lookup"><span data-stu-id="bda02-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="bda02-109">Üye [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), ona erişmek için bir değişken gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bda02-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="bda02-110">Bilinen türünde bir nesnenin üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="bda02-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="bda02-111">Derleme zamanında bir nesne türünü biliyorsanız, kullanabileceğiniz *erken bağlama* kendisine başvuran bir değişken için.</span><span class="sxs-lookup"><span data-stu-id="bda02-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="bda02-112">Derleme zamanında tür öğrenmek bildiğiniz bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="bda02-112">To access members of an object for which you know the type at compile time</span></span>  
  
1. <span data-ttu-id="bda02-113">Değişkenine atamak istediğiniz nesne türünü olmaya nesne değişkeni bildirme.</span><span class="sxs-lookup"><span data-stu-id="bda02-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="bda02-114">İle `Option Strict On`, yalnızca atayabilirsiniz <xref:System.Windows.Forms.Form> nesneleri (veya bir türden nesneleri türetilen <xref:System.Windows.Forms.Form>) için `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="bda02-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="bda02-115">Bir sınıf veya yapı bir genişletme ile tanımlanan, `CType` dönüştürme <xref:System.Windows.Forms.Form>, ayrıca bu sınıf atayın veya için yapı `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="bda02-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2. <span data-ttu-id="bda02-116">Üye erişimi işlecini kullanın (`.`) üye adı arasındaki nesne değişkeni adı.</span><span class="sxs-lookup"><span data-stu-id="bda02-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="bda02-117">Tüm yöntemler ve özellikler için belirli erişebileceğiniz <xref:System.Windows.Forms.Form> ne olursa olsun, sınıf `Option Strict` ayardır.</span><span class="sxs-lookup"><span data-stu-id="bda02-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="bda02-118">Bilinmeyen türdeki bir nesnenin üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="bda02-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="bda02-119">Derleme zamanında bir nesnenin türünü bilmiyorsanız kullanmalısınız *geç bağlama* kendisine başvuran herhangi bir değişken için.</span><span class="sxs-lookup"><span data-stu-id="bda02-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="bda02-120">Kendisi için türü derleme zamanında bilmediğiniz bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="bda02-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1. <span data-ttu-id="bda02-121">Olmaya nesne değişkeni bildirme [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="bda02-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="bda02-122">(Bir değişken olarak bildirme `Object` olarak bildirme aynı <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="bda02-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="bda02-123">İle `Option Strict On`, üzerinde tanımlanan üyeler erişebileceğiniz <xref:System.Object> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bda02-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2. <span data-ttu-id="bda02-124">Üye erişimi işlecini kullanın (`.`) üye adı arasındaki nesne değişkeni adı.</span><span class="sxs-lookup"><span data-stu-id="bda02-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="bda02-125">Nesne değişkenine atayın herhangi bir nesnenin üyeleri erişebilmesi için ayarlamalısınız `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="bda02-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="bda02-126">Bunu yaptığınızda, derleyici belirli bir üye değişkenine atayın nesnesi tarafından kullanıma sunulduğunu garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="bda02-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="bda02-127">Nesne girişiminde erişmek için üye sunmuyorsa bir <xref:System.MemberAccessException> özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="bda02-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda02-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bda02-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="bda02-129">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bda02-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="bda02-130">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="bda02-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="bda02-131">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="bda02-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="bda02-132">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="bda02-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

---
title: "Nasıl yapılır: Bir Nesnenin Üyelerine Erişme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 85fa4932b449bf7b9ecb3902fc17fd954ea8cfac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="cbb1d-102">Nasıl yapılır: Bir Nesnenin Üyelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbb1d-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="cbb1d-103">Bir nesneye başvuruda bulunan bir nesne değişkeni varsa, genellikle yöntemler, özellikler, alanları ve olaylar gibi söz konusu nesne üyeleri çalışmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="cbb1d-104">Örneğin, bir kez oluşturduğunuz yeni bir <xref:System.Windows.Forms.Form> nesne ayarlamak isteyebilirsiniz, <xref:System.Windows.Forms.Control.Text%2A> özelliği veya çağrı kendi <xref:System.Windows.Forms.Control.Focus%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="cbb1d-105">Üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="cbb1d-105">Accessing Members</span></span>  
 <span data-ttu-id="cbb1d-106">Kendisine başvuran değişkeni aracılığıyla bir nesnenin üyeleri erişin.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="cbb1d-107">Bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="cbb1d-107">To access members of an object</span></span>  
  
-   <span data-ttu-id="cbb1d-108">Üye erişimi işleci kullanın (`.`) arasında nesne değişken adını ve üye adı.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="cbb1d-109">Üye ise [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), erişmek için bir değişken gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="cbb1d-110">Bilinen türünde bir nesnenin üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="cbb1d-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="cbb1d-111">Derleme zamanında bir nesne türünü biliyorsanız, kullanabileceğiniz *erken bağlama* kendisine başvuran bir değişken için.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="cbb1d-112">Derleme zamanında türü öğrenmek bildiğiniz bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="cbb1d-112">To access members of an object for which you know the type at compile time</span></span>  
  
1.  <span data-ttu-id="cbb1d-113">Değişkenine atamak istediğiniz nesne türünü olmaya nesne değişkeni bildirme.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="cbb1d-114">İle `Option Strict On`, yalnızca atayabilirsiniz <xref:System.Windows.Forms.Form> nesneler (veya bir türdeki nesneleri türetilen <xref:System.Windows.Forms.Form>) için `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="cbb1d-115">Bir sınıf veya yapı bir genişletme ile tanımlanan, `CType` dönüştürme <xref:System.Windows.Forms.Form>, ayrıca bu sınıf atayın veya için yapı `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2.  <span data-ttu-id="cbb1d-116">Üye erişimi işleci kullanın (`.`) arasında nesne değişken adını ve üye adı.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="cbb1d-117">Tüm özgü özellikleri ve yöntemleri erişebilirsiniz <xref:System.Windows.Forms.Form> ne olursa olsun sınıfı `Option Strict` ayardır.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="cbb1d-118">Bilinmeyen türdeki bir nesnenin üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="cbb1d-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="cbb1d-119">Derleme zamanında bir nesnenin türünü bilmiyorsanız, kullanmalısınız *geç bağlama* kendisine başvuran herhangi bir değişken için.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="cbb1d-120">Kendisi için türü derleme zamanında Tanımadığınız bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="cbb1d-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1.  <span data-ttu-id="cbb1d-121">Olmaya nesne değişkeni bildirme [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="cbb1d-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="cbb1d-122">(Bir değişken olarak bildirme `Object` olarak bildirme aynı <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="cbb1d-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="cbb1d-123">İle `Option Strict On`, üzerinde tanımlanan üyeleri erişebilir <xref:System.Object> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2.  <span data-ttu-id="cbb1d-124">Üye erişimi işleci kullanın (`.`) arasında nesne değişken adını ve üye adı.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="cbb1d-125">Nesne değişkeni atadığınız herhangi bir nesnenin üyelerine erişebilmeleri için ayarlamalısınız `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="cbb1d-126">Bunu yaptığınızda derleyici belirli bir üye değişkenine atayın nesnesi tarafından sunulan garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="cbb1d-127">Nesne erişim çalıştığınızda üye imkanı sunmuyorsa bir <xref:System.MemberAccessException> özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb1d-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbb1d-128">See Also</span></span>  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [<span data-ttu-id="cbb1d-129">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cbb1d-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="cbb1d-130">Nesne değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="cbb1d-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="cbb1d-131">Nesne veri türü</span><span class="sxs-lookup"><span data-stu-id="cbb1d-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="cbb1d-132">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="cbb1d-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

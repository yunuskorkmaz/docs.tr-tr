---
title: 'Nasıl yapılır: Bir Nesnenin Üyelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: d44b538e8413eb1412e937375e9bca77600a29b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348662"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="6c9c9-102">Nasıl yapılır: Bir Nesnenin Üyelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c9c9-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="6c9c9-103">Bir nesneye başvuran bir nesne değişkeniniz varsa, genellikle bu nesnenin, yöntemleri, özellikleri, alanları ve olayları gibi üyeleriyle çalışmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="6c9c9-104">Örneğin, yeni bir <xref:System.Windows.Forms.Form> nesnesi oluşturduktan sonra, <xref:System.Windows.Forms.Control.Text%2A> özelliğini ayarlamak veya <xref:System.Windows.Forms.Control.Focus%2A> metodunu çağırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="6c9c9-105">Üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="6c9c9-105">Accessing Members</span></span>

<span data-ttu-id="6c9c9-106">Bir nesnenin üyelerine, ona başvuran değişken aracılığıyla erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="6c9c9-107">Bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="6c9c9-107">To access members of an object</span></span>

- <span data-ttu-id="6c9c9-108">Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini (`.`) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="6c9c9-109">Üye [paylaşılmışsa](../../../../visual-basic/language-reference/modifiers/shared.md), ona erişmek için bir değişkene ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="6c9c9-110">Bilinen türdeki bir nesnenin üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="6c9c9-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="6c9c9-111">Derleme zamanında bir nesnenin türünü biliyorsanız, ona başvuran bir değişken için *erken bağlamayı* kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="6c9c9-112">Derleme zamanında türünü bildiğiniz bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="6c9c9-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="6c9c9-113">Değişkene atamak istediğiniz nesnenin türünün nesne değişkenini bildirin.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="6c9c9-114">`Option Strict On`, yalnızca <xref:System.Windows.Forms.Form> nesneleri (veya <xref:System.Windows.Forms.Form>türetilen bir türdeki nesneleri `extraForm`' a atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="6c9c9-115"><xref:System.Windows.Forms.Form>için genişleyen `CType` dönüştürmeye sahip bir sınıf veya yapı tanımladıysanız, bu sınıfı veya yapıyı da `extraForm`atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="6c9c9-116">Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini (`.`) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="6c9c9-117">`Option Strict` ayarının ne olduğuna bakılmaksızın <xref:System.Windows.Forms.Form> sınıfına özgü tüm yöntemlere ve özelliklere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="6c9c9-118">Bilinmeyen türdeki bir nesnenin üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="6c9c9-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="6c9c9-119">Derleme zamanında bir nesnenin türünü bilmiyor değilseniz, ona başvuran herhangi bir değişken için *geç bağlamayı* kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="6c9c9-120">Derleme zamanında türünü tanımadığınız bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="6c9c9-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="6c9c9-121">Nesne [veri türünde](../../../../visual-basic/language-reference/data-types/object-data-type.md)olacak nesne değişkenini bildirin.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="6c9c9-122">(Bir değişkeni `Object` olarak bildirmek, <xref:System.Object?displayProperty=nameWithType>olarak bildirme ile aynıdır.)</span><span class="sxs-lookup"><span data-stu-id="6c9c9-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="6c9c9-123">`Option Strict On`, yalnızca <xref:System.Object> sınıfında tanımlanmış üyelere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="6c9c9-124">Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini (`.`) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="6c9c9-125">Nesne değişkenine atadığınız herhangi bir nesnenin üyelerine erişebilmek için `Option Strict Off`ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="6c9c9-126">Bunu yaptığınızda derleyici, belirli bir üyenin değişkene atadığınız nesne tarafından açığa çıkarılabileceği garantisi vermez.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="6c9c9-127">Nesne, erişmeye çalıştığınız bir üyeyi kullanıma sunmadığından, bir <xref:System.MemberAccessException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c9c9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c9c9-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="6c9c9-129">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="6c9c9-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="6c9c9-130">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="6c9c9-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="6c9c9-131">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="6c9c9-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="6c9c9-132">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="6c9c9-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

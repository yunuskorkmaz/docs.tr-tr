---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir nesnenin üyelerine erişme (Visual Basic)'
title: 'Nasıl yapılır: Bir Nesnenin Üyelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: b4aed213bbe520b7b7027acc146d0973f7273fd1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435531"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="a0add-103">Nasıl yapılır: Bir Nesnenin Üyelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0add-103">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="a0add-104">Bir nesneye başvuran bir nesne değişkeniniz varsa, genellikle bu nesnenin, yöntemleri, özellikleri, alanları ve olayları gibi üyeleriyle çalışmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="a0add-104">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="a0add-105">Örneğin, yeni bir nesne oluşturduktan sonra <xref:System.Windows.Forms.Form> , <xref:System.Windows.Forms.Control.Text%2A> özelliğini ayarlamak veya metodunu çağırmak isteyebilirsiniz <xref:System.Windows.Forms.Control.Focus%2A> .</span><span class="sxs-lookup"><span data-stu-id="a0add-105">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="a0add-106">Üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="a0add-106">Accessing Members</span></span>

<span data-ttu-id="a0add-107">Bir nesnenin üyelerine, ona başvuran değişken aracılığıyla erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0add-107">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="a0add-108">Bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="a0add-108">To access members of an object</span></span>

- <span data-ttu-id="a0add-109">`.`Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini () kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0add-109">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="a0add-110">Üye [paylaşılmışsa](../../../language-reference/modifiers/shared.md), ona erişmek için bir değişkene ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="a0add-110">If the member is [Shared](../../../language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="a0add-111">Bilinen türdeki bir nesnenin üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="a0add-111">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="a0add-112">Derleme zamanında bir nesnenin türünü biliyorsanız, ona başvuran bir değişken için *erken bağlamayı* kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0add-112">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="a0add-113">Derleme zamanında türünü bildiğiniz bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="a0add-113">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="a0add-114">Değişkene atamak istediğiniz nesnenin türünün nesne değişkenini bildirin.</span><span class="sxs-lookup"><span data-stu-id="a0add-114">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="a0add-115">İle `Option Strict On` , yalnızca <xref:System.Windows.Forms.Form> nesneleri (veya öğesinden türetilmiş bir türün nesnelerini <xref:System.Windows.Forms.Form> ) atayabilirsiniz `extraForm` .</span><span class="sxs-lookup"><span data-stu-id="a0add-115">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="a0add-116">Üzerinde genişleyen dönüştürmeye sahip bir sınıf veya yapı tanımladıysanız `CType` <xref:System.Windows.Forms.Form> , bu sınıfa veya yapıya de atayabilirsiniz `extraForm` .</span><span class="sxs-lookup"><span data-stu-id="a0add-116">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="a0add-117">`.`Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini () kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0add-117">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="a0add-118">Ayarın ne olduğuna bakılmaksızın sınıfa özgü tüm yöntemlere ve özelliklere erişebilirsiniz <xref:System.Windows.Forms.Form> `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="a0add-118">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="a0add-119">Bilinmeyen türdeki bir nesnenin üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="a0add-119">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="a0add-120">Derleme zamanında bir nesnenin türünü bilmiyor değilseniz, ona başvuran herhangi bir değişken için *geç bağlamayı* kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0add-120">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="a0add-121">Derleme zamanında türünü tanımadığınız bir nesnenin üyelerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="a0add-121">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="a0add-122">Nesne [veri türünde](../../../language-reference/data-types/object-data-type.md)olacak nesne değişkenini bildirin.</span><span class="sxs-lookup"><span data-stu-id="a0add-122">Declare the object variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="a0add-123">(Bir değişkeni olarak bildirmek ile aynı şekilde bildirme `Object` <xref:System.Object?displayProperty=nameWithType> .)</span><span class="sxs-lookup"><span data-stu-id="a0add-123">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="a0add-124">İle `Option Strict On` , yalnızca sınıfında tanımlanmış üyelere erişebilirsiniz <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="a0add-124">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="a0add-125">`.`Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini () kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0add-125">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="a0add-126">Nesne değişkenine atadığınız herhangi bir nesnenin üyelerine erişebilmek için, öğesini ayarlamanız gerekir `Option Strict Off` .</span><span class="sxs-lookup"><span data-stu-id="a0add-126">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="a0add-127">Bunu yaptığınızda derleyici, belirli bir üyenin değişkene atadığınız nesne tarafından açığa çıkarılabileceği garantisi vermez.</span><span class="sxs-lookup"><span data-stu-id="a0add-127">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="a0add-128">Nesne, erişmeye çalıştığınız bir üyeyi kullanıma sunmadığından, bir <xref:System.MemberAccessException> özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="a0add-128">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0add-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0add-129">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="a0add-130">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="a0add-130">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="a0add-131">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="a0add-131">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="a0add-132">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a0add-132">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="a0add-133">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0add-133">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)

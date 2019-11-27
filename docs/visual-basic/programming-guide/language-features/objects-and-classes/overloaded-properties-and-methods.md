---
title: Aşırı yüklenmiş Özellikler ve Yöntemler
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346096"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="b6d5e-102">Aşırı yüklenmiş Özellikler ve Yöntemler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6d5e-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="b6d5e-103">Aşırı yükleme, aynı ada ancak farklı bağımsız değişken türlerine sahip bir sınıfta birden fazla yordamın, örnek oluşturucunun veya özelliğin oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="b6d5e-104">Kullanımı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="b6d5e-104">Overloading usage</span></span>

<span data-ttu-id="b6d5e-105">Aşırı yükleme özellikle, nesne modeliniz farklı veri türlerinde çalışan yordamlar için özdeş adlar kullanmayı belirlemesi durumunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="b6d5e-106">Örneğin, çeşitli farklı veri türlerini görüntüleyebilen bir sınıf şuna benzer `Display` yordamlarına sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="b6d5e-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="b6d5e-107">Aşırı yükleme olmadan, her bir yordam için, daha sonra gösterildiği gibi, aynı şeyi gerçekleştirseler bile ayrı adlar oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b6d5e-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="b6d5e-108">Aşırı yükleme özelliği, kullanılabilecek bir veri türleri seçimi sağladığından özellikleri veya yöntemleri kullanmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="b6d5e-109">Örneğin, daha önce açıklanan aşırı yüklenmiş `Display` yöntemi aşağıdaki kod satırlarıyla çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="b6d5e-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="b6d5e-110">Çalışma zamanında, Visual Basic belirttiğiniz parametrelerin veri türlerine göre doğru yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="b6d5e-111">Kuralları aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="b6d5e-111">Overloading rules</span></span>

 <span data-ttu-id="b6d5e-112">Aynı ada sahip iki veya daha fazla özellik ya da yöntem ekleyerek bir sınıf için aşırı yüklenmiş bir üye oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="b6d5e-113">Aşırı yüklenmiş türetilmiş Üyeler hariç olmak üzere, her aşırı yüklenmiş üye farklı parametre listelerine sahip olmalıdır ve bir özellik veya yordamı aşırı yüklerken bir ayrım özelliği olarak aşağıdaki öğeler kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="b6d5e-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="b6d5e-114">Bir üyeye veya üyenin parametrelerine uygulanan `ByVal` veya `ByRef`gibi değiştiriciler.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="b6d5e-115">Parametrelerin adları</span><span class="sxs-lookup"><span data-stu-id="b6d5e-115">Names of parameters</span></span>

- <span data-ttu-id="b6d5e-116">Yordamların dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="b6d5e-116">Return types of procedures</span></span>

<span data-ttu-id="b6d5e-117">Aşırı yükleme sırasında `Overloads` anahtar sözcüğü isteğe bağlıdır, ancak herhangi bir aşırı yüklenmiş üye `Overloads` anahtar sözcüğünü kullanıyorsa, aynı ada sahip diğer tüm aşırı yüklenmiş Üyeler de bu anahtar sözcüğü belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="b6d5e-118">Türetilmiş sınıflar, *ad ve imza ile gölgeleme*olarak bilinen bir işlem olan aynı parametrelere ve parametre türlerine sahip üyelere sahip devralınan üyeleri aşırı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="b6d5e-119">Ad ve imza ile gölgeleme sırasında `Overloads` anahtar sözcüğü kullanılırsa, türetilmiş sınıfın üyenin uygulanması temel sınıftaki uygulama yerine kullanılır ve bu üyenin diğer tüm aşırı yüklemeleri türetilmiş sınıfın örnekleri tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="b6d5e-120">Aynı parametrelere ve parametre türlerine sahip bir üyeyle devralınan bir üyenin aşırı yüklemesi sırasında `Overloads` anahtar sözcüğü atlanırsa aşırı yükleme, *ada göre gölgeleme*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="b6d5e-121">Ada göre gölgeleme bir üyenin devralınmış uygulamasını değiştirir ve diğer tüm aşırı yüklemeleri türetilmiş sınıfın örneklerine ve onun decedents kullanılamaz hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="b6d5e-122">`Overloads` ve `Shadows` değiştiricileri her ikisi de aynı özellik veya yöntemle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="b6d5e-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6d5e-123">Example</span></span>

<span data-ttu-id="b6d5e-124">Aşağıdaki örnek, bir dolar tutarının `String` veya `Decimal` gösterimini kabul eden aşırı yüklenmiş yöntemler oluşturur ve satış vergisini içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="b6d5e-125">Daha fazla yüklenmiş bir yöntem oluşturmak için bu örneği kullanın</span><span class="sxs-lookup"><span data-stu-id="b6d5e-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="b6d5e-126">Yeni bir proje açın ve `TaxClass`adlı bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="b6d5e-127">Aşağıdaki kodu `TaxClass` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="b6d5e-128">Formunuza aşağıdaki yordamı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="b6d5e-129">Formunuza bir düğme ekleyin ve düğmenin `Button1_Click` olayından `ShowTax` yordamını çağırın.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="b6d5e-130">Projeyi çalıştırın ve aşırı yüklenmiş `ShowTax` yordamını sınamak için formdaki düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="b6d5e-131">Çalışma zamanında, derleyici kullanılan parametrelerle eşleşen uygun aşırı yüklenmiş işlevi seçer.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="b6d5e-132">Düğmeye tıkladığınızda, önce aşırı yüklenmiş yöntemi bir dize ve ileti olan bir `Price` parametresiyle ilk olarak çağrılır, "Price bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="b6d5e-133">Vergi $5,12 "görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="b6d5e-134">`TaxAmount` ikinci kez bir `Decimal` değeriyle çağrılır, "Price bir Decimal olur.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="b6d5e-135">Vergi $5,12 "görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6d5e-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6d5e-136">See also</span></span>

- [<span data-ttu-id="b6d5e-137">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b6d5e-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="b6d5e-138">Visual Basic gölgeleme</span><span class="sxs-lookup"><span data-stu-id="b6d5e-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="b6d5e-139">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="b6d5e-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="b6d5e-140">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="b6d5e-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="b6d5e-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="b6d5e-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="b6d5e-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="b6d5e-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)
- [<span data-ttu-id="b6d5e-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="b6d5e-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)
- [<span data-ttu-id="b6d5e-144">Overloads</span><span class="sxs-lookup"><span data-stu-id="b6d5e-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="b6d5e-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="b6d5e-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)

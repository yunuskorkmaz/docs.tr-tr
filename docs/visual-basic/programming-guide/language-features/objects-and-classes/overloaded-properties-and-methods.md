---
title: Aşırı yüklenmiş özellikler ve yöntemler (Visual Basic)
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
ms.openlocfilehash: 8d7341370d9770d2e57f786ac7c68277e66a9bbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864877"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="6e744-102">Aşırı yüklenmiş özellikler ve yöntemler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e744-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="6e744-103">Aşırı yükleme birden fazla yordam, örnek oluşturucusu veya bir sınıf ile aynı ada ancak farklı bağımsız değişken türleri özelliğinde oluşturulmasını var.</span><span class="sxs-lookup"><span data-stu-id="6e744-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="6e744-104">Kullanım aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="6e744-104">Overloading usage</span></span>

<span data-ttu-id="6e744-105">Aynı adları için farklı veri türleri üzerinde çalışması yordamları kullanmak istemiyorsunuz, nesne modeli belirler. aşırı yükleme özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="6e744-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="6e744-106">Örneğin, birçok farklı veri türlerini görüntülemek için bir sınıf olabilir `Display` şuna yordamları:</span><span class="sxs-lookup"><span data-stu-id="6e744-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="6e744-107">Bunlar aşağıda gösterildiği aynı şeyi yapmak olsa da aşırı yüklemeden, her bir yordam için farklı adlar oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6e744-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="6e744-108">Aşırı yükleme özelliklerinin veya yöntemlerin bir seçenek kullanılabilir veri türleri sağladığından kullanmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6e744-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="6e744-109">Örneğin, aşırı yüklenmiş `Display` yöntemi daha önce çağrılabilir herhangi aşağıdaki kod satırlarını:</span><span class="sxs-lookup"><span data-stu-id="6e744-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="6e744-110">Çalışma zamanında, Visual Basic belirttiğiniz parametrelerin veri türlerine göre doğru yordamını çağırır.</span><span class="sxs-lookup"><span data-stu-id="6e744-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="6e744-111">Kuralları aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="6e744-111">Overloading rules</span></span>

 <span data-ttu-id="6e744-112">Bir sınıf için aşırı yüklenmiş bir üye, iki veya daha fazla özelliklerinin veya yöntemlerin aynı ada sahip ekleyerek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6e744-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="6e744-113">Türetilmiş aşırı yüklenmiş üyelerin dışında aşırı yüklenmiş üyelerin farklı parametre listeleri olmalıdır ve bir özellik veya yordamı aşırı yüklerken ayırt edici bir özellik olarak aşağıdaki öğeleri kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="6e744-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="6e744-114">Değiştiriciler, gibi `ByVal` veya `ByRef`, üye veya üyenin parametreleri geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6e744-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="6e744-115">Parametre adları</span><span class="sxs-lookup"><span data-stu-id="6e744-115">Names of parameters</span></span>

- <span data-ttu-id="6e744-116">Yordamları dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="6e744-116">Return types of procedures</span></span>

<span data-ttu-id="6e744-117">`Overloads` Aşırı yüklerken anahtar sözcüğü isteğe bağlı, ancak varsa aşırı üyeyi kullanan `Overloads` anahtar sözcüğü ve ardından aynı ada sahip diğer tüm aşırı yüklenmiş üyeler de belirtmelisiniz bu anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="6e744-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="6e744-118">Türetilen sınıfların aynı parametreleri ve parametre türleri olarak da bilinen bir işlem olan üyelere sahip devralınan üyeleri aşırı yükleme *ada ve imzaya göre gölgeleme*.</span><span class="sxs-lookup"><span data-stu-id="6e744-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="6e744-119">Varsa `Overloads` ada ve imzaya göre Gölgeleme, üyeyi türetilen sınıfın uygulaması temel sınıf uygulaması yerine kullanılır ve bu üye için diğer aşırı yüklemeler için örnekleri kullanılabilir olduğunda anahtar sözcüğü kullanılır türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="6e744-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="6e744-120">Varsa `Overloads` anahtar sözcüğü devralınan bir üyeyi aynı parametreleri ve parametre türlerine sahip bir üye ile aşırı yüklerken atlanırsa, ardından aşırı yükleme olarak adlandırılır *adıyla gölgeleme*.</span><span class="sxs-lookup"><span data-stu-id="6e744-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="6e744-121">Üye'nın devralınmış uygulaması adıyla gölgeleme değiştirir ve, diğer tüm aşırı yüklemeler türetilmiş sınıf ve onun decedents örneklerine kullanılamaz hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6e744-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="6e744-122">`Overloads` Ve `Shadows` değiştiriciler hem de kullanılamaz aynı özellik veya yöntem.</span><span class="sxs-lookup"><span data-stu-id="6e744-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="6e744-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e744-123">Example</span></span>

<span data-ttu-id="6e744-124">Aşağıdaki örnek, ya da kabul eden aşırı yüklenmiş yöntemler oluşturur. bir `String` veya `Decimal` dolar tutarını ve dönüş vergi içeren bir dize gösterimi.</span><span class="sxs-lookup"><span data-stu-id="6e744-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="6e744-125">Aşırı yüklenmiş bir yöntem oluşturmak için bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6e744-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="6e744-126">Adlı bir sınıf ekleyin ve yeni bir proje açmayı `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="6e744-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="6e744-127">Aşağıdaki kodu ekleyin `TaxClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6e744-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="6e744-128">Aşağıdaki yordam formunuza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e744-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="6e744-129">Çağrı ve form için bir düğme ekleyin `ShowTax` yordamdan `Button1_Click` düğmesinin olayı.</span><span class="sxs-lookup"><span data-stu-id="6e744-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="6e744-130">Projeyi çalıştırın ve Aşırı yüklenen test etmek için form üzerindeki düğmeye tıklayın `ShowTax` yordamı.</span><span class="sxs-lookup"><span data-stu-id="6e744-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="6e744-131">Çalışma zamanında derleyici kullanılmakta parametrelerle eşleşen Aşırı yüklenen işlevin uygun seçer.</span><span class="sxs-lookup"><span data-stu-id="6e744-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="6e744-132">Düğmeye tıkladığınızda, aşırı yüklenmiş yöntem ile ilk çağrılır bir `Price` parametresine bir dize ve iletinin "Fiyat bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="6e744-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="6e744-133">Vergi is $5,12" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e744-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="6e744-134">`TaxAmount` ile adlı bir `Decimal` ikinci kez ve ileti değeri, "Fiyat bir ondalık.</span><span class="sxs-lookup"><span data-stu-id="6e744-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="6e744-135">Vergi is $5,12" görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e744-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e744-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e744-136">See also</span></span>

- [<span data-ttu-id="6e744-137">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="6e744-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="6e744-138">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="6e744-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="6e744-139">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e744-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="6e744-140">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="6e744-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="6e744-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="6e744-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="6e744-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="6e744-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)
- [<span data-ttu-id="6e744-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="6e744-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)
- [<span data-ttu-id="6e744-144">Overloads</span><span class="sxs-lookup"><span data-stu-id="6e744-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="6e744-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="6e744-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)

---
title: Visual Basic'de diziler
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="8f5ff-102">Diziler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f5ff-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="8f5ff-103">Visual Basic 2017 ile başlayarak, Visual Basic Dil yapar diziler için yerleşik destek sunar tanımlama grupları oluşturma ve diziler daha kolay öğelerini erişme.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="8f5ff-104">Bir tanımlama grubu belirli sayıda ve değerleri dizisi olan bir hafif veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-104">A tuple is a light-weight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="8f5ff-105">Tuple örneği olduğunda sayısını ve her değeri (veya bir öğenin) veri türünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="8f5ff-106">Örneğin, bir 2 bölütlü (veya çifti) iki öğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="8f5ff-107">İlk olabilir bir `Boolean` değer ikinci olsa da bir `String`.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="8f5ff-108">Tanımlama grupları birden çok değeri tek bir nesnede depolama kolaylaştırmak için bunlar genellikle birden çok değer döndürme için basit bir yol olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f5ff-109">Tuple destek gerektiren <xref:System.ValueTuple> türü.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="8f5ff-110">.NET Framework 4.7 yüklü değilse, NuGet paketini eklemeniz gerekir `System.ValueTuple`, hangi kullanılabilir NuGet galerisinde.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="8f5ff-111">Bu paketi bir derleme hatası benzer şekilde, "'ValueTuple(Of,,,)' tanımlı veya alınmamış önceden tanımlanmış türü." alabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="8f5ff-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="8f5ff-112">Örnek oluşturma ve bir tanımlama grubu kullanma</span><span class="sxs-lookup"><span data-stu-id="8f5ff-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="8f5ff-113">Bir tanımlama grubu, virgülle ayrılmış değerler IM parantez kapsayan tarafından örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-113">You instantiate a tuple by enclosing its comma-delimited values im parentheses.</span></span> <span data-ttu-id="8f5ff-114">Bu değerlerin her birini daha sonra kayıt bir alan olur.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="8f5ff-115">Örneğin, aşağıdaki kodu Üçlü (veya 3-tanımlama grubu) ile tanımlayan bir `Date` ilk değeri olarak bir `String` , ikinci olarak ve bir `Boolean` kendi üçüncü olarak.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="8f5ff-116">Varsayılan olarak, bir tanımlama grubu içindeki her alan adını dizesi oluşur `Item` birlikte alanın tabanlı konumda yer alan tanımlama grubu.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="8f5ff-117">Bu 3-başlığı için `Date` alandır `Item1`, `String` alandır `Item2`ve `Boolean` alanı `Item3`.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="8f5ff-118">Aşağıdaki örnek kod önceki satırında örneği kayıt alanların değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="8f5ff-119">Visual Basic tanımlama grubu okuma-yazma alanlardır; bir tanımlama grubu örneği sonra değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="8f5ff-120">Aşağıdaki örnek önceki örnekte oluşturulan tanımlama grubu üç alanlarını ikilisi değiştirir ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="8f5ff-121">Örnek oluşturma ve adlandırılmış bir tanımlama grubu kullanma</span><span class="sxs-lookup"><span data-stu-id="8f5ff-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="8f5ff-122">Demete ait alanları için varsayılan adlar kullanmak yerine, bir örneğini oluşturabilirsiniz bir *tanımlama grubu adlı* demete ait öğelerine kendi adlarınızı atayarak.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="8f5ff-123">Demete ait alanlara sonra atanan adlarıyla erişilebilir *veya* varsayılan adlarına göre.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="8f5ff-124">Açıkça ilk alan adları dışında aynı 3-tanımlama grubu olarak daha önce aşağıdaki örnek başlatır `EventDate`, ikinci `Name`ve üçüncü `IsHoliday`.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="8f5ff-125">Bunu ardından alan değerlerini, bunları değiştirir ve alan değerlerini yeniden görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="8f5ff-126">Çıkarsanan tanımlama grubu öğe adları</span><span class="sxs-lookup"><span data-stu-id="8f5ff-126">Inferred tuple element names</span></span>

<span data-ttu-id="8f5ff-127">Visual Basic, Visual Basic 15.3 ile başlayarak, başlığın öğeleri adlarının çıkarımını; açıkça atamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="8f5ff-128">Çıkarsanan tanımlama grubu adları değişkenleri kümesinden bir tanımlama grubu başlatmak ve tanımlama grubu öğe adı değişken adı ile aynı olacak şekilde istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span> 

<span data-ttu-id="8f5ff-129">Aşağıdaki örnekte bir `stateInfo` üç açıkça içeren tanımlama grubu adlı öğeleri `state`, `stateName`, ve `capital`.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="8f5ff-130">Öğeleri adlandırmada tanımlama grubu başlatma deyimi yalnızca adlandırılmış öğeleri aynı adlı değişkenlerin değerleri atar, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
<span data-ttu-id="8f5ff-131">Visual Basic derleyici öğeleri ve değişkenleri aynı ada sahip olduğundan, aşağıdaki örnekte gösterildiği gibi alanların adlarını çıkarımını.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="8f5ff-132">İnterred tanımlama grubu öğe adları etkinleştirmek için Visual Basic projesinde kullanmak için Visual Basic derleyici sürümünü tanımlama (\*.vbproj) dosyası:</span><span class="sxs-lookup"><span data-stu-id="8f5ff-132">To enable interred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span> 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="8f5ff-133">Diziler yöntemi olarak dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="8f5ff-133">Tuples as method return values</span></span>

<span data-ttu-id="8f5ff-134">Bir yöntem yalnızca tek bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-134">A method can return only a single value.</span></span> <span data-ttu-id="8f5ff-135">Sık sık rağmen birden çok değer döndürmek için bir yöntem çağrısı istersiniz.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-135">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="8f5ff-136">Bu sınırlamaya geçici bir çözüm için birkaç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="8f5ff-136">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="8f5ff-137">Özel sınıf veya yapı özellikleri oluşturabilir veya alanlar yöntemi tarafından döndürülen değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-137">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="8f5ff-138">Bu nedenle bir ağır çözümdür; Bu yöntem çağrısından değerleri almak için tek amacı olan bir özel tür tanımlamanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-138">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="8f5ff-139">Tek bir değer döndürme ve yöntemine başvuruya geçirerek kalan değerler döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-139">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="8f5ff-140">Bu değişken ve başvuruya göre geçirme değişkenin değerini yanlışlıkla üzerine riskleri başlatmasını yükünü içerir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-140">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="8f5ff-141">Birden çok dönüş değerleri alma için basit bir çözüm sağlar bir tanımlama grubu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-141">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="8f5ff-142">Örneğin, **TryParseyöntemini** .NET return yöntemleri bir `Boolean` ayrıştırma işlemi başarılı olup olmadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-142">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="8f5ff-143">Ayrıştırma işleminin sonucu başvuruya yöntemine geçirilen bir değişken döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-143">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="8f5ff-144">Normal olarak yapılan bir çağrı gibi ayrıştırma yönteminin <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="8f5ff-144">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="8f5ff-145">Biz çağrısı sarmalama, biz bir tanımlama grubu ayrıştırma işlemi döndürebilir <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> kendi yöntemi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-145">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="8f5ff-146">Aşağıdaki örnekte, `NumericLibrary.ParseInteger` çağrıları <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemi ve iki öğe ile adlandırılmış bir tanımlama grubu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-146">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span> 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="8f5ff-147">Ardından aşağıdaki gibi kod ile yöntemi çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8f5ff-147">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="8f5ff-148">Visual Basic başlıkları ve .NET Framework diziler</span><span class="sxs-lookup"><span data-stu-id="8f5ff-148">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="8f5ff-149">Visual Basic tanımlama grubu birinin örneğidir **System.ValueTuple** .NET Framework 4.7 içinde sunulan genel türler.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-149">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="8f5ff-150">.NET Framework genel bir dizi de içerir **System.Tuple** sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-150">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="8f5ff-151">Bu sınıfları, ancak Visual Basic diziler farklı ve **System.ValueTuple** çeşitli yollarla genel türleri:</span><span class="sxs-lookup"><span data-stu-id="8f5ff-151">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="8f5ff-152">Öğelerini **tanımlama grubu** sınıflardır adlı özellikleri `Item1`, `Item2`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-152">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="8f5ff-153">Visual Basic dizilerde ve **ValueTuple** türleri, başlığın öğeleri alanlardır.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-153">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="8f5ff-154">Anlamlı adlar öğelerine atayamazsınız bir **tanımlama grubu** örneği veya bir **ValueTuple** örneği.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-154">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="8f5ff-155">Visual Basic, alanları anlamını iletişim adları atamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-155">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="8f5ff-156">Özelliklerini bir **tanımlama grubu** örnek salt okunur; başlıklar değişmez.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-156">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="8f5ff-157">Visual Basic dizilerde ve **ValueTuple** türleri tanımlama grubu alanlardır okuma-yazma; başlıklar değişebilir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-157">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="8f5ff-158">Genel **tanımlama grubu** türleri başvuru türleridir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-158">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="8f5ff-159">Bunlar kullanarak **tanımlama grubu** türleri nesneleri ayırma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-159">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="8f5ff-160">Sık kullanılan yollarına göre bu, uygulamanızın performans üzerinde ölçülebilir bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-160">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="8f5ff-161">Visual Basic başlıkları ve **ValueTuple** değer türleri türleridir.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-161">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="8f5ff-162">Genişletme yöntemleri <xref:System.TupleExtensions> sınıfı kolaylaştırır Visual Basic başlıkları ve .NET arasında dönüştürme **tanımlama grubu** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-162">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="8f5ff-163">**ToTuple** yöntemi dönüştürür Visual Basic tanımlama grubu için bir .NET **tanımlama grubu** nesnesi ve **ToValueTuple** yöntemi bir .NET dönüştürür **tanımlama grubu** Visual Basic tanımlama grubu nesne.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-163">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="8f5ff-164">Aşağıdaki örnek bir tanımlama grubu oluşturur, bir .NET dönüştürür **tanımlama grubu** nesne ve bir Visual Basic tanımlama grubu geri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-164">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="8f5ff-165">Örnek daha sonra bu tanımlama grubu eşit olduğundan emin olmak için özgün bir karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-165">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="8f5ff-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f5ff-166">See also</span></span>

[<span data-ttu-id="8f5ff-167">Visual Basic Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8f5ff-167">Visual Basic Language Reference</span></span>](index.md)  

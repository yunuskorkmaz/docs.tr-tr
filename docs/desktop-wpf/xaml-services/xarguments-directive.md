---
title: x:Arguments Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071593"
---
# <a name="xarguments-directive"></a><span data-ttu-id="43a3d-102">x:Arguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="43a3d-102">x:Arguments Directive</span></span>

<span data-ttu-id="43a3d-103">XAML'de parametresiz olmayan bir yapı oluşturucu nesne öğesi bildirimi veya fabrika yöntemi nesne bildirimi için yapı bağımsız değişkenlerini paketler.</span><span class="sxs-lookup"><span data-stu-id="43a3d-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>

## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="43a3d-104">XAML Eleman Kullanımı (Parametresiz yapıcı)</span><span class="sxs-lookup"><span data-stu-id="43a3d-104">XAML Element Usage (Nonparameterless constructor)</span></span>

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="43a3d-105">XAML Eleman Kullanımı (fabrika yöntemi)</span><span class="sxs-lookup"><span data-stu-id="43a3d-105">XAML Element Usage (factory method)</span></span>

```xaml
<object x:FactoryMethod="methodName"...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="43a3d-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="43a3d-106">XAML Values</span></span>

|||
|-|-|
|`oneOrMoreObjectElements`|<span data-ttu-id="43a3d-107">Parametresiz olmayan kurucu veya fabrika yöntemine geçirilecek bağımsız değişkenleri belirten bir veya daha fazla nesne öğesi.</span><span class="sxs-lookup"><span data-stu-id="43a3d-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="43a3d-108">Tipik kullanım, nesne öğeleri içindeki başlatma metnini kullanarak gerçek bağımsız değişken değerlerini belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="43a3d-109">Örnekler bölümüne bakınız.</span><span class="sxs-lookup"><span data-stu-id="43a3d-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="43a3d-110">Elementlerin sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-110">The order of the elements is significant.</span></span> <span data-ttu-id="43a3d-111">Sırayla XAML türleri, destek oluşturucu veya fabrika yöntemi aşırı yüklemesinin türleri ve türü sırasına uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43a3d-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|
|`methodName`|<span data-ttu-id="43a3d-112">Herhangi bir `x:Arguments` bağımsız değişkeni işlemesi gereken fabrika yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="43a3d-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="43a3d-113">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="43a3d-113">Dependencies</span></span>

<span data-ttu-id="43a3d-114">`x:FactoryMethod`uygulandığı durumlarda `x:Arguments` kapsamı ve davranışı değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>

<span data-ttu-id="43a3d-115">Hiçbir `x:FactoryMethod` şey belirtilmemişse, `x:Arguments` destek oluşturucuların alternatif (varsayılan olmayan) imzaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>

<span data-ttu-id="43a3d-116">`x:FactoryMethod` Belirtilirse, `x:Arguments` adlandırılmış yöntemin aşırı yüklenmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>

## <a name="remarks"></a><span data-ttu-id="43a3d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43a3d-117">Remarks</span></span>

<span data-ttu-id="43a3d-118">XAML 2006, başlatma metni aracılığıyla varsayılan olmayan başlatmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="43a3d-119">Ancak, bir başlatma metin yapım tekniğinin pratik uygulama sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="43a3d-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="43a3d-120">Başlatma metni tek bir metin dizesi olarak kabul edilir; bu nedenle, özel bilgi öğelerini ve özel sınır aşanları dizeden ayrıştırabilen yapı davranışı için bir tür dönüştürücü tanımlanmadıkça, yalnızca tek bir parametre başlatma özelliği ekler.</span><span class="sxs-lookup"><span data-stu-id="43a3d-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="43a3d-121">Ayrıca, nesne mantığımetin dize potansiyel olarak gerçek bir dize dışında ilkel işlemek için verilen bir XAML parleyici yerel varsayılan türü dönüştürücüdür.</span><span class="sxs-lookup"><span data-stu-id="43a3d-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>

<span data-ttu-id="43a3d-122">`x:Arguments` XAML kullanımı, yönerge biçimlendirmesi içeren nesne öğe öğesinin türüne başvurmadığından, tipik anlamda özellik öğesi kullanımı değildir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="43a3d-123">Bu, öğenin biçimlendirmenin `x:Code` alt içerikler için varsayılan dan başka bir aralık olarak yorumlanması gereken bir aralığı işaretlediği yer gibi diğer yönergelere daha çok benzer.</span><span class="sxs-lookup"><span data-stu-id="43a3d-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="43a3d-124">Bu durumda, her nesne öğesinin XAML türü, xaml parsers tarafından hangi belirli kurucu fabrika yöntemi imzasını `x:Arguments` belirlemek için kullanılan bağımsız değişken türleri hakkında bilgi iletir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>

<span data-ttu-id="43a3d-125">`x:Arguments`yapılandırılan bir nesne öğesi için nesne öğesinin diğer özellik öğelerinden, içeriğinden, iç metinden veya başlatma dizelerinden önce olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43a3d-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="43a3d-126">İçerdeki `x:Arguments` nesne öğeleri, xaml türü ve onun destek oluşturucusu veya fabrika yönteminin izin verdiği gibi öznitelikleri ve başlatma dizeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="43a3d-127">Nesne veya bağımsız değişkenler için, yerleşik önek eşlemelerine başvurarak varsayılan XAML ad alanının dışında olan özel XAML türleri veya XAML türleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43a3d-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>

<span data-ttu-id="43a3d-128">XAML işlemciler, bir nesne oluşturmak için `x:Arguments` belirtilen bağımsız değişkenlerin nasıl kullanılması gerektiğini belirlemek için aşağıdaki yönergeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="43a3d-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="43a3d-129">`x:FactoryMethod` Belirtilirse, bilgiler belirtilenle `x:FactoryMethod` karşılaştırılır (değerin `x:FactoryMethod` yöntem adı olduğunu ve adlandırılmış yöntemin aşırı yüklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="43a3d-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="43a3d-130">`x:FactoryMethod` Belirtilmemişse, bilgiler nesnenin tüm ortak yapı oluşturma kümesiyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="43a3d-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="43a3d-131">XAML işleme mantığı daha sonra parametrelerin sayısını karşılaştırır ve aşırı yükü eşleşen arite ile seçer.</span><span class="sxs-lookup"><span data-stu-id="43a3d-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="43a3d-132">Birden fazla eşleşme varsa, XAML işlemci sağlanan nesne elemanlarının XAML türlerine dayalı parametre türlerini karşılaştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43a3d-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="43a3d-133">Hala birden fazla eşleşme varsa, XAML işlemci davranışı tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="43a3d-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="43a3d-134">A `x:FactoryMethod` belirtilmişse ancak yöntem çözülemiyorsa, Bir XAML işlemci bir özel durum atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43a3d-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>

<span data-ttu-id="43a3d-135">XAML öznitelik `<x:Arguments>string</x:Arguments>` kullanımı teknik olarak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="43a3d-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="43a3d-136">Ancak, bu, başlatma metni ve tür dönüştürücüler aracılığıyla başka türlü yapılabileceklerin ötesinde hiçbir yetenek sağlamaz ve bu sözdizimini kullanmak XAML 2009 fabrika yöntemi özelliklerinin tasarım amacı değildir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>

## <a name="examples"></a><span data-ttu-id="43a3d-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="43a3d-137">Examples</span></span>

<span data-ttu-id="43a3d-138">Aşağıdaki örnek, parametresiz olmayan bir yapıcı imzasını, daha `x:Arguments` sonra bu imzaya erişen XAML kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43a3d-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

```csharp
public class Food {
  private string _name;
  private Int32 _calories;
  public Food(string name, Int32 calories) {
      _name=name;
      _calories=calories;
  }
}
```

```xaml
<my:Food>
  <x:Arguments>
      <x:String>Apple</x:String>
      <x:Int32>150</x:Int32>
  </x:Arguments>
</my:Food>
```

<span data-ttu-id="43a3d-139">Aşağıdaki örnek, bir hedef fabrika yöntemi imzasını gösterir, ardından bu imzaya erişen in XAML `x:Arguments` kullanımı.</span><span class="sxs-lookup"><span data-stu-id="43a3d-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

```csharp
public Food TryLookupFood(string name)
{
switch (name) {
  case "Apple": return new Food("Apple",150);
  case "Chocolate": return new Food("Chocolate",200);
  case "Cheese": return new Food("Cheese", 450);
  default: {return new Food(name,0);
}
}
```

```xaml
<my:Food x:FactoryMethod="TryLookupFood">
  <x:Arguments>
      <x:String>Apple</x:String>
  </x:Arguments>
</my:Food>
```

## <a name="see-also"></a><span data-ttu-id="43a3d-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43a3d-140">See also</span></span>

- [<span data-ttu-id="43a3d-141">.NET XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="43a3d-141">Defining Custom Types for Use with .NET XAML Services</span></span>](define-custom-types.md)
- [<span data-ttu-id="43a3d-142">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="43a3d-142">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)

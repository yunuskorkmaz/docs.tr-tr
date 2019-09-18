---
title: x:Arguments Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a18de9a07839f5b01620311832b85667680c12ad
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053827"
---
# <a name="xarguments-directive"></a><span data-ttu-id="ffbdd-102">x:Arguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="ffbdd-102">x:Arguments Directive</span></span>
<span data-ttu-id="ffbdd-103">XAML içindeki parametresiz bir Oluşturucu nesne öğesi bildirimi veya bir Factory yöntemi nesne bildirimi için paket oluşturma bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="ffbdd-104">XAML öğesi kullanımı (parametresiz Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="ffbdd-104">XAML Element Usage (Nonparameterless constructor)</span></span>  
  
```xaml  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="ffbdd-105">XAML öğesi kullanımı (Factory yöntemi)</span><span class="sxs-lookup"><span data-stu-id="ffbdd-105">XAML Element Usage (factory method)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="ffbdd-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="ffbdd-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="ffbdd-107">, Parametresiz oluşturucuya veya fabrika yöntemine geçirilecek bağımsız değişkenleri belirten bir veya daha fazla nesne öğesi.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="ffbdd-108">Tipik kullanım, gerçek bağımsız değişken değerlerini belirtmek için nesne öğeleri içinde başlatma metni kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="ffbdd-109">Örnekler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="ffbdd-110">Öğelerin sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-110">The order of the elements is significant.</span></span> <span data-ttu-id="ffbdd-111">Sırasıyla XAML türleri, yedekleme oluşturucusunun veya fabrika yöntemi aşırı yüklemesinin türleri ve tür sırasıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="ffbdd-112">Herhangi bir `x:Arguments` bağımsız değişkeni işlemesi gereken fabrika yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="ffbdd-113">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="ffbdd-113">Dependencies</span></span>  
 <span data-ttu-id="ffbdd-114">`x:FactoryMethod`, geçerli olduğu yerde `x:Arguments` kapsamı ve davranışı değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="ffbdd-115">Hayır `x:FactoryMethod` belirtilirse, `x:Arguments` yedekleme oluşturucuların alternatif (varsayılan olmayan) imzaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="ffbdd-116">`x:FactoryMethod` Belirtilmişse ,`x:Arguments` adlandırılmış yöntemin aşırı yüklemesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffbdd-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffbdd-117">Remarks</span></span>  
 <span data-ttu-id="ffbdd-118">XAML 2006, başlatma metni aracılığıyla varsayılan olmayan başlatmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="ffbdd-119">Ancak, bir başlatma metni oluşturma tekniğinin pratik uygulaması sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="ffbdd-120">Başlatma metni tek bir metin dizesi olarak değerlendirilir; Bu nedenle, özel bilgi öğelerini ve dizeden özel sınırlayıcıları ayrıştırabilen oluşturma davranışı için bir tür dönüştürücüsü tanımlanmadığı müddetçe yalnızca tek bir parametre başlatması için yetenek ekler.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="ffbdd-121">Ayrıca, nesne mantığından metin dizesi büyük olasılıkla belirli bir XAML ayrıştırıcısının, doğru bir dize dışındaki temelleri işlemek için yerel varsayılan tür dönüştürücütür.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="ffbdd-122">`x:Arguments` XAML kullanımı tipik anlamda Özellik öğesi kullanımı değildir, çünkü yönerge biçimlendirmesi kapsayan nesne öğesinin türüne başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="ffbdd-123">Bu, öğenin, biçimlendirmenin alt içerik için varsayılan değer `x:Code` olarak yorumlanacağı bir aralığı nerede işaretlediği gibi diğer yönergelere daha fazla oturum açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="ffbdd-124">Bu durumda, her bir nesne öğesinin xaml türü, bir `x:Arguments` kullanımın başvuruya hangi belirli Oluşturucu fabrikası için imza olduğunu belirleyen xaml Çözümleyicileri tarafından kullanılan bağımsız değişken türleriyle ilgili bilgileri iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="ffbdd-125">`x:Arguments`oluşturulmakta olan bir nesne öğesinin, nesne öğesinin diğer özellik öğelerinden, içerik, iç metin veya başlatma dizelerinin önünde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="ffbdd-126">İçindeki `x:Arguments` nesne öğeleri, bu xaml türü ve onun yedekleme Oluşturucusu ya da fabrika yöntemi tarafından izin verilen öznitelikleri ve başlatma dizelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="ffbdd-127">Nesne veya bağımsız değişkenler için, oluşturulan önek eşlemelerine başvurarak varsayılan XAML ad alanı dışındaki özel XAML türlerini veya XAML türlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="ffbdd-128">XAML işlemcileri, ' de `x:Arguments` belirtilen bağımsız değişkenlerin bir nesne oluşturmak için nasıl kullanılması gerektiğini belirlemede aşağıdaki yönergeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="ffbdd-129">Belirtilmişse, bilgiler belirtilen `x:FactoryMethod` ile karşılaştırılır (değerinin yöntemin adı `x:FactoryMethod` olduğunu ve adlandırılmış yöntemin aşırı yüklemeleri olabileceğini unutmayın. `x:FactoryMethod`</span><span class="sxs-lookup"><span data-stu-id="ffbdd-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="ffbdd-130">`x:FactoryMethod` Belirtilmemişse, bilgiler nesnenin tüm genel Oluşturucu aşırı yüklerini kümesiyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="ffbdd-131">XAML işleme mantığı, parametre sayısını karşılaştırır ve eşleşen parametre sayısına sahip aşırı yüklemeyi seçer.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="ffbdd-132">Birden fazla eşleşme varsa, XAML işlemcisi parametrelerin türlerini, belirtilen nesne öğelerinin XAML türlerine göre karşılaştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="ffbdd-133">Hala birden fazla eşleşme varsa XAML işlemci davranışı tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="ffbdd-134">Bir `x:FactoryMethod` , belirtilmişse ancak yöntem çözümlenemiyorsa, bir XAML işlemcisi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="ffbdd-135">XAML öznitelik kullanımı `<x:Arguments>string</x:Arguments>` teknik açıdan mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="ffbdd-136">Bununla birlikte, bu, başlatma metni ve tür dönüştürücüler aracılığıyla ne yapabileceğinize ilişkin hiçbir özellik sağlamaz ve bu sözdiziminin kullanılması XAML 2009 fabrika yöntemi özelliklerinin tasarım amacı değildir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ffbdd-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ffbdd-137">Examples</span></span>  
 <span data-ttu-id="ffbdd-138">Aşağıdaki örnek, parametresiz bir Oluşturucu imzasını, ardından bu imzaya erişen xaml kullanımını `x:Arguments` gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="ffbdd-139">Aşağıdaki örnek, bir hedef fabrika yöntemi imzasını, ardından bu imzaya erişen xaml kullanımını `x:Arguments` gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ffbdd-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffbdd-140">See also</span></span>

- [<span data-ttu-id="ffbdd-141">.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="ffbdd-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="ffbdd-142">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="ffbdd-142">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)

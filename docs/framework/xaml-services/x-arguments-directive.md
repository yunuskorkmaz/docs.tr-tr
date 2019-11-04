---
title: x:Arguments Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 338286b417c78b7cceeb30188e888928a15607cd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458660"
---
# <a name="xarguments-directive"></a><span data-ttu-id="79147-102">x:Arguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="79147-102">x:Arguments Directive</span></span>
<span data-ttu-id="79147-103">XAML içindeki parametresiz bir Oluşturucu nesne öğesi bildirimi veya bir Factory yöntemi nesne bildirimi için paket oluşturma bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="79147-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="79147-104">XAML öğesi kullanımı (parametresiz Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="79147-104">XAML Element Usage (Nonparameterless constructor)</span></span>  
  
```xaml  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="79147-105">XAML öğesi kullanımı (Factory yöntemi)</span><span class="sxs-lookup"><span data-stu-id="79147-105">XAML Element Usage (factory method)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="79147-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="79147-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="79147-107">, Parametresiz oluşturucuya veya fabrika yöntemine geçirilecek bağımsız değişkenleri belirten bir veya daha fazla nesne öğesi.</span><span class="sxs-lookup"><span data-stu-id="79147-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="79147-108">Tipik kullanım, gerçek bağımsız değişken değerlerini belirtmek için nesne öğeleri içinde başlatma metni kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="79147-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="79147-109">Örnekler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="79147-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="79147-110">Öğelerin sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="79147-110">The order of the elements is significant.</span></span> <span data-ttu-id="79147-111">Sırasıyla XAML türleri, yedekleme oluşturucusunun veya fabrika yöntemi aşırı yüklemesinin türleri ve tür sırasıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="79147-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="79147-112">`x:Arguments` bağımsız değişkenlerini işlemek zorunda olan Factory yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="79147-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="79147-113">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="79147-113">Dependencies</span></span>  
 <span data-ttu-id="79147-114">`x:FactoryMethod`, `x:Arguments` uygulandığı kapsam ve davranışı değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="79147-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="79147-115">`x:FactoryMethod` belirtilmemişse `x:Arguments`, yedekleme oluşturucuların alternatif (varsayılan olmayan) imzaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="79147-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="79147-116">`x:FactoryMethod` belirtilirse, `x:Arguments` adlandırılmış yöntemin aşırı yüklemesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="79147-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79147-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79147-117">Remarks</span></span>  
 <span data-ttu-id="79147-118">XAML 2006, başlatma metni aracılığıyla varsayılan olmayan başlatmayı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="79147-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="79147-119">Ancak, bir başlatma metni oluşturma tekniğinin pratik uygulaması sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="79147-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="79147-120">Başlatma metni tek bir metin dizesi olarak değerlendirilir; Bu nedenle, özel bilgi öğelerini ve dizeden özel sınırlayıcıları ayrıştırabilen oluşturma davranışı için bir tür dönüştürücüsü tanımlanmadığı müddetçe yalnızca tek bir parametre başlatması için yetenek ekler.</span><span class="sxs-lookup"><span data-stu-id="79147-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="79147-121">Ayrıca, nesne mantığından metin dizesi büyük olasılıkla belirli bir XAML ayrıştırıcısının, doğru bir dize dışındaki temelleri işlemek için yerel varsayılan tür dönüştürücütür.</span><span class="sxs-lookup"><span data-stu-id="79147-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="79147-122">`x:Arguments` XAML kullanımı, yönerge işaretlemesi kapsayan nesne öğesinin türüne başvurmadığından tipik anlamda Özellik öğesi kullanımı değildir.</span><span class="sxs-lookup"><span data-stu-id="79147-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="79147-123">`x:Code` gibi diğer yönergelere daha fazla oturum vardır; burada öğe, biçimlendirmenin alt içerik için varsayılan değer olarak yorumlanacağı bir aralığı işaretler.</span><span class="sxs-lookup"><span data-stu-id="79147-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="79147-124">Bu durumda, her bir nesne öğesinin XAML türü, `x:Arguments` kullanımı için hangi belirli Oluşturucu fabrikası yönteminin başvurulmaya çalışacağını belirleyen XAML Çözümleyicileri tarafından kullanılan bağımsız değişken türleriyle ilgili bilgileri iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="79147-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="79147-125">oluşturulan nesne öğesi için `x:Arguments`, nesne öğesinin diğer özellik öğelerinden, içerikten, iç metinden veya başlatma dizelerinden önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="79147-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="79147-126">`x:Arguments` içindeki nesne öğeleri, bu XAML türü ve onun yedekleme Oluşturucusu ya da fabrika yöntemi tarafından izin verilen öznitelikleri ve başlatma dizelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="79147-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="79147-127">Nesne veya bağımsız değişkenler için, oluşturulan önek eşlemelerine başvurarak varsayılan XAML ad alanı dışındaki özel XAML türlerini veya XAML türlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79147-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="79147-128">XAML işlemcileri, `x:Arguments` ' de belirtilen bağımsız değişkenlerin bir nesne oluşturmak için nasıl kullanılacağını belirlemede aşağıdaki yönergeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="79147-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="79147-129">`x:FactoryMethod` belirtilirse, bilgiler belirtilen `x:FactoryMethod` karşılaştırılır (`x:FactoryMethod` değerinin Yöntem adı olduğunu ve adlandırılmış yöntemin aşırı yüklemeleri olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="79147-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="79147-130">`x:FactoryMethod` belirtilmemişse, bilgiler nesnenin tüm genel Oluşturucu aşırı yüklerini kümesiyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="79147-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="79147-131">XAML işleme mantığı, parametre sayısını karşılaştırır ve eşleşen parametre sayısına sahip aşırı yüklemeyi seçer.</span><span class="sxs-lookup"><span data-stu-id="79147-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="79147-132">Birden fazla eşleşme varsa, XAML işlemcisi parametrelerin türlerini, belirtilen nesne öğelerinin XAML türlerine göre karşılaştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="79147-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="79147-133">Hala birden fazla eşleşme varsa XAML işlemci davranışı tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="79147-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="79147-134">Bir `x:FactoryMethod` belirtilirse, ancak yöntem çözümlenemiyorsa, bir XAML işlemcisi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="79147-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="79147-135">XAML öznitelik kullanımı `<x:Arguments>string</x:Arguments>` teknik açıdan mümkündür.</span><span class="sxs-lookup"><span data-stu-id="79147-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="79147-136">Bununla birlikte, bu, başlatma metni ve tür dönüştürücüler aracılığıyla ne yapabileceğinize ilişkin hiçbir özellik sağlamaz ve bu sözdiziminin kullanılması XAML 2009 fabrika yöntemi özelliklerinin tasarım amacı değildir.</span><span class="sxs-lookup"><span data-stu-id="79147-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="79147-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="79147-137">Examples</span></span>  
 <span data-ttu-id="79147-138">Aşağıdaki örnek, parametresiz bir Oluşturucu imzasını, ardından bu imzaya erişen `x:Arguments` XAML kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="79147-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="79147-139">Aşağıdaki örnek, bir hedef fabrika yöntemi imzasını, ardından bu imzaya erişen `x:Arguments` XAML kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="79147-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79147-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79147-140">See also</span></span>

- [<span data-ttu-id="79147-141">.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="79147-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="79147-142">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="79147-142">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)

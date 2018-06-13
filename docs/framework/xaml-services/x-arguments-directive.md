---
title: x:Arguments Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: e0e7f380ec176e80d2422878a2e676d64985d660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564884"
---
# <a name="xarguments-directive"></a><span data-ttu-id="5c1c1-102">x:Arguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5c1c1-102">x:Arguments Directive</span></span>
<span data-ttu-id="5c1c1-103">Paketler yapı değişkenleri XAML varsayılan olmayan Oluşturucusu nesne öğesi bildiriminde ya da bir fabrika yöntemi nesne bildirimi.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="5c1c1-104">XAML öğesi kullanımı (varsayılan olmayan Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="5c1c1-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="5c1c1-105">XAML öğesi kullanımı (fabrika yöntemi)</span><span class="sxs-lookup"><span data-stu-id="5c1c1-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5c1c1-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="5c1c1-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="5c1c1-107">Yedekleme varsayılan olmayan Oluşturucusu veya Fabrika yönteme iletilecek bağımsız değişkenleri belirtin bir veya daha fazla nesne öğeleri.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="5c1c1-108">Tipik kullanım gerçek bağımsız değişken değerleri belirtmek için nesne öğeleri başlatma metinde kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="5c1c1-109">Örnekler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="5c1c1-110">Öğelerin sırasını önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-110">The order of the elements is significant.</span></span> <span data-ttu-id="5c1c1-111">XAML türleri sırayla türlerinin eşleşmesi gerekir ve yedekleme Oluşturucusu veya Fabrika yöntemi aşırı yüklemesini sırasını yazın.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="5c1c1-112">Herhangi bir işlem Fabrika yöntemin adını `x:Arguments` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="5c1c1-113">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="5c1c1-113">Dependencies</span></span>  
 <span data-ttu-id="5c1c1-114">`x:FactoryMethod` kapsam ve davranışını değiştirebilirsiniz nerede `x:Arguments` uygular.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="5c1c1-115">Öyle değilse `x:FactoryMethod` belirtilirse, `x:Arguments` yedekleme oluşturucular alternatif (varsayılan olmayan) imzalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="5c1c1-116">Varsa `x:FactoryMethod` belirtilirse, `x:Arguments` bir adlandırılmış yöntemi aşırı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c1c1-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c1c1-117">Remarks</span></span>  
 <span data-ttu-id="5c1c1-118">XAML 2006 varsayılan olmayan başlatma başlatma metin aracılığıyla destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="5c1c1-119">Ancak, bir başlatma metin oluşturma teknik pratik uygulamasının sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="5c1c1-120">Başlatma metin tek bir metin dizesi kabul edilir; Bu nedenle, özel bilgiler öğeleri ve özel sınırlayıcıları dizesinden ayrıştıramıyor oluşturma davranışı için tür dönüştürücüsünü tanımlanmadıkça yalnızca tek bir parametre başlatma için özelliğini ekler.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="5c1c1-121">Ayrıca, nesne mantığı potansiyel olarak doğru bir dize dışında temelleri işleme için belirli bir XAML Ayrıştırıcıyı ait yerel varsayılan türü dönüştürücü metindir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="5c1c1-122">`x:Arguments` XAML kullanımı tipik herkese açık özellik öğesi kullanımı yönerge biçimlendirme içeren nesne öğenin türü başvurmuyor olmadığından değil.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="5c1c1-123">Gibi diğer yönergeleri benzer daha fazla `x:Code` burada öğesi demarks içinde işaretleme kabul varsayılandan gibi alt içeriği için bir aralığı.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="5c1c1-124">Bu durumda, her nesne öğesi XAML tür XAML ayrıştırıcıları göre hangi belirli Oluşturucusu fabrika yöntemi imza belirlemek için kullanılan bağımsız değişken türleri hakkında bilgi iletişim kuran bir `x:Arguments` kullanım başvurmak çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="5c1c1-125">`x:Arguments` bir nesne öğesi için yapılandırılan herhangi diğer özellik öğelerinin, içerik, iç metni veya başlatma dizeleri nesne öğesinin gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="5c1c1-126">İçinde nesne öğelerin `x:Arguments` öznitelikleri ve başlatma dizeleri XAML türü ve yedekleme Oluşturucusu veya Fabrika yöntemi tarafından izin verildiği şekilde içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="5c1c1-127">Nesne veya bağımsız değişkenler için özel XAML türler veya aksi takdirde varsayılan XAML ad uzayı dışında kurulan önek eşlemeleri başvurarak XAML türlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="5c1c1-128">XAML işlemcileri bağımsız değişkenleri nasıl belirtilen belirlemek için aşağıdaki kılavuzları kullanın `x:Arguments` bir nesne oluşturmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="5c1c1-129">Varsa `x:FactoryMethod` belirtilirse, bilgi karşılaştırıldığı belirtilen `x:FactoryMethod` (unutmayın değerini `x:FactoryMethod` yöntem adı ve adlandırılmış yöntemi aşırı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="5c1c1-130">Varsa `x:FactoryMethod` belirtilmezse, bilgi nesnesinin tüm ortak oluşturucu aşırı kümesine karşılaştırılan.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="5c1c1-131">XAML işleme mantığı sonra parametrelerin sayısı karşılaştırır ve eşleşen parametre ile aşırı seçer.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="5c1c1-132">Birden fazla eşleşme varsa XAML işlemci sağlanan nesne öğeleri XAML türlerine göre parametre türlerini karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="5c1c1-133">XAML işlemci davranış hala birden fazla eşleşme varsa, tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="5c1c1-134">Varsa bir `x:FactoryMethod` belirtildi, ancak yöntem çözümlenemiyor, XAML işlemci bir özel durum oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="5c1c1-135">XAML öznitelik kullanımı `<x:Arguments>string</x:Arguments>` teknik olarak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="5c1c1-136">Ancak, bu ne aksi başlatma metin ve tür dönüştürücüleri yapılabilir ötesinde hiçbir özellikleri sağlar ve bu sözdiziminin kullanıldığı XAML 2009 fabrika yöntemi özellikleri tasarım amacı değil.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5c1c1-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5c1c1-137">Examples</span></span>  
 <span data-ttu-id="5c1c1-138">Aşağıdaki örnek, varsayılan olmayan bir oluşturucu imza sonra XAML kullanımını gösterir `x:Arguments` Bu imza erişir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="5c1c1-139">Aşağıdaki örnek, bir hedef fabrika yöntemi imzası sonra XAML kullanımını gösterir `x:Arguments` Bu imza erişir.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c1c1-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c1c1-140">See Also</span></span>  
 [<span data-ttu-id="5c1c1-141">.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="5c1c1-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [<span data-ttu-id="5c1c1-142">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="5c1c1-142">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)

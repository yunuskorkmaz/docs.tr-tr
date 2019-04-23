---
title: x:Arguments Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a87542513ffeeec7efc526d4218f921d1b7579a1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184853"
---
# <a name="xarguments-directive"></a><span data-ttu-id="4a743-102">x:Arguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="4a743-102">x:Arguments Directive</span></span>
<span data-ttu-id="4a743-103">Paketleri yapım bağımsız XAML varsayılan olmayan bir oluşturucu nesne öğe bildiriminde ya da bir fabrika yöntemi nesne bildirimi.</span><span class="sxs-lookup"><span data-stu-id="4a743-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="4a743-104">XAML öğesi kullanımı (varsayılan oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="4a743-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="4a743-105">XAML öğesi kullanımı (Üreteç yöntemi)</span><span class="sxs-lookup"><span data-stu-id="4a743-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4a743-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="4a743-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="4a743-107">Yedekleme varsayılan olmayan oluşturucu veya Fabrika yöntemine geçirilecek bağımsız değişkenleri belirten bir veya daha fazla nesne öğeler.</span><span class="sxs-lookup"><span data-stu-id="4a743-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="4a743-108">Tipik kullanım gerçek bağımsız değişken değerlerini belirtmek için nesne öğelerini başlatma metinde kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4a743-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="4a743-109">Örnekler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4a743-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="4a743-110">Öğelerin sırasını büyük/küçük harf önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4a743-110">The order of the elements is significant.</span></span> <span data-ttu-id="4a743-111">XAML türleri sırayla, türlerinin eşleşmesi ve yedekleme Oluşturucusu veya Fabrika yöntemi aşırı yüklemesini sırasını yazın.</span><span class="sxs-lookup"><span data-stu-id="4a743-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="4a743-112">Tüm işlemelisiniz Üreteç yöntemi adını `x:Arguments` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="4a743-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="4a743-113">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="4a743-113">Dependencies</span></span>  
 <span data-ttu-id="4a743-114">`x:FactoryMethod` kapsam ve davranışını değiştirebilirsiniz burada `x:Arguments` uygular.</span><span class="sxs-lookup"><span data-stu-id="4a743-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="4a743-115">Hayır ise `x:FactoryMethod` belirtilen `x:Arguments` yedekleme oluşturucular alternatif (varsayılan olmayan) imzalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a743-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="4a743-116">Varsa `x:FactoryMethod` belirtilen `x:Arguments` adlandırılmış yöntemi aşırı yüklemesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a743-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a743-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a743-117">Remarks</span></span>  
 <span data-ttu-id="4a743-118">XAML 2006 başlatma metnin varsayılan olmayan başlatma destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="4a743-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="4a743-119">Ancak, bir başlatma metin oluşturma teknik uygulaması pratik sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="4a743-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="4a743-120">Başlatma metin tek metin dizesi olarak kabul edilir; Bu nedenle, bir tür dönüştürücüsü özel bilgi öğeleri ve özel sınırlayıcıları dizesinden ayrıştırabilen oluşturma davranışı için tanımlı olmadığı sürece yalnızca tek bir parametre başlatma özelliği ekler.</span><span class="sxs-lookup"><span data-stu-id="4a743-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="4a743-121">Ayrıca, nesne mantığı potansiyel olarak doğru bir dize dışında temelleri işlemek için bir verilen XAML ayrıştırıcı ait yerel varsayılan tür dönüştürücüsü metindir.</span><span class="sxs-lookup"><span data-stu-id="4a743-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="4a743-122">`x:Arguments` XAML kullanım değil özellik öğesi kullanımı tipik anlamında yönerge biçimlendirme içeren nesne öğe türünün başvurmadığından.</span><span class="sxs-lookup"><span data-stu-id="4a743-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="4a743-123">Gibi diğer yönergeleri yakındır daha fazla `x:Code` burada öğe demarks içine işaretleme yorumlanabilir alt içeriğini için varsayılan olarak dışındaki bir aralık.</span><span class="sxs-lookup"><span data-stu-id="4a743-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="4a743-124">Bu durumda, her nesne öğesi XAML türü XAML ayrıştırıcıları tarafından hangi belirli Oluşturucusu Fabrika yöntem imzası belirlemek için kullanılan bağımsız değişken türleri hakkında bilgi iletişim kuran bir `x:Arguments` kullanım başvurmak çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="4a743-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="4a743-125">`x:Arguments` bir nesne öğesi için yapılandırılan herhangi diğer özellik öğeleri, içerik, iç metni veya nesne öğesi başlatma dizeleri gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="4a743-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="4a743-126">Nesne öğeleri içinde `x:Arguments` öznitelikleri ve başlatma dizeleri, XAML türü ve yedekleme Oluşturucusu veya Fabrika yöntemi tarafından izin verildiğinde içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4a743-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="4a743-127">Nesne veya bağımsız değişkenleri için özel bir XAML türleri ya da aksi takdirde varsayılan XAML ad alanı dışında belirlenen önek eşletirmeleri başvurarak XAML türlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a743-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="4a743-128">XAML işlemci bağımsız değişkenlerin nasıl belirtilen belirlemek için aşağıdaki yönergeleri kullanın `x:Arguments` bir nesne oluşturmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a743-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="4a743-129">Varsa `x:FactoryMethod` belirtilirse, bilgi karşılaştırılır belirtilen `x:FactoryMethod` (unutmayın değerini `x:FactoryMethod` yöntem adı ve aşırı yüklemeleri adlandırılmış yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="4a743-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="4a743-130">Varsa `x:FactoryMethod` belirtilmezse, bilgi, nesnenin tüm ortak oluşturucu aşırı yüklemeleri kümesine karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="4a743-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="4a743-131">XAML işleme mantığı, parametrelerin sayısıyla karşılaştırır ve aşırı yükleme ile eşleşen kutup seçer.</span><span class="sxs-lookup"><span data-stu-id="4a743-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="4a743-132">Birden fazla eşleşme varsa, XAML işlemci sağlanan nesne öğeleri XAML türlerine bağlı parametre türleri karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a743-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="4a743-133">Yine de birden çok eşleşme varsa, XAML işlemci davranışı tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="4a743-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="4a743-134">Varsa bir `x:FactoryMethod` belirtildi ancak metodu nelze rozpoznat, XAML işlemci özel bir durum oluşturmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a743-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="4a743-135">XAML öznitelik kullanımı `<x:Arguments>string</x:Arguments>` teknik olarak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4a743-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="4a743-136">Ancak, bu ne aksi başlatma metin ve tür dönüştürücüleri yapılabilir dışında hiçbir özellikleri sağlar ve bu sözdizimi kullanarak XAML 2009 fabrika yöntemi özelliklerini tasarım amacınıza değil.</span><span class="sxs-lookup"><span data-stu-id="4a743-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4a743-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4a743-137">Examples</span></span>  
 <span data-ttu-id="4a743-138">Aşağıdaki örnek, varsayılan olmayan bir oluşturucu imzası ve XAML kullanımını gösterir `x:Arguments` , bu imza erişir.</span><span class="sxs-lookup"><span data-stu-id="4a743-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="4a743-139">Aşağıdaki örnek, bir hedef Fabrika yöntem imzası ve XAML kullanımını gösterir. `x:Arguments` , bu imza erişir.</span><span class="sxs-lookup"><span data-stu-id="4a743-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a743-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a743-140">See also</span></span>

- [<span data-ttu-id="4a743-141">.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="4a743-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="4a743-142">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="4a743-142">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)

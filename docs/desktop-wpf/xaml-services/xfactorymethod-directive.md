---
title: x:FactoryMethod Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071537"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="6c783-102">x:FactoryMethod Yönergesi</span><span class="sxs-lookup"><span data-stu-id="6c783-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="6c783-103">Bir XAML işlemcinin bir nesneyi destek türünü çözdükten sonra başlatmayı kullanmak için kullanması gereken bir oluşturucu dışında bir yöntem belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c783-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="6c783-104">XAML Öznitelik Kullanımı, x:Bağımsız Değişkenler yok</span><span class="sxs-lookup"><span data-stu-id="6c783-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="6c783-105">XAML Öznitelik Kullanımı, x:Element(ler) olarak bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="6c783-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="6c783-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="6c783-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="6c783-107">XAML işlemcilerinin çağırdığı bir yöntemin dize yöntemi adı, 'da `object`belirtilen örneği başlatmayı.</span><span class="sxs-lookup"><span data-stu-id="6c783-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="6c783-108">Bkz. Açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="6c783-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="6c783-109">Fabrika yöntemi parametrelerini belirten nesneler için bir veya daha fazla nesne öğesi.</span><span class="sxs-lookup"><span data-stu-id="6c783-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="6c783-110">Düzen önemlidir; bağımsız değişkenlerin fabrika yöntemine geçirilme sırasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c783-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c783-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c783-111">Remarks</span></span>  
 <span data-ttu-id="6c783-112">Örnek `methodname` bir yöntemse, nitelikli olamaz.</span><span class="sxs-lookup"><span data-stu-id="6c783-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="6c783-113">Fabrika yöntemleri olarak statik yöntemler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6c783-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="6c783-114">Statik `methodname` bir yöntem `methodname` ise, statik `typeName.methodName` fabrika `typeName` yöntemini tanımlayan sınıfı adlandırır bir kombinasyon olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6c783-114">If `methodname` is a static method, `methodname` is provided as a `typeName.methodName` combination, where `typeName` names the class that defines the static factory method.</span></span> <span data-ttu-id="6c783-115">`typeName`eşlenen xmlns bir tür atıfta varsa önek nitelikli olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c783-115">`typeName` can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="6c783-116">`typeName`daha farklı bir `typeof(object)`tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c783-116">`typeName` can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="6c783-117">Fabrika yöntemi, ilgili nesne öğeöğesini destekleyen türün genel olarak bildirilen bir yöntemi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c783-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="6c783-118">Fabrika yöntemi, ilgili nesneye atayabilen bir örneği döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="6c783-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="6c783-119">Fabrika yöntemleri asla null dönmelidir.</span><span class="sxs-lookup"><span data-stu-id="6c783-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="6c783-120">`x:Arguments`fabrika yöntemlerinin imzaları için en iyi maç prensibine göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="6c783-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="6c783-121">Eşleştirme önce parametre sayısını değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="6c783-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="6c783-122">Bir parametre sayısı için birden fazla olası eşleşme varsa, parametre türü değerlendirilir ve en iyi eşleşme belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6c783-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="6c783-123">Bu değerlendirme aşamasından sonra hala belirsizlik varsa, XAML işlemci davranışı tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="6c783-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="6c783-124">Yönerge biçimlendirmesi `x:FactoryMethod` içeren nesne öğe öğesinin türüne başvurmadığından, öğe kullanımı tipik anlamda özellik öğesi kullanımı değildir.</span><span class="sxs-lookup"><span data-stu-id="6c783-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="6c783-125">Öğe kullanımının öznitelik kullanımından daha az yaygın olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="6c783-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="6c783-126">`x:Arguments`(öznitelik veya eleman kullanımı) öğe `x:FactoryMethod` kullanımıyla birlikte kullanılabilir, ancak bu özellikle Kullanım bölümlerinde gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="6c783-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="6c783-127">`x:FactoryMethod`bir öğe diğer özellik öğeleri önce gerekir, `x:Arguments` herhangi bir da elements olarak sağlanan önce ve herhangi bir içerik / iç metin / başlatma metni önce olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c783-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c783-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c783-128">See also</span></span>

- [<span data-ttu-id="6c783-129">x:Arguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="6c783-129">x:Arguments Directive</span></span>](xarguments-directive.md)

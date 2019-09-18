---
title: x:FactoryMethod Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053783"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="47156-102">x:FactoryMethod Yönergesi</span><span class="sxs-lookup"><span data-stu-id="47156-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="47156-103">Bir XAML işlemcisinin, kendi destek türünü çözümledikten sonra bir nesneyi başlatmak için kullanması gereken bir Oluşturucu dışında bir yöntemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="47156-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="47156-104">XAML öznitelik kullanımı, x:Arguments yok</span><span class="sxs-lookup"><span data-stu-id="47156-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="47156-105">XAML öznitelik kullanımı, x:Arguments öğe (ler) olarak</span><span class="sxs-lookup"><span data-stu-id="47156-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="47156-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="47156-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="47156-107">XAML işlemcilerin, olarak `object`belirtilen örneği başlatmak için çağrı yapan yöntemin dize yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="47156-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="47156-108">Bkz. açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="47156-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="47156-109">Fabrika Yöntemi parametrelerini belirten nesneler için bir veya daha fazla nesne öğesi.</span><span class="sxs-lookup"><span data-stu-id="47156-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="47156-110">Sıra önemlidir; bağımsız değişkenlerin fabrika yöntemine geçirilmesi gereken sırayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="47156-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47156-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47156-111">Remarks</span></span>  
 <span data-ttu-id="47156-112">`methodname` Bir örnek yöntemi ise, nitelenemez.</span><span class="sxs-lookup"><span data-stu-id="47156-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="47156-113">Fabrika yöntemleri olarak statik yöntemler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="47156-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="47156-114">Statik bir yöntem ise, `methodname` typeName olarak sağlanır. `methodname`  *methodName* birleşimi, *TypeName* , statik fabrika yöntemini tanımlayan sınıfın adını belirler.</span><span class="sxs-lookup"><span data-stu-id="47156-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="47156-115">*TypeName* , eşlenmiş bir xmlns içindeki bir türe başvurulduğunda önek nitelenebilir.</span><span class="sxs-lookup"><span data-stu-id="47156-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="47156-116">*TypeName* , öğesinden `typeof(object)`farklı bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="47156-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="47156-117">Factory yöntemi, ilgili nesne öğesini yedekleyen türün tanımlanmış bir ortak yöntemi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47156-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="47156-118">Factory yöntemi, ilgili nesneye atanabilen bir örnek döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="47156-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="47156-119">Fabrika yöntemleri asla null döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="47156-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="47156-120">`x:Arguments`Fabrika yöntemlerinin imzaları için en iyi eşleşme ilkesi üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="47156-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="47156-121">Eşleşen parametre sayısını önce değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="47156-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="47156-122">Bir parametre sayısı için birden fazla olası eşleşme varsa, parametre türü değerlendirilir ve en iyi eşleşme belirlenir.</span><span class="sxs-lookup"><span data-stu-id="47156-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="47156-123">Bu değerlendirme aşamasından sonra hala belirsizlik varsa XAML işlemci davranışı tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="47156-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="47156-124">Yönerge biçimlendirmesi kapsayan nesne öğesinin türüne başvurmadığından, öğekullanımıtipikanlamdaÖzelliköğesikullanımıdeğildir.`x:FactoryMethod`</span><span class="sxs-lookup"><span data-stu-id="47156-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="47156-125">Öğe kullanımının öznitelik kullanımından daha az yaygın olması beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="47156-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="47156-126">`x:Arguments`(öznitelik veya öğe kullanımı) öğe kullanımı ile `x:FactoryMethod` birlikte kullanılabilir, ancak bu özellikle kullanım bölümlerinde gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="47156-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="47156-127">`x:FactoryMethod`bir öğe, diğer tüm özellik öğelerinden önce gelmeli, `x:Arguments` öğeler olarak sağlanmasının ve tüm içerik/iç metin/başlatma metininin önüne gelmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="47156-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47156-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47156-128">See also</span></span>

- [<span data-ttu-id="47156-129">x:Arguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="47156-129">x:Arguments Directive</span></span>](x-arguments-directive.md)

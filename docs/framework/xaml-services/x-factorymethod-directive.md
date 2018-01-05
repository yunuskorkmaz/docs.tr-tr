---
title: "x:FactoryMethod Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58349c5440d0062c64346933e48b64de6c4c7b60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="c43da-102">x:FactoryMethod Yönergesi</span><span class="sxs-lookup"><span data-stu-id="c43da-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="c43da-103">XAML işlemci yedekleme türünü düzelttikten sonra bir nesneyi başlatmak için kullanması gereken bir oluşturucu dışında bir yöntem belirtir.</span><span class="sxs-lookup"><span data-stu-id="c43da-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="c43da-104">XAML öznitelik kullanımı, hiçbir x: Arguments</span><span class="sxs-lookup"><span data-stu-id="c43da-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="c43da-105">XAML öznitelik kullanımı, x: Arguments öğe olarak</span><span class="sxs-lookup"><span data-stu-id="c43da-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c43da-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="c43da-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="c43da-107">Olarak belirtilen örneği başlatmak için XAML işlemcileri çağıran bir yöntem dize yöntemi adını `object`.</span><span class="sxs-lookup"><span data-stu-id="c43da-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="c43da-108">Açıklamalar bakın.</span><span class="sxs-lookup"><span data-stu-id="c43da-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="c43da-109">Fabrika yöntemi parametrelerini belirtin nesneleri için bir veya daha fazla nesne öğeleri.</span><span class="sxs-lookup"><span data-stu-id="c43da-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="c43da-110">Sırası önemlidir; bağımsız değişkenler için Üreteç yöntemi iletilmesi gereken sırayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c43da-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c43da-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c43da-111">Remarks</span></span>  
 <span data-ttu-id="c43da-112">Varsa `methodname` bir örnek yöntemidir tam olamaz.</span><span class="sxs-lookup"><span data-stu-id="c43da-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="c43da-113">Statik yöntemler fabrika yöntemi olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c43da-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="c43da-114">Varsa `methodname` bir statik yöntem `methodname` olarak sağlanan bir *typeName*. *methodName* birleşimi, burada *typeName* statik Üreteç yöntemi tanımlayan sınıf adları.</span><span class="sxs-lookup"><span data-stu-id="c43da-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="c43da-115">*typeName* öneki nitelenmiş eşlenen xmlns içinde türüne başvuran durumunda olabilir.</span><span class="sxs-lookup"><span data-stu-id="c43da-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="c43da-116">*typeName* farklı bir type olabilir `typeof(``object``)`.</span><span class="sxs-lookup"><span data-stu-id="c43da-116">*typeName* can be a different type than `typeof(``object``)`.</span></span>  
  
 <span data-ttu-id="c43da-117">Üreteç yöntemi ilgili nesne öğesi yedekler türünde bildirilen bir genel yöntem olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c43da-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="c43da-118">Üreteç yöntemi ilgili nesnesine atanamaz örneğini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="c43da-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="c43da-119">Fabrika yöntemleri hiçbir zaman null değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="c43da-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="c43da-120">`x:Arguments`Fabrika yöntemleri, imzaları için en iyi eşleşmeyi prensibi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c43da-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="c43da-121">Eşleşen parametre sayısı önce değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c43da-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="c43da-122">Parametre sayısı için birden fazla olası eşleşme varsa, değerlendirilen ve en iyi eşleşme belirlenir sonra parametre türü değil.</span><span class="sxs-lookup"><span data-stu-id="c43da-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="c43da-123">XAML işlemci davranış hala belirsizlik varsa bu Değerlendirme Aşaması sonra tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c43da-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="c43da-124">`x:FactoryMethod` Öğesi kullanımı tipik herkese açık özellik öğesi kullanımı yönerge biçimlendirme içeren nesne öğenin türü başvurmuyor olmadığından değil.</span><span class="sxs-lookup"><span data-stu-id="c43da-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="c43da-125">Beklenen bu öğe kullanım öznitelik kullanımı daha az yaygındır.</span><span class="sxs-lookup"><span data-stu-id="c43da-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="c43da-126">`x:Arguments`(öznitelik veya öğe kullanım) ile birlikte kullanılabilir `x:FactoryMethod` öğesi kullanımı, ancak bu özellikle gösterilmez kullanım bölümlerde.</span><span class="sxs-lookup"><span data-stu-id="c43da-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="c43da-127">`x:FactoryMethod`herhangi bir öğe başka bir özellik öğelerinin gelmelidir gibi gelmelidir `x:Arguments` ayrıca öğeleri olarak sağlanan ve herhangi bir içeriği/iç metin/başlatma metin gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="c43da-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c43da-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c43da-128">See Also</span></span>  
 [<span data-ttu-id="c43da-129">x:Arguments Yönergesi</span><span class="sxs-lookup"><span data-stu-id="c43da-129">x:Arguments Directive</span></span>](../../../docs/framework/xaml-services/x-arguments-directive.md)

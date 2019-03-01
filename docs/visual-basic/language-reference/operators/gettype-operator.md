---
title: GetType İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: e3b4ee9a1bfcc2132d3e9e1239ff2c8f7158e513
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966773"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="52b0f-102">GetType İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52b0f-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="52b0f-103">Döndürür bir <xref:System.Type> belirtilen türde bir nesne.</span><span class="sxs-lookup"><span data-stu-id="52b0f-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="52b0f-104"><xref:System.Type> Nesne türü özellikleri, yöntemleri ve olayları gibi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="52b0f-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b0f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52b0f-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52b0f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52b0f-106">Parameters</span></span>  
  
|<span data-ttu-id="52b0f-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="52b0f-107">Parameter</span></span>|<span data-ttu-id="52b0f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52b0f-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="52b0f-109">Bilgi bağlamasına türünün adı.</span><span class="sxs-lookup"><span data-stu-id="52b0f-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52b0f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52b0f-110">Remarks</span></span>  
 <span data-ttu-id="52b0f-111">`GetType` İşleci döndürür <xref:System.Type> nesne için belirtilen `typename`.</span><span class="sxs-lookup"><span data-stu-id="52b0f-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="52b0f-112">İçinde tanımlanan bir tür adını geçirebilirsiniz `typename`.</span><span class="sxs-lookup"><span data-stu-id="52b0f-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="52b0f-113">Bu, aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="52b0f-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="52b0f-114">Herhangi bir Visual Basic veri türü, gibi `Boolean` veya `Date`.</span><span class="sxs-lookup"><span data-stu-id="52b0f-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="52b0f-115">Herhangi .NET Framework sınıf, yapı, modül veya arabirimi gibi <xref:System.ArgumentException?displayProperty=nameWithType> veya <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="52b0f-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="52b0f-116">Herhangi sınıf, yapı, modül veya uygulamanız tarafından tanımlanan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="52b0f-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="52b0f-117">Uygulamanız tarafından tanımlanan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="52b0f-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="52b0f-118">Uygulamanız tarafından tanımlanan herhangi bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="52b0f-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="52b0f-119">Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="52b0f-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="52b0f-120">Bir nesne değişkeninin türdeki nesneyi almak istiyorsanız, kullanmanız <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52b0f-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="52b0f-121">`GetType` İşleci aşağıdaki durumlarda kullanışlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="52b0f-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="52b0f-122">Çalışma zamanında bir türü için meta veriler erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="52b0f-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="52b0f-123"><xref:System.Type> Nesnesi, tür üyeleri ve dağıtım bilgileri gibi meta veriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="52b0f-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="52b0f-124">Bu, örneğin, bir derleme üzerinden yansıtacak şekilde ihtiyacınız var.</span><span class="sxs-lookup"><span data-stu-id="52b0f-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="52b0f-125">Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="52b0f-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="52b0f-126">Bunlar aynı tür örneklerine başvuruyorsa görmek için iki nesne başvuru karşılaştırmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="52b0f-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="52b0f-127">Eğer öyleyse `GetType` aynı başvuruları döndürür <xref:System.Type> nesne.</span><span class="sxs-lookup"><span data-stu-id="52b0f-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52b0f-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="52b0f-128">Example</span></span>  
 <span data-ttu-id="52b0f-129">Aşağıdaki örneklerde gösterildiği `GetType` işleci kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="52b0f-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="52b0f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52b0f-130">See also</span></span>
- [<span data-ttu-id="52b0f-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="52b0f-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="52b0f-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="52b0f-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="52b0f-133">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="52b0f-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

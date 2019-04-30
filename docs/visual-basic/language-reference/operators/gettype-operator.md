---
title: GetType İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 34ab192814583db5cdc0d0183c73cc22b8633e9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663615"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="58d22-102">GetType İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58d22-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="58d22-103">Döndürür bir <xref:System.Type> belirtilen türde bir nesne.</span><span class="sxs-lookup"><span data-stu-id="58d22-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="58d22-104"><xref:System.Type> Nesne türü özellikleri, yöntemleri ve olayları gibi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="58d22-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58d22-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58d22-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="58d22-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58d22-106">Parameters</span></span>  
  
|<span data-ttu-id="58d22-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="58d22-107">Parameter</span></span>|<span data-ttu-id="58d22-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58d22-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="58d22-109">Bilgi bağlamasına türünün adı.</span><span class="sxs-lookup"><span data-stu-id="58d22-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58d22-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58d22-110">Remarks</span></span>  
 <span data-ttu-id="58d22-111">`GetType` İşleci döndürür <xref:System.Type> nesne için belirtilen `typename`.</span><span class="sxs-lookup"><span data-stu-id="58d22-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="58d22-112">İçinde tanımlanan bir tür adını geçirebilirsiniz `typename`.</span><span class="sxs-lookup"><span data-stu-id="58d22-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="58d22-113">Bu, aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="58d22-113">This includes the following:</span></span>  
  
- <span data-ttu-id="58d22-114">Herhangi bir Visual Basic veri türü, gibi `Boolean` veya `Date`.</span><span class="sxs-lookup"><span data-stu-id="58d22-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="58d22-115">Herhangi .NET Framework sınıf, yapı, modül veya arabirimi gibi <xref:System.ArgumentException?displayProperty=nameWithType> veya <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58d22-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="58d22-116">Herhangi sınıf, yapı, modül veya uygulamanız tarafından tanımlanan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="58d22-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="58d22-117">Uygulamanız tarafından tanımlanan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="58d22-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="58d22-118">Uygulamanız tarafından tanımlanan herhangi bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="58d22-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="58d22-119">Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="58d22-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="58d22-120">Bir nesne değişkeninin türdeki nesneyi almak istiyorsanız, kullanmanız <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58d22-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="58d22-121">`GetType` İşleci aşağıdaki durumlarda kullanışlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="58d22-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="58d22-122">Çalışma zamanında bir türü için meta veriler erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="58d22-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="58d22-123"><xref:System.Type> Nesnesi, tür üyeleri ve dağıtım bilgileri gibi meta veriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="58d22-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="58d22-124">Bu, örneğin, bir derleme üzerinden yansıtacak şekilde ihtiyacınız var.</span><span class="sxs-lookup"><span data-stu-id="58d22-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="58d22-125">Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58d22-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="58d22-126">Bunlar aynı tür örneklerine başvuruyorsa görmek için iki nesne başvuru karşılaştırmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="58d22-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="58d22-127">Eğer öyleyse `GetType` aynı başvuruları döndürür <xref:System.Type> nesne.</span><span class="sxs-lookup"><span data-stu-id="58d22-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58d22-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="58d22-128">Example</span></span>  
 <span data-ttu-id="58d22-129">Aşağıdaki örneklerde gösterildiği `GetType` işleci kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="58d22-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="58d22-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58d22-130">See also</span></span>

- [<span data-ttu-id="58d22-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="58d22-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="58d22-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="58d22-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="58d22-133">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="58d22-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

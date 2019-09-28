---
title: GetType İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592146"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="c86f6-102">GetType İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c86f6-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="c86f6-103">Belirtilen tür için bir <xref:System.Type> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="c86f6-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="c86f6-104">@No__t-0 nesnesi, bu tür hakkında özellikler, Yöntemler ve olaylar gibi bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c86f6-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c86f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c86f6-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="c86f6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c86f6-106">Parameters</span></span>  
  
|<span data-ttu-id="c86f6-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="c86f6-107">Parameter</span></span>|<span data-ttu-id="c86f6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c86f6-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="c86f6-109">Bilgilerini istediğiniz türün adı.</span><span class="sxs-lookup"><span data-stu-id="c86f6-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c86f6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c86f6-110">Remarks</span></span>  
 <span data-ttu-id="c86f6-111">@No__t-0 işleci, belirtilen `typename` için <xref:System.Type> nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c86f6-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="c86f6-112">@No__t-0 ' da tanımlı herhangi bir türün adını geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c86f6-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="c86f6-113">Bu, aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="c86f6-113">This includes the following:</span></span>  
  
- <span data-ttu-id="c86f6-114">@No__t-0 veya `Date` gibi Visual Basic veri türleri.</span><span class="sxs-lookup"><span data-stu-id="c86f6-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="c86f6-115">@No__t-0 veya <xref:System.Double?displayProperty=nameWithType> gibi .NET Framework sınıf, yapı, modül veya arabirim.</span><span class="sxs-lookup"><span data-stu-id="c86f6-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="c86f6-116">Uygulamanız tarafından tanımlanan herhangi bir sınıf, yapı, modül veya arabirim.</span><span class="sxs-lookup"><span data-stu-id="c86f6-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="c86f6-117">Uygulamanız tarafından tanımlanan herhangi bir dizi.</span><span class="sxs-lookup"><span data-stu-id="c86f6-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="c86f6-118">Uygulamanız tarafından tanımlanan tüm temsilciler.</span><span class="sxs-lookup"><span data-stu-id="c86f6-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="c86f6-119">Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c86f6-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="c86f6-120">Bir nesne değişkeninin tür nesnesini almak istiyorsanız <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c86f6-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="c86f6-121">@No__t-0 işleci aşağıdaki koşullarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="c86f6-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="c86f6-122">Çalışma zamanında bir türün meta verilerine erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c86f6-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="c86f6-123">@No__t-0 nesnesi, tür üyeleri ve dağıtım bilgileri gibi meta verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c86f6-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="c86f6-124">Örneğin, bir derlemeyi yansıtmak için bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c86f6-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="c86f6-125">Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c86f6-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="c86f6-126">Aynı türdeki örneklere başvurduklarında, iki nesne başvurularını karşılaştırmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c86f6-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="c86f6-127">@No__t-0, aynı <xref:System.Type> nesnesine başvuruları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c86f6-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c86f6-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="c86f6-128">Example</span></span>  
 <span data-ttu-id="c86f6-129">Aşağıdaki örneklerde `GetType` işleci kullanımda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c86f6-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="c86f6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c86f6-130">See also</span></span>

- [<span data-ttu-id="c86f6-131">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="c86f6-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="c86f6-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="c86f6-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="c86f6-133">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="c86f6-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

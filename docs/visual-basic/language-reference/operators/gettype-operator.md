---
description: 'Daha fazla bilgi edinin: GetType Işleci (Visual Basic)'
title: GetType İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 15fe9c28997aa01527f23c0cc8fdbb0fe6cc53f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665997"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="21c23-103">GetType İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21c23-103">GetType Operator (Visual Basic)</span></span>

<span data-ttu-id="21c23-104"><xref:System.Type>Belirtilen tür için bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="21c23-104">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="21c23-105"><xref:System.Type>Nesnesi, bu tür hakkında özellikler, Yöntemler ve olaylar gibi bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="21c23-105">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c23-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21c23-106">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="21c23-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21c23-107">Parameters</span></span>  
  
|<span data-ttu-id="21c23-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="21c23-108">Parameter</span></span>|<span data-ttu-id="21c23-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21c23-109">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="21c23-110">Bilgilerini istediğiniz türün adı.</span><span class="sxs-lookup"><span data-stu-id="21c23-110">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21c23-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21c23-111">Remarks</span></span>  

 <span data-ttu-id="21c23-112">`GetType`İşleci, <xref:System.Type> belirtilen için nesnesini döndürür `typename` .</span><span class="sxs-lookup"><span data-stu-id="21c23-112">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="21c23-113">' De tanımlı herhangi bir türün adını geçirebilirsiniz `typename` .</span><span class="sxs-lookup"><span data-stu-id="21c23-113">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="21c23-114">Bu, aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="21c23-114">This includes the following:</span></span>  
  
- <span data-ttu-id="21c23-115">Ya da gibi Visual Basic veri türü `Boolean` `Date` .</span><span class="sxs-lookup"><span data-stu-id="21c23-115">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="21c23-116">Ya da gibi .NET Framework sınıf, yapı, modül veya arabirim <xref:System.ArgumentException?displayProperty=nameWithType> <xref:System.Double?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="21c23-116">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="21c23-117">Uygulamanız tarafından tanımlanan herhangi bir sınıf, yapı, modül veya arabirim.</span><span class="sxs-lookup"><span data-stu-id="21c23-117">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="21c23-118">Uygulamanız tarafından tanımlanan herhangi bir dizi.</span><span class="sxs-lookup"><span data-stu-id="21c23-118">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="21c23-119">Uygulamanız tarafından tanımlanan tüm temsilciler.</span><span class="sxs-lookup"><span data-stu-id="21c23-119">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="21c23-120">Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="21c23-120">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="21c23-121">Bir nesne değişkeninin Type nesnesini almak istiyorsanız <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="21c23-121">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="21c23-122">`GetType`İşleci aşağıdaki koşullarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="21c23-122">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="21c23-123">Çalışma zamanında bir türün meta verilerine erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21c23-123">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="21c23-124"><xref:System.Type>Nesnesi, tür üyeleri ve dağıtım bilgileri gibi meta verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="21c23-124">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="21c23-125">Örneğin, bir derlemeyi yansıtmak için bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21c23-125">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="21c23-126">Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21c23-126">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="21c23-127">Aynı türdeki örneklere başvurduklarında, iki nesne başvurularını karşılaştırmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="21c23-127">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="21c23-128">Varsa, `GetType` aynı nesneye başvuruları döndürür <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="21c23-128">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21c23-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="21c23-129">Example</span></span>  

 <span data-ttu-id="21c23-130">Aşağıdaki örneklerde `GetType` kullanılan operatör gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="21c23-130">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="21c23-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21c23-131">See also</span></span>

- [<span data-ttu-id="21c23-132">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="21c23-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="21c23-133">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="21c23-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="21c23-134">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="21c23-134">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)

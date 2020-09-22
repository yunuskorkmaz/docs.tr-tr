---
title: GetType İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 9ff207ea4f2b89ea30eb8f46a3e640ccf3789974
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867008"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="642ec-102">GetType İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="642ec-102">GetType Operator (Visual Basic)</span></span>

<span data-ttu-id="642ec-103"><xref:System.Type>Belirtilen tür için bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="642ec-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="642ec-104"><xref:System.Type>Nesnesi, bu tür hakkında özellikler, Yöntemler ve olaylar gibi bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="642ec-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="642ec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="642ec-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="642ec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="642ec-106">Parameters</span></span>  
  
|<span data-ttu-id="642ec-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="642ec-107">Parameter</span></span>|<span data-ttu-id="642ec-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="642ec-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="642ec-109">Bilgilerini istediğiniz türün adı.</span><span class="sxs-lookup"><span data-stu-id="642ec-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="642ec-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="642ec-110">Remarks</span></span>  

 <span data-ttu-id="642ec-111">`GetType`İşleci, <xref:System.Type> belirtilen için nesnesini döndürür `typename` .</span><span class="sxs-lookup"><span data-stu-id="642ec-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="642ec-112">' De tanımlı herhangi bir türün adını geçirebilirsiniz `typename` .</span><span class="sxs-lookup"><span data-stu-id="642ec-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="642ec-113">Bu, aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="642ec-113">This includes the following:</span></span>  
  
- <span data-ttu-id="642ec-114">Ya da gibi Visual Basic veri türü `Boolean` `Date` .</span><span class="sxs-lookup"><span data-stu-id="642ec-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="642ec-115">Ya da gibi .NET Framework sınıf, yapı, modül veya arabirim <xref:System.ArgumentException?displayProperty=nameWithType> <xref:System.Double?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="642ec-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="642ec-116">Uygulamanız tarafından tanımlanan herhangi bir sınıf, yapı, modül veya arabirim.</span><span class="sxs-lookup"><span data-stu-id="642ec-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="642ec-117">Uygulamanız tarafından tanımlanan herhangi bir dizi.</span><span class="sxs-lookup"><span data-stu-id="642ec-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="642ec-118">Uygulamanız tarafından tanımlanan tüm temsilciler.</span><span class="sxs-lookup"><span data-stu-id="642ec-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="642ec-119">Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="642ec-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="642ec-120">Bir nesne değişkeninin Type nesnesini almak istiyorsanız <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="642ec-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="642ec-121">`GetType`İşleci aşağıdaki koşullarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="642ec-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="642ec-122">Çalışma zamanında bir türün meta verilerine erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="642ec-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="642ec-123"><xref:System.Type>Nesnesi, tür üyeleri ve dağıtım bilgileri gibi meta verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="642ec-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="642ec-124">Örneğin, bir derlemeyi yansıtmak için bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="642ec-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="642ec-125">Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="642ec-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="642ec-126">Aynı türdeki örneklere başvurduklarında, iki nesne başvurularını karşılaştırmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="642ec-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="642ec-127">Varsa, `GetType` aynı nesneye başvuruları döndürür <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="642ec-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="642ec-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="642ec-128">Example</span></span>  

 <span data-ttu-id="642ec-129">Aşağıdaki örneklerde `GetType` kullanılan operatör gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="642ec-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="642ec-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="642ec-130">See also</span></span>

- [<span data-ttu-id="642ec-131">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="642ec-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="642ec-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="642ec-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="642ec-133">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="642ec-133">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)

---
title: GetType İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 4e59bcfaa24c9545ed75c6b5c1d29cad398ac2de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349545"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="f9bd1-102">GetType İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9bd1-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="f9bd1-103">Returns a <xref:System.Type> object for the specified type.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="f9bd1-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9bd1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9bd1-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9bd1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9bd1-106">Parameters</span></span>  
  
|<span data-ttu-id="f9bd1-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="f9bd1-107">Parameter</span></span>|<span data-ttu-id="f9bd1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9bd1-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="f9bd1-109">The name of the type for which you desire information.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9bd1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9bd1-110">Remarks</span></span>  
 <span data-ttu-id="f9bd1-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="f9bd1-112">You can pass the name of any defined type in `typename`.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="f9bd1-113">Bu, aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="f9bd1-113">This includes the following:</span></span>  
  
- <span data-ttu-id="f9bd1-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="f9bd1-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f9bd1-116">Any class, structure, module, or interface defined by your application.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="f9bd1-117">Any array defined by your application.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="f9bd1-118">Any delegate defined by your application.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="f9bd1-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="f9bd1-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f9bd1-121">The `GetType` operator can be useful in the following circumstances:</span><span class="sxs-lookup"><span data-stu-id="f9bd1-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="f9bd1-122">You must access the metadata for a type at run time.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="f9bd1-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="f9bd1-124">You need this, for example, to reflect over an assembly.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="f9bd1-125">Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f9bd1-126">You want to compare two object references to see if they refer to instances of the same type.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="f9bd1-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9bd1-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9bd1-128">Example</span></span>  
 <span data-ttu-id="f9bd1-129">The following examples show the `GetType` operator in use.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="f9bd1-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9bd1-130">See also</span></span>

- [<span data-ttu-id="f9bd1-131">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9bd1-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f9bd1-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="f9bd1-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f9bd1-133">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="f9bd1-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

---
title: "GetType İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="3f2f0-102">GetType İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f2f0-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="3f2f0-103">Döndürür bir <xref:System.Type> nesne belirtilen türe.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="3f2f0-104"><xref:System.Type> Nesne türü özellikleri, yöntemleri ve olayları gibi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f2f0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f2f0-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f2f0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f2f0-106">Parameters</span></span>  
  
|<span data-ttu-id="3f2f0-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="3f2f0-107">Parameter</span></span>|<span data-ttu-id="3f2f0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f2f0-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="3f2f0-109">Bilgi işlemleriniz türünün adı.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f2f0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f2f0-110">Remarks</span></span>  
 <span data-ttu-id="3f2f0-111">`GetType` Operatörü döndürür <xref:System.Type> için belirtilen nesne `typename`.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="3f2f0-112">İçinde tanımlanan tüm türünün adı geçirebilirsiniz `typename`.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="3f2f0-113">Buna aşağıdakiler dahildir:</span><span class="sxs-lookup"><span data-stu-id="3f2f0-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="3f2f0-114">Herhangi bir Visual Basic veri türü, gibi `Boolean` veya `Date`.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="3f2f0-115">Tüm .NET Framework sınıf, yapısı, modül veya arabirimi, aşağıdaki gibi <xref:System.ArgumentException?displayProperty=nameWithType> veya <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="3f2f0-116">Tüm sınıfı, yapısı, modül veya uygulamanız tarafından tanımlanan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="3f2f0-117">Uygulamanız tarafından tanımlanan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="3f2f0-118">Uygulamanız tarafından tanımlanan herhangi bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="3f2f0-119">Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="3f2f0-120">Bir nesne değişkeninin türü nesnesinin almak istiyorsanız, kullanmak <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="3f2f0-121">`GetType` İşleci aşağıdaki durumlarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="3f2f0-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="3f2f0-122">Çalışma zamanında bir türü için meta veriler erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="3f2f0-123"><xref:System.Type> Nesne türü üyeleri ve dağıtım bilgileri gibi meta veriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="3f2f0-124">Bu, örneğin, bir derlemeyi yansıtacak şekilde ihtiyacınız var.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="3f2f0-125">Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="3f2f0-126">Aynı türde örneklerine başvurursanız görmek için iki nesne başvuruları karşılaştırmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="3f2f0-127">İçermiyorlarsa `GetType` aynı başvurular döndürür <xref:System.Type> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f2f0-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f2f0-128">Example</span></span>  
 <span data-ttu-id="3f2f0-129">Aşağıdaki örneklerde gösterildiği `GetType` işleci kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3f2f0-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f2f0-130">See Also</span></span>  
 [<span data-ttu-id="3f2f0-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="3f2f0-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="3f2f0-132">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="3f2f0-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="3f2f0-133">İşleçler ve ifadeler</span><span class="sxs-lookup"><span data-stu-id="3f2f0-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

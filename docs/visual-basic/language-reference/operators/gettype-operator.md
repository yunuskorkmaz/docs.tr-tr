---
title: GetType İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 581f576222eb149aede841a5da7a0e5f38c77b58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603853"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="6896d-102">GetType İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6896d-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="6896d-103">Döndürür bir <xref:System.Type> nesne belirtilen türe.</span><span class="sxs-lookup"><span data-stu-id="6896d-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="6896d-104"><xref:System.Type> Nesne türü özellikleri, yöntemleri ve olayları gibi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6896d-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6896d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6896d-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6896d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6896d-106">Parameters</span></span>  
  
|<span data-ttu-id="6896d-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="6896d-107">Parameter</span></span>|<span data-ttu-id="6896d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6896d-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="6896d-109">Bilgi işlemleriniz türünün adı.</span><span class="sxs-lookup"><span data-stu-id="6896d-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6896d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6896d-110">Remarks</span></span>  
 <span data-ttu-id="6896d-111">`GetType` Operatörü döndürür <xref:System.Type> için belirtilen nesne `typename`.</span><span class="sxs-lookup"><span data-stu-id="6896d-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="6896d-112">İçinde tanımlanan tüm türünün adı geçirebilirsiniz `typename`.</span><span class="sxs-lookup"><span data-stu-id="6896d-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="6896d-113">Buna aşağıdakiler dahildir:</span><span class="sxs-lookup"><span data-stu-id="6896d-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="6896d-114">Herhangi bir Visual Basic veri türü, gibi `Boolean` veya `Date`.</span><span class="sxs-lookup"><span data-stu-id="6896d-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="6896d-115">Tüm .NET Framework sınıf, yapısı, modül veya arabirimi, aşağıdaki gibi <xref:System.ArgumentException?displayProperty=nameWithType> veya <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6896d-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="6896d-116">Tüm sınıfı, yapısı, modül veya uygulamanız tarafından tanımlanan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6896d-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="6896d-117">Uygulamanız tarafından tanımlanan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="6896d-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="6896d-118">Uygulamanız tarafından tanımlanan herhangi bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="6896d-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="6896d-119">Visual Basic, .NET Framework veya uygulamanız tarafından tanımlanan tüm numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="6896d-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="6896d-120">Bir nesne değişkeninin türü nesnesinin almak istiyorsanız, kullanmak <xref:System.Type.GetType%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6896d-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6896d-121">`GetType` İşleci aşağıdaki durumlarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="6896d-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="6896d-122">Çalışma zamanında bir türü için meta veriler erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6896d-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="6896d-123"><xref:System.Type> Nesne türü üyeleri ve dağıtım bilgileri gibi meta veriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6896d-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="6896d-124">Bu, örneğin, bir derlemeyi yansıtacak şekilde ihtiyacınız var.</span><span class="sxs-lookup"><span data-stu-id="6896d-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="6896d-125">Daha fazla bilgi için bkz. <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6896d-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="6896d-126">Aynı türde örneklerine başvurursanız görmek için iki nesne başvuruları karşılaştırmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="6896d-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="6896d-127">İçermiyorlarsa `GetType` aynı başvurular döndürür <xref:System.Type> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6896d-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6896d-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="6896d-128">Example</span></span>  
 <span data-ttu-id="6896d-129">Aşağıdaki örneklerde gösterildiği `GetType` işleci kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="6896d-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6896d-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6896d-130">See Also</span></span>  
 [<span data-ttu-id="6896d-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="6896d-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="6896d-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="6896d-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="6896d-133">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="6896d-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

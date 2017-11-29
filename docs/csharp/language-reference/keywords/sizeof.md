---
title: "sizeof (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords: sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0148ae8381804ca9286315251582c8ab40778369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="3e986-102">sizeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3e986-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="3e986-103">Yönetilmeyen bir tür için bayt cinsinden boyutu almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e986-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="3e986-104">Yönetilmeyen türleri, aşağıdaki tabloda, aşağıdaki yanı sıra listelenen yerleşik türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3e986-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="3e986-105">Numaralandırma türleri</span><span class="sxs-lookup"><span data-stu-id="3e986-105">Enum types</span></span>  
  
-   <span data-ttu-id="3e986-106">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="3e986-106">Pointer types</span></span>  
  
-   <span data-ttu-id="3e986-107">Herhangi bir alan veya başvuru türleri olan özellikler içermeyen kullanıcı tanımlı yapılar</span><span class="sxs-lookup"><span data-stu-id="3e986-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="3e986-108">Aşağıdaki örnek boyutunu almak nasıl gösterir bir `int`:</span><span class="sxs-lookup"><span data-stu-id="3e986-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="3e986-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e986-109">Remarks</span></span>  
 <span data-ttu-id="3e986-110">C# 2.0 sürümünden başlayarak, uygulama `sizeof` için yerleşik türler artık gerektiren [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) modu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e986-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="3e986-111">`sizeof` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e986-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="3e986-112">Tarafından döndürülen değer `sizeof` işleci türündedir `int`.</span><span class="sxs-lookup"><span data-stu-id="3e986-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="3e986-113">İçin yerine sabit değerleri aşağıdaki tabloda gösterilmektedir `sizeof` işlenen olarak yerleşik belirli türlerine sahip bir ifade.</span><span class="sxs-lookup"><span data-stu-id="3e986-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="3e986-114">İfade</span><span class="sxs-lookup"><span data-stu-id="3e986-114">Expression</span></span>|<span data-ttu-id="3e986-115">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="3e986-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="3e986-116">1.</span><span class="sxs-lookup"><span data-stu-id="3e986-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="3e986-117">1.</span><span class="sxs-lookup"><span data-stu-id="3e986-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="3e986-118">2</span><span class="sxs-lookup"><span data-stu-id="3e986-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="3e986-119">2</span><span class="sxs-lookup"><span data-stu-id="3e986-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="3e986-120">4</span><span class="sxs-lookup"><span data-stu-id="3e986-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="3e986-121">4</span><span class="sxs-lookup"><span data-stu-id="3e986-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="3e986-122">8</span><span class="sxs-lookup"><span data-stu-id="3e986-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="3e986-123">8</span><span class="sxs-lookup"><span data-stu-id="3e986-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="3e986-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="3e986-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="3e986-125">4</span><span class="sxs-lookup"><span data-stu-id="3e986-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="3e986-126">8</span><span class="sxs-lookup"><span data-stu-id="3e986-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="3e986-127">16</span><span class="sxs-lookup"><span data-stu-id="3e986-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="3e986-128">1.</span><span class="sxs-lookup"><span data-stu-id="3e986-128">1</span></span>|  
  
 <span data-ttu-id="3e986-129">Yapılar, diğer tüm türler için dahil olmak üzere `sizeof` işleci yalnızca güvenli olmayan kod blokları içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e986-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="3e986-130">Kullanabilirsiniz ancak <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemi, bu yöntem tarafından döndürülen değeri değil her zaman tarafından döndürülen değer ile aynı `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="3e986-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="3e986-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>türü sıralanmış sonra ancak boyutunu döndüren `sizeof` herhangi bir doldurmaya dahil olmak üzere ortak dil çalışma zamanı tarafından ayrılmış olarak boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e986-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e986-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e986-132">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3e986-133">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3e986-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3e986-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e986-134">See Also</span></span>  
 [<span data-ttu-id="3e986-135">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3e986-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3e986-136">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3e986-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3e986-137">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3e986-137">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3e986-138">İşleç anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3e986-138">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="3e986-139">Enum</span><span class="sxs-lookup"><span data-stu-id="3e986-139">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
 [<span data-ttu-id="3e986-140">Güvenli olmayan kod ve işaretçiler</span><span class="sxs-lookup"><span data-stu-id="3e986-140">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="3e986-141">Yapılar</span><span class="sxs-lookup"><span data-stu-id="3e986-141">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="3e986-142">Sabitleri</span><span class="sxs-lookup"><span data-stu-id="3e986-142">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

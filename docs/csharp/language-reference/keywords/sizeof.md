---
title: sizeof (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: f2507dd8528e2e66016524873ada890227a74ed8
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258446"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="a1492-102">sizeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a1492-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="a1492-103">Yönetilmeyen bir tür için bayt cinsinden boyutunu almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1492-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="a1492-104">Yönetilmeyen türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a1492-104">Unmanaged types include:</span></span>

-   <span data-ttu-id="a1492-105">Aşağıdaki tabloda listelenen basit türler:</span><span class="sxs-lookup"><span data-stu-id="a1492-105">The simple types that are listed in the following table:</span></span>
  
   |<span data-ttu-id="a1492-106">İfade</span><span class="sxs-lookup"><span data-stu-id="a1492-106">Expression</span></span>|<span data-ttu-id="a1492-107">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="a1492-107">Constant value</span></span>|  
   |----------------|--------------------|  
   |`sizeof(sbyte)`|<span data-ttu-id="a1492-108">1.</span><span class="sxs-lookup"><span data-stu-id="a1492-108">1</span></span>|  
   |`sizeof(byte)`|<span data-ttu-id="a1492-109">1.</span><span class="sxs-lookup"><span data-stu-id="a1492-109">1</span></span>|  
   |`sizeof(short)`|<span data-ttu-id="a1492-110">2</span><span class="sxs-lookup"><span data-stu-id="a1492-110">2</span></span>|  
   |`sizeof(ushort)`|<span data-ttu-id="a1492-111">2</span><span class="sxs-lookup"><span data-stu-id="a1492-111">2</span></span>|  
   |`sizeof(int)`|<span data-ttu-id="a1492-112">4</span><span class="sxs-lookup"><span data-stu-id="a1492-112">4</span></span>|  
   |`sizeof(uint)`|<span data-ttu-id="a1492-113">4</span><span class="sxs-lookup"><span data-stu-id="a1492-113">4</span></span>|  
   |`sizeof(long)`|<span data-ttu-id="a1492-114">8</span><span class="sxs-lookup"><span data-stu-id="a1492-114">8</span></span>|  
   |`sizeof(ulong)`|<span data-ttu-id="a1492-115">8</span><span class="sxs-lookup"><span data-stu-id="a1492-115">8</span></span>|  
   |`sizeof(char)`|<span data-ttu-id="a1492-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="a1492-116">2 (Unicode)</span></span>|  
   |`sizeof(float)`|<span data-ttu-id="a1492-117">4</span><span class="sxs-lookup"><span data-stu-id="a1492-117">4</span></span>|  
   |`sizeof(double)`|<span data-ttu-id="a1492-118">8</span><span class="sxs-lookup"><span data-stu-id="a1492-118">8</span></span>|  
   |`sizeof(decimal)`|<span data-ttu-id="a1492-119">16</span><span class="sxs-lookup"><span data-stu-id="a1492-119">16</span></span>|  
   |`sizeof(bool)`|<span data-ttu-id="a1492-120">1.</span><span class="sxs-lookup"><span data-stu-id="a1492-120">1</span></span>| 
  
-   <span data-ttu-id="a1492-121">Numaralandırma türleri.</span><span class="sxs-lookup"><span data-stu-id="a1492-121">Enum types.</span></span>
  
-   <span data-ttu-id="a1492-122">İşaretçi türleri.</span><span class="sxs-lookup"><span data-stu-id="a1492-122">Pointer types.</span></span>
  
-   <span data-ttu-id="a1492-123">Tüm örnek alanları veya başvuru türleri veya oluşturulan türler otomatik olarak uygulanan örnek özellikler içermeyen kullanıcı tarafından tanımlanan yapılar.</span><span class="sxs-lookup"><span data-stu-id="a1492-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>
  
 <span data-ttu-id="a1492-124">Aşağıdaki örnek boyutunu almak nasıl gösterir bir `int`:</span><span class="sxs-lookup"><span data-stu-id="a1492-124">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="a1492-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1492-125">Remarks</span></span>  
 <span data-ttu-id="a1492-126">C# 2.0 sürümünden itibaren uygulama `sizeof` basit veya sabit listesi türleri artık gerektirir kod içinde derlenecek bir [güvenli](unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="a1492-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>
  
 <span data-ttu-id="a1492-127">`sizeof` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="a1492-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="a1492-128">Tarafından döndürülen değerler `sizeof` işleci, tür `int`.</span><span class="sxs-lookup"><span data-stu-id="a1492-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="a1492-129">Önceki tablonun gösterdiği için yerine sabit değerler `sizeof` işlenen olarak bazı basit türler sahip ifadeler.</span><span class="sxs-lookup"><span data-stu-id="a1492-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>  
    
 <span data-ttu-id="a1492-130">Yapılar, diğer tüm türleri için de dahil olmak üzere `sizeof` işleci yalnızca güvenli olmayan kod blokları içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1492-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="a1492-131">Hizmetini kullanıyor olsanız da <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemi, bu yöntem tarafından döndürülen değeri değil her zaman aynı tarafından döndürülen değer olarak `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="a1492-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="a1492-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> türü sıralanmış sonra ise boyutunu döndürür `sizeof` herhangi doldurma dahil olmak üzere ortak dil çalışma zamanı tarafından ayrılan boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1492-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1492-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1492-133">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a1492-134">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a1492-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1492-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1492-135">See Also</span></span>

- [<span data-ttu-id="a1492-136">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a1492-136">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a1492-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a1492-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a1492-138">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a1492-138">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="a1492-139">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a1492-139">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
- [<span data-ttu-id="a1492-140">enum</span><span class="sxs-lookup"><span data-stu-id="a1492-140">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
- [<span data-ttu-id="a1492-141">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="a1492-141">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="a1492-142">Yapılar</span><span class="sxs-lookup"><span data-stu-id="a1492-142">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [<span data-ttu-id="a1492-143">Sabitler</span><span class="sxs-lookup"><span data-stu-id="a1492-143">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

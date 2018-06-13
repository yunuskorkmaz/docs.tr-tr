---
title: sizeof (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 83038255160ec778c71120566cf8f99092761add
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270584"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="cec1a-102">sizeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cec1a-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="cec1a-103">Yönetilmeyen bir tür için bayt cinsinden boyutu almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cec1a-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="cec1a-104">Yönetilmeyen türleri, aşağıdaki tabloda, aşağıdaki yanı sıra listelenen yerleşik türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cec1a-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="cec1a-105">Numaralandırma türleri</span><span class="sxs-lookup"><span data-stu-id="cec1a-105">Enum types</span></span>  
  
-   <span data-ttu-id="cec1a-106">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="cec1a-106">Pointer types</span></span>  
  
-   <span data-ttu-id="cec1a-107">Herhangi bir alan veya başvuru türleri olan özellikler içermeyen kullanıcı tanımlı yapılar</span><span class="sxs-lookup"><span data-stu-id="cec1a-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="cec1a-108">Aşağıdaki örnek boyutunu almak nasıl gösterir bir `int`:</span><span class="sxs-lookup"><span data-stu-id="cec1a-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="cec1a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cec1a-109">Remarks</span></span>  
 <span data-ttu-id="cec1a-110">C# 2.0 sürümünden başlayarak, uygulama `sizeof` için yerleşik türler artık gerektiren [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) modu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cec1a-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="cec1a-111">`sizeof` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="cec1a-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="cec1a-112">Tarafından döndürülen değer `sizeof` işleci türündedir `int`.</span><span class="sxs-lookup"><span data-stu-id="cec1a-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="cec1a-113">İçin yerine sabit değerleri aşağıdaki tabloda gösterilmektedir `sizeof` işlenen olarak yerleşik belirli türlerine sahip bir ifade.</span><span class="sxs-lookup"><span data-stu-id="cec1a-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="cec1a-114">İfade</span><span class="sxs-lookup"><span data-stu-id="cec1a-114">Expression</span></span>|<span data-ttu-id="cec1a-115">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="cec1a-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="cec1a-116">1.</span><span class="sxs-lookup"><span data-stu-id="cec1a-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="cec1a-117">1.</span><span class="sxs-lookup"><span data-stu-id="cec1a-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="cec1a-118">2</span><span class="sxs-lookup"><span data-stu-id="cec1a-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="cec1a-119">2</span><span class="sxs-lookup"><span data-stu-id="cec1a-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="cec1a-120">4</span><span class="sxs-lookup"><span data-stu-id="cec1a-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="cec1a-121">4</span><span class="sxs-lookup"><span data-stu-id="cec1a-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="cec1a-122">8</span><span class="sxs-lookup"><span data-stu-id="cec1a-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="cec1a-123">8</span><span class="sxs-lookup"><span data-stu-id="cec1a-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="cec1a-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="cec1a-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="cec1a-125">4</span><span class="sxs-lookup"><span data-stu-id="cec1a-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="cec1a-126">8</span><span class="sxs-lookup"><span data-stu-id="cec1a-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="cec1a-127">16</span><span class="sxs-lookup"><span data-stu-id="cec1a-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="cec1a-128">1.</span><span class="sxs-lookup"><span data-stu-id="cec1a-128">1</span></span>|  
  
 <span data-ttu-id="cec1a-129">Yapılar, diğer tüm türler için dahil olmak üzere `sizeof` işleci yalnızca güvenli olmayan kod blokları içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cec1a-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="cec1a-130">Kullanabilirsiniz ancak <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemi, bu yöntem tarafından döndürülen değeri değil her zaman tarafından döndürülen değer ile aynı `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="cec1a-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="cec1a-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> türü sıralanmış sonra ancak boyutunu döndüren `sizeof` herhangi bir doldurmaya dahil olmak üzere ortak dil çalışma zamanı tarafından ayrılmış olarak boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="cec1a-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cec1a-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="cec1a-132">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="cec1a-133">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="cec1a-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cec1a-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cec1a-134">See Also</span></span>  
 [<span data-ttu-id="cec1a-135">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="cec1a-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cec1a-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cec1a-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cec1a-137">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="cec1a-137">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="cec1a-138">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="cec1a-138">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="cec1a-139">enum</span><span class="sxs-lookup"><span data-stu-id="cec1a-139">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
 [<span data-ttu-id="cec1a-140">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="cec1a-140">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="cec1a-141">Yapılar</span><span class="sxs-lookup"><span data-stu-id="cec1a-141">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="cec1a-142">Sabitler</span><span class="sxs-lookup"><span data-stu-id="cec1a-142">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

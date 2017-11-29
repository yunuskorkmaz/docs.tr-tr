---
title: "&lt;özel durum&gt; (C# programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd859a09bfbe9f814bf57f0987fd49ded9ba7100
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="fe689-102">&lt;özel durum&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fe689-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="fe689-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe689-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe689-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe689-104">Parameters</span></span>  
 <span data-ttu-id="fe689-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="fe689-105">cref = " `member`"</span></span>  
 <span data-ttu-id="fe689-106">Geçerli derleme ortamından kullanılabilir bir özel durum referansı.</span><span class="sxs-lookup"><span data-stu-id="fe689-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="fe689-107">Belirtilen özel durum var ve çevirir derleyici denetler `member` XML çıktısında kurallı öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="fe689-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="fe689-108">`member`çift tırnak işaretleri içinde görünmesi gerekir ("").</span><span class="sxs-lookup"><span data-stu-id="fe689-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="fe689-109">Genel bir tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz: [ \<bkz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="fe689-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="fe689-110">Özel durum açıklaması.</span><span class="sxs-lookup"><span data-stu-id="fe689-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe689-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe689-111">Remarks</span></span>  
 <span data-ttu-id="fe689-112">\<Özel durum > etiketi hangi özel durum belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe689-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="fe689-113">Bu etiket yöntemleri, özellikleri, olayları ve dizin oluşturucular için tanımları uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe689-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="fe689-114">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="fe689-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="fe689-115">Özel durum işleme hakkında daha fazla bilgi için bkz: [özel durumlar ve özel durum işleme](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="fe689-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe689-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe689-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fe689-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe689-117">See Also</span></span>  
 [<span data-ttu-id="fe689-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fe689-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fe689-119">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="fe689-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

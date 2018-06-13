---
title: '&lt;özel durum&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: eca61416077896c9fa7d5828bbab79b399ad69d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332666"
---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="97313-102">&lt;özel durum&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="97313-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="97313-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97313-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97313-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97313-104">Parameters</span></span>  
 <span data-ttu-id="97313-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="97313-105">cref = " `member`"</span></span>  
 <span data-ttu-id="97313-106">Geçerli derleme ortamından kullanılabilir bir özel durum referansı.</span><span class="sxs-lookup"><span data-stu-id="97313-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="97313-107">Belirtilen özel durum var ve çevirir derleyici denetler `member` XML çıktısında kurallı öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="97313-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="97313-108">`member` çift tırnak işaretleri içinde görünmesi gerekir ("").</span><span class="sxs-lookup"><span data-stu-id="97313-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="97313-109">Genel bir tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz: [ \<bkz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="97313-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="97313-110">Özel durum açıklaması.</span><span class="sxs-lookup"><span data-stu-id="97313-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97313-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97313-111">Remarks</span></span>  
 <span data-ttu-id="97313-112">\<Özel durum > etiketi hangi özel durum belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="97313-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="97313-113">Bu etiket yöntemleri, özellikleri, olayları ve dizin oluşturucular için tanımları uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="97313-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="97313-114">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="97313-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="97313-115">Özel durum işleme hakkında daha fazla bilgi için bkz: [özel durumlar ve özel durum işleme](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="97313-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97313-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="97313-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="97313-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97313-117">See Also</span></span>  
 [<span data-ttu-id="97313-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="97313-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="97313-119">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="97313-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

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
ms.openlocfilehash: c865fe97db16c95396e03747958d3590e80de614
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129358"
---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="31287-102">&lt;özel durum&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="31287-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="31287-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31287-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31287-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31287-104">Parameters</span></span>  
 <span data-ttu-id="31287-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="31287-105">cref = " `member`"</span></span>  
 <span data-ttu-id="31287-106">Geçerli derleme ortamdan kullanılabilir bir özel durum başvuru.</span><span class="sxs-lookup"><span data-stu-id="31287-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="31287-107">Belirtilen özel var ve çevirir derleyici denetler `member` kurallı öğesi adı ' % s'çıkış XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="31287-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="31287-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="31287-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="31287-109">Genel tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz. [ \<bakın >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="31287-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="31287-110">Özel durumun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="31287-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31287-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31287-111">Remarks</span></span>  
 <span data-ttu-id="31287-112">\<Özel durum > etiketi hangi özel durumlar atılabilir belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="31287-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="31287-113">Bu etiket, yöntemleri, özellikleri, olayları ve dizin oluşturucular için tanımlarına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="31287-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="31287-114">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="31287-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="31287-115">Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="31287-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31287-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="31287-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="31287-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31287-117">See Also</span></span>

- [<span data-ttu-id="31287-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="31287-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="31287-119">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="31287-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

---
title: <exception> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: fe304b9c6631591cf7a3d62fcecd2ed3ca05db9c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257297"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="26032-102">\<Özel Durum > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="26032-102">\<exception> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="26032-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26032-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26032-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26032-104">Parameters</span></span>  
 <span data-ttu-id="26032-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="26032-105">cref = " `member`"</span></span>  
 <span data-ttu-id="26032-106">Geçerli derleme ortamdan kullanılabilir bir özel durum başvuru.</span><span class="sxs-lookup"><span data-stu-id="26032-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="26032-107">Belirtilen özel var ve çevirir derleyici denetler `member` kurallı öğesi adı ' % s'çıkış XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="26032-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="26032-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="26032-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="26032-109">Genel tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz. [ \<bakın >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="26032-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="26032-110">Özel durumun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="26032-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26032-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26032-111">Remarks</span></span>  
 <span data-ttu-id="26032-112">\<Özel durum > etiketi hangi özel durumlar atılabilir belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="26032-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="26032-113">Bu etiket, yöntemleri, özellikleri, olayları ve dizin oluşturucular için tanımlarına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="26032-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="26032-114">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="26032-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="26032-115">Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="26032-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26032-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="26032-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="26032-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26032-117">See also</span></span>

- [<span data-ttu-id="26032-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="26032-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="26032-119">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="26032-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

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
ms.openlocfilehash: b316927c5dfd5eda05bea653f9a601cca9865af3
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982069"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="64320-102">\<Özel Durum > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="64320-102">\<exception> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="64320-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64320-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64320-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64320-104">Parameters</span></span>  
 <span data-ttu-id="64320-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="64320-105">cref = " `member`"</span></span>  
 <span data-ttu-id="64320-106">Geçerli derleme ortamdan kullanılabilir bir özel durum başvuru.</span><span class="sxs-lookup"><span data-stu-id="64320-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="64320-107">Belirtilen özel var ve çevirir derleyici denetler `member` kurallı öğesi adı ' % s'çıkış XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="64320-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="64320-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="64320-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="64320-109">Genel tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz. [ \<bakın >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="64320-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="64320-110">Özel durumun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="64320-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64320-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64320-111">Remarks</span></span>  
 <span data-ttu-id="64320-112">\<Özel durum > etiketi hangi özel durumlar atılabilir belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="64320-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="64320-113">Bu etiket, yöntemleri, özellikleri, olayları ve dizin oluşturucular için tanımlarına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="64320-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="64320-114">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="64320-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="64320-115">Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="64320-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64320-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="64320-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="64320-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64320-117">See also</span></span>

- [<span data-ttu-id="64320-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="64320-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="64320-119">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="64320-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

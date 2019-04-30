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
ms.openlocfilehash: 639e3a345fc8ed3d348461718f73ead6167158db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675929"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="80a4b-102">\<Özel Durum > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="80a4b-102">\<exception> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="80a4b-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80a4b-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="80a4b-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80a4b-104">Parameters</span></span>  
 <span data-ttu-id="80a4b-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="80a4b-105">cref = " `member`"</span></span>  
 <span data-ttu-id="80a4b-106">Geçerli derleme ortamdan kullanılabilir bir özel durum başvuru.</span><span class="sxs-lookup"><span data-stu-id="80a4b-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="80a4b-107">Belirtilen özel var ve çevirir derleyici denetler `member` kurallı öğesi adı ' % s'çıkış XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="80a4b-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="80a4b-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="80a4b-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="80a4b-109">Biçimlendirme hakkında daha fazla bilgi için `member` genel bir tür başvurusu yapmak için bkz: [XML dosyasını işleme](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="80a4b-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>
  
 `description`  
 <span data-ttu-id="80a4b-110">Özel durumun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="80a4b-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80a4b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80a4b-111">Remarks</span></span>  
 <span data-ttu-id="80a4b-112">\<Özel durum > etiketi hangi özel durumlar atılabilir belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="80a4b-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="80a4b-113">Bu etiket, yöntemleri, özellikleri, olayları ve dizin oluşturucular için tanımlarına uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="80a4b-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="80a4b-114">Derleme [/doc](../../language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="80a4b-114">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="80a4b-115">Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="80a4b-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80a4b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="80a4b-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="80a4b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80a4b-117">See also</span></span>

- [<span data-ttu-id="80a4b-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="80a4b-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="80a4b-119">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="80a4b-119">Recommended Tags for Documentation Comments</span></span>](recommended-tags-for-documentation-comments.md)

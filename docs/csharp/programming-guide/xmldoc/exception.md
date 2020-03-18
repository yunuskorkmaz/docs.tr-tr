---
title: <exception>- C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789797"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="b02d6-102">\<özel durum> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b02d6-102">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b02d6-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b02d6-103">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="b02d6-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b02d6-104">Parameters</span></span>

- <span data-ttu-id="b02d6-105">cref = `member`" "</span><span class="sxs-lookup"><span data-stu-id="b02d6-105">cref = " `member`"</span></span>

  <span data-ttu-id="b02d6-106">Geçerli derleme ortamından kullanılabilen bir özel durum için bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="b02d6-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="b02d6-107">Derleyici, verilen özel durum var `member` olduğunu denetler ve xml çıkışındaki kanonik öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="b02d6-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="b02d6-108">`member`çift tırnak işaretleri içinde görünmelidir (" ").</span><span class="sxs-lookup"><span data-stu-id="b02d6-108">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="b02d6-109">Genel bir türe `member` başvurmak için biçimlendirme hakkında daha fazla bilgi için Bkz. [XML Dosyasını İşleme.](processing-the-xml-file.md)</span><span class="sxs-lookup"><span data-stu-id="b02d6-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="b02d6-110">Özel durum açıklaması.</span><span class="sxs-lookup"><span data-stu-id="b02d6-110">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="b02d6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b02d6-111">Remarks</span></span>

<span data-ttu-id="b02d6-112">Özel \<durum> etiketi, hangi özel durumların atılacağını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b02d6-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="b02d6-113">Bu etiket, yöntemler, özellikler, olaylar ve dizin leyiciler için tanımlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b02d6-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="b02d6-114">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="b02d6-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="b02d6-115">Özel durum işleme hakkında daha fazla bilgi için [bkz.](../exceptions/index.md)</span><span class="sxs-lookup"><span data-stu-id="b02d6-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="b02d6-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="b02d6-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="b02d6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b02d6-117">See also</span></span>

- [<span data-ttu-id="b02d6-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b02d6-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b02d6-119">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="b02d6-119">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)

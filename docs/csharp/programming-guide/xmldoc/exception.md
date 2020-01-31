---
title: <exception> C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789797"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="100eb-102">\<özel durum >C# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="100eb-102">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="100eb-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="100eb-103">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="100eb-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="100eb-104">Parameters</span></span>

- <span data-ttu-id="100eb-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="100eb-105">cref = " `member`"</span></span>

  <span data-ttu-id="100eb-106">Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru.</span><span class="sxs-lookup"><span data-stu-id="100eb-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="100eb-107">Derleyici verilen özel durumun var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir.</span><span class="sxs-lookup"><span data-stu-id="100eb-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="100eb-108">`member` çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="100eb-108">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="100eb-109">Genel bir türe başvurmak üzere `member` biçimlendirme hakkında daha fazla bilgi için bkz. [XML dosyasını işleme](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="100eb-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="100eb-110">Özel durumun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="100eb-110">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="100eb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="100eb-111">Remarks</span></span>

<span data-ttu-id="100eb-112">\<özel durum > etiketi hangi özel durumların atılamayacağını belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="100eb-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="100eb-113">Bu etiket Yöntemler, özellikler, olaylar ve Dizin oluşturucular için tanımlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="100eb-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="100eb-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="100eb-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="100eb-115">Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="100eb-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="100eb-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="100eb-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="100eb-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="100eb-117">See also</span></span>

- [<span data-ttu-id="100eb-118">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="100eb-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="100eb-119">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="100eb-119">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)

---
title: <exception> -C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <exception> . Bu etiket hangi özel durumların atılamayacağını belirtmenizi sağlar ve yöntemlere, özelliklere, olaylara ve Dizin oluşturuculara uygulanabilir.
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 37d119e3cde115104d149d8f35b8937efddd70d4
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479104"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="41f6f-104">\<exception> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="41f6f-104">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="41f6f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41f6f-105">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="41f6f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41f6f-106">Parameters</span></span>

- <span data-ttu-id="41f6f-107">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="41f6f-107">cref = " `member`"</span></span>

  <span data-ttu-id="41f6f-108">Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru.</span><span class="sxs-lookup"><span data-stu-id="41f6f-108">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="41f6f-109">Derleyici verilen özel durumun var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="41f6f-109">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="41f6f-110">`member` Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="41f6f-110">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="41f6f-111">Genel bir türe başvurmak için biçimlendirme hakkında daha fazla bilgi için `member` bkz. [XML dosyasını işleme](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="41f6f-111">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="41f6f-112">Özel durumun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="41f6f-112">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="41f6f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41f6f-113">Remarks</span></span>

<span data-ttu-id="41f6f-114">`<exception>`Etiketi hangi özel durumların atılamayacağını belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="41f6f-114">The `<exception>` tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="41f6f-115">Bu etiket Yöntemler, özellikler, olaylar ve Dizin oluşturucular için tanımlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="41f6f-115">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="41f6f-116">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="41f6f-116">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

<span data-ttu-id="41f6f-117">Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="41f6f-117">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="41f6f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="41f6f-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="41f6f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41f6f-119">See also</span></span>

- [<span data-ttu-id="41f6f-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="41f6f-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="41f6f-121">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="41f6f-121">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)

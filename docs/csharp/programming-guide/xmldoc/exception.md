---
title: <exception>-C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: fb193c586456497ee60aad941d56241ad7c6b63a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287405"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="7258b-102">\<exception>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7258b-102">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7258b-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7258b-103">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="7258b-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7258b-104">Parameters</span></span>

- <span data-ttu-id="7258b-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="7258b-105">cref = " `member`"</span></span>

  <span data-ttu-id="7258b-106">Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru.</span><span class="sxs-lookup"><span data-stu-id="7258b-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="7258b-107">Derleyici verilen özel durumun var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="7258b-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="7258b-108">`member`Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="7258b-108">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="7258b-109">Genel bir türe başvurmak için biçimlendirme hakkında daha fazla bilgi için `member` bkz. [XML dosyasını işleme](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="7258b-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="7258b-110">Özel durumun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="7258b-110">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="7258b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7258b-111">Remarks</span></span>

<span data-ttu-id="7258b-112">`<exception>`Etiketi hangi özel durumların atılamayacağını belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7258b-112">The `<exception>` tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="7258b-113">Bu etiket Yöntemler, özellikler, olaylar ve Dizin oluşturucular için tanımlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7258b-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="7258b-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="7258b-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="7258b-115">Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="7258b-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="7258b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="7258b-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="7258b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7258b-117">See also</span></span>

- [<span data-ttu-id="7258b-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7258b-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="7258b-119">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="7258b-119">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)

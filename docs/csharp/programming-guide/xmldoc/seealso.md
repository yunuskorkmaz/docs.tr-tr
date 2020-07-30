---
title: <seealso> -C# Programlama Kılavuzu
description: XML 'i kullanmayı öğrenin <seealso> Etiket. Bu etiket, ' Ayrıca bkz. ' bölümünde görünmesini isteyebileceğiniz metni belirtmenize olanak tanır.
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e8618ef352a4fa7f0fd4c88733c6568b0e12e376
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380650"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="7bc18-105">\<seealso>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7bc18-105">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7bc18-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7bc18-106">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="7bc18-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bc18-107">Parameters</span></span>

- <span data-ttu-id="7bc18-108">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="7bc18-108">cref = " `member`"</span></span>

  <span data-ttu-id="7bc18-109">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="7bc18-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="7bc18-110">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.`member`</span><span class="sxs-lookup"><span data-stu-id="7bc18-110">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="7bc18-111">Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="7bc18-111">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="7bc18-112">Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [cref özniteliği](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="7bc18-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="7bc18-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bc18-113">Remarks</span></span>

<span data-ttu-id="7bc18-114">`<seealso>`Etiketi, Ayrıca bkz. bölümünde görünmesini isteyebileceğiniz metni belirtmenize imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bc18-114">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="7bc18-115">[\<see>](./see.md)Metnin içinden bir bağlantı belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7bc18-115">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="7bc18-116">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="7bc18-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="7bc18-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bc18-117">Example</span></span>

<span data-ttu-id="7bc18-118">[\<summary>](./summary.md)Hakkında bir örnek için bkz \<seealso> ..</span><span class="sxs-lookup"><span data-stu-id="7bc18-118">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bc18-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bc18-119">See also</span></span>

- [<span data-ttu-id="7bc18-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7bc18-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="7bc18-121">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="7bc18-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

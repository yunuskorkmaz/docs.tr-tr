---
title: <see> -C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <see> . Bu etiket, örneğin bir cref özniteliği kullanarak metin içinden bir bağlantı belirtmenize olanak tanır.
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 154feca5e7e4f4d3f5313c4ae05cd991e69e298f
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477767"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="1e8ac-104">\<see> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1e8ac-104">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e8ac-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e8ac-105">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="1e8ac-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e8ac-106">Parameters</span></span>

- <span data-ttu-id="1e8ac-107">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="1e8ac-107">cref = "`member`"</span></span>

  <span data-ttu-id="1e8ac-108">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-108">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="1e8ac-109">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-109">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="1e8ac-110">*Üyeyi* çift tırnak işareti ("") içine koyun.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-110">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="1e8ac-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e8ac-111">Remarks</span></span>

<span data-ttu-id="1e8ac-112">`<see>`Etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-112">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="1e8ac-113">[\<seealso>](./seealso.md)Metnin Ayrıca bkz. bölümüne yerleştirilmesi gerektiğini belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-113">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="1e8ac-114">Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-114">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="1e8ac-115">Ayrıca, ``href`` köprü olarak işlev sağlayacak geçerli bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-115">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="1e8ac-116">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-116">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

<span data-ttu-id="1e8ac-117">Aşağıdaki örnek bir `<see>` Özet bölümü içindeki bir etiketi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-117">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="1e8ac-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e8ac-118">See also</span></span>

- [<span data-ttu-id="1e8ac-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1e8ac-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1e8ac-120">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="1e8ac-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

---
title: <see>-C# Programlama Kılavuzu
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
ms.openlocfilehash: 1cc4982d1ebe9d6896404218a6d200b10cc6503f
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381937"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="6a84a-104">\<see>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6a84a-104">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a84a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6a84a-105">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="6a84a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a84a-106">Parameters</span></span>

- <span data-ttu-id="6a84a-107">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="6a84a-107">cref = "`member`"</span></span>

  <span data-ttu-id="6a84a-108">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="6a84a-108">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="6a84a-109">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-109">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="6a84a-110">*Üyeyi* çift tırnak işareti ("") içine koyun.</span><span class="sxs-lookup"><span data-stu-id="6a84a-110">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="6a84a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a84a-111">Remarks</span></span>

<span data-ttu-id="6a84a-112">`<see>`Etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-112">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="6a84a-113">[\<seealso>](./seealso.md)Metnin Ayrıca bkz. bölümüne yerleştirilmesi gerektiğini belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a84a-113">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="6a84a-114">Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a84a-114">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="6a84a-115">Ayrıca, ``href`` köprü olarak işlev sağlayacak geçerli bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-115">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="6a84a-116">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="6a84a-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="6a84a-117">Aşağıdaki örnek bir `<see>` Özet bölümü içindeki bir etiketi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-117">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="6a84a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a84a-118">See also</span></span>

- [<span data-ttu-id="6a84a-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6a84a-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6a84a-120">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="6a84a-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

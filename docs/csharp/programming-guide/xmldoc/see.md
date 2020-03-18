---
title: <see>- C# programlama kılavuzu
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
ms.openlocfilehash: f4834f88c646b44269f8290c2ad08698c34e714a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627678"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="75aa3-102">\<bkz.> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="75aa3-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="75aa3-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75aa3-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="75aa3-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75aa3-104">Parameters</span></span>

- <span data-ttu-id="75aa3-105">cref =`member`" "</span><span class="sxs-lookup"><span data-stu-id="75aa3-105">cref = "`member`"</span></span>

  <span data-ttu-id="75aa3-106">Geçerli derleme ortamından çağrılabilecek bir üye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="75aa3-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="75aa3-107">Derleyici, verilen kod öğesinin var `member` olduğunu denetler ve XML çıkışındaki öğe adına geçer.</span><span class="sxs-lookup"><span data-stu-id="75aa3-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="75aa3-108">*Üyeyi* çift tırnak işaretleri (" ") içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="75aa3-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="75aa3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75aa3-109">Remarks</span></span>

<span data-ttu-id="75aa3-110">Bkz. \<> etiketi, metin içinden bir bağlantı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="75aa3-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="75aa3-111">Metnin Bkz. Also bölümüne yerleştirilmesi gerektiğini belirtmek için [ \<seealso>](./seealso.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="75aa3-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="75aa3-112">Kod öğeleri için belge sayfalarına dahili köprüler oluşturmak için [cref Özniteliği'ni](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="75aa3-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="75aa3-113">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="75aa3-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="75aa3-114">Aşağıdaki örnekte, \<özet bölümünde> etiketi ni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="75aa3-114">The following example shows a \<see> tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="75aa3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75aa3-115">See also</span></span>

- [<span data-ttu-id="75aa3-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="75aa3-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="75aa3-117">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="75aa3-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

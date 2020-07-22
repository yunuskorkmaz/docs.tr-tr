---
title: <see>-C# Programlama Kılavuzu
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
ms.openlocfilehash: 731e42a6d4d354b043a56dbe150bb03a693a9454
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863792"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="33170-102">\<see>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="33170-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="33170-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="33170-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="33170-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33170-104">Parameters</span></span>

- <span data-ttu-id="33170-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="33170-105">cref = "`member`"</span></span>

  <span data-ttu-id="33170-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="33170-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="33170-107">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.</span><span class="sxs-lookup"><span data-stu-id="33170-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="33170-108">*Üyeyi* çift tırnak işareti ("") içine koyun.</span><span class="sxs-lookup"><span data-stu-id="33170-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="33170-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33170-109">Remarks</span></span>

<span data-ttu-id="33170-110">`<see>`Etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="33170-110">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="33170-111">[\<seealso>](./seealso.md)Metnin Ayrıca bkz. bölümüne yerleştirilmesi gerektiğini belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="33170-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="33170-112">Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="33170-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="33170-113">Ayrıca, ``href`` köprü olarak işlev sağlayacak geçerli bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="33170-113">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="33170-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="33170-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="33170-115">Aşağıdaki örnek bir `<see>` Özet bölümü içindeki bir etiketi gösterir.</span><span class="sxs-lookup"><span data-stu-id="33170-115">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="33170-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33170-116">See also</span></span>

- [<span data-ttu-id="33170-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="33170-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="33170-118">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="33170-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

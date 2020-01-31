---
title: <seealso> - C# Programlama Kılavuzu
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
ms.openlocfilehash: ad22b423d085a152f47c4e34d7ee4247ef9836b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789690"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="24286-102">\<SeeAlso > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="24286-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="24286-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24286-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="24286-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24286-104">Parameters</span></span>

- <span data-ttu-id="24286-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="24286-105">cref = " `member`"</span></span>

  <span data-ttu-id="24286-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="24286-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="24286-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir.`member`</span><span class="sxs-lookup"><span data-stu-id="24286-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="24286-108">Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="24286-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="24286-109">Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [\<](./see.md).</span><span class="sxs-lookup"><span data-stu-id="24286-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="24286-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24286-110">Remarks</span></span>

<span data-ttu-id="24286-111">\<seede > etiketi, Ayrıca bkz. bölümünde görünmesini isteyebileceğiniz metni belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="24286-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="24286-112">Metin içinden bir bağlantı belirtmek için [\<> bakın](./see.md) .</span><span class="sxs-lookup"><span data-stu-id="24286-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="24286-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="24286-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="24286-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="24286-114">Example</span></span>

<span data-ttu-id="24286-115">Bkz. \<SeeAlso > kullanımı örneği için [\<özet >](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="24286-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="24286-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24286-116">See also</span></span>

- [<span data-ttu-id="24286-117">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="24286-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="24286-118">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="24286-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

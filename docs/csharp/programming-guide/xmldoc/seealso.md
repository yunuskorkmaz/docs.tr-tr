---
title: <seealso> - C# Programlama Kılavuzu
ms.custom: seodec18
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
ms.openlocfilehash: 430270c170f2829d9bf9b90d258c948176b9c086
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523332"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="1f350-102">\<seealso > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1f350-102">\<seealso> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1f350-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f350-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f350-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f350-104">Parameters</span></span>  
 <span data-ttu-id="1f350-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="1f350-105">cref = " `member`"</span></span>  
 <span data-ttu-id="1f350-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="1f350-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="1f350-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir. `member`</span><span class="sxs-lookup"><span data-stu-id="1f350-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="1f350-108">Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f350-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="1f350-109">Genel bir türe cref başvurusu oluşturma hakkında bilgi için bkz. [\<see >](./see.md).</span><span class="sxs-lookup"><span data-stu-id="1f350-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f350-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f350-110">Remarks</span></span>  
 <span data-ttu-id="1f350-111">@No__t_0seealso > etiketi, Ayrıca bkz. bölümünde görünmesini isteyebileceğiniz metni belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1f350-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="1f350-112">Metnin içinden bir bağlantı belirtmek için [\<see >](./see.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f350-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="1f350-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="1f350-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f350-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f350-114">Example</span></span>  
 <span data-ttu-id="1f350-115">@No__t_2seealso > kullanma örneği için bkz. [\<summary >](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="1f350-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f350-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f350-116">See also</span></span>

- [<span data-ttu-id="1f350-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1f350-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1f350-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="1f350-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)

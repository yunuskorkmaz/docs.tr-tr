---
title: '&lt;bkz:&gt; (C# programlama Kılavuzu)'
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
ms.openlocfilehash: c37ad869b3eb904377cd4470a85cd557f6560290
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43737794"
---
# <a name="ltseegt-c-programming-guide"></a><span data-ttu-id="b59fd-102">&lt;bkz:&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b59fd-102">&lt;see&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b59fd-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b59fd-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b59fd-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b59fd-104">Parameters</span></span>  
 <span data-ttu-id="b59fd-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="b59fd-105">cref = " `member`"</span></span>  
 <span data-ttu-id="b59fd-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="b59fd-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="b59fd-107">Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı. Bir yerde *üye* içinde çift tırnak ("").</span><span class="sxs-lookup"><span data-stu-id="b59fd-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b59fd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b59fd-108">Remarks</span></span>  
 <span data-ttu-id="b59fd-109">\<Bakın > etiketi bağlantı metninde belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b59fd-109">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="b59fd-110">Kullanım [ \<seealso >](../../../csharp/programming-guide/xmldoc/seealso.md) metin ayrıca bölümü yerleştirilmesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="b59fd-110">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="b59fd-111">Kullanım [cref özniteliği](../../../csharp/programming-guide/xmldoc/cref-attribute.md) iç kod öğeleri için belge sayfalarına köprüler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b59fd-111">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="b59fd-112">Derleme [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="b59fd-112">Compile with [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="b59fd-113">Aşağıdaki örnekte gösterildiği bir \<bakın > etiketi içinde Özet bölümü.</span><span class="sxs-lookup"><span data-stu-id="b59fd-113">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b59fd-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b59fd-114">See Also</span></span>

- [<span data-ttu-id="b59fd-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b59fd-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b59fd-116">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="b59fd-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

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
ms.openlocfilehash: 24fa317a0f89568d9aa1b53849e327ef7615cc7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348797"
---
# <a name="ltseegt-c-programming-guide"></a><span data-ttu-id="92e35-102">&lt;bkz:&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="92e35-102">&lt;see&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="92e35-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92e35-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92e35-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92e35-104">Parameters</span></span>  
 <span data-ttu-id="92e35-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="92e35-105">cref = " `member`"</span></span>  
 <span data-ttu-id="92e35-106">Bir üye ya da geçerli derleme ortamından çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="92e35-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="92e35-107">Verilen code öğesi var ve geçirir derleyici denetler `member` çıktı XML öğesi adı. Yer *üye* çift tırnak işareti ("").</span><span class="sxs-lookup"><span data-stu-id="92e35-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92e35-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92e35-108">Remarks</span></span>  
 <span data-ttu-id="92e35-109">\<Bkz > etiketi metin içindeki bir bağlantıdan belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="92e35-109">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="92e35-110">Kullanım [ \<seealso >](../../../csharp/programming-guide/xmldoc/seealso.md) metin bir Ayrıca bkz. bölümünde yerleştirilmesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="92e35-110">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="92e35-111">Kullanım [cref özniteliği](../../../csharp/programming-guide/xmldoc/cref-attribute.md) kod öğeleri için belgeleri sayfalara iç köprüler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="92e35-111">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="92e35-112">İle derleme [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="92e35-112">Compile with [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="92e35-113">Aşağıdaki örnekte gösterildiği bir \<bkz > Özet bölümü içindeki etiketi.</span><span class="sxs-lookup"><span data-stu-id="92e35-113">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="92e35-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92e35-114">See Also</span></span>  
 [<span data-ttu-id="92e35-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="92e35-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="92e35-116">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="92e35-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

---
title: <see> - C# Programlama Kılavuzu
ms.custom: seodec18
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
ms.openlocfilehash: 90fd73346d255d195fa7384ebc2f60ebc4f32fba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675825"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="593e1-102">\<bkz: > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="593e1-102">\<see> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="593e1-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="593e1-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="593e1-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="593e1-104">Parameters</span></span>  
 <span data-ttu-id="593e1-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="593e1-105">cref = " `member`"</span></span>  
 <span data-ttu-id="593e1-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="593e1-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="593e1-107">Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="593e1-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="593e1-108">Bir yerde *üye* içinde çift tırnak ("").</span><span class="sxs-lookup"><span data-stu-id="593e1-108">Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="593e1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="593e1-109">Remarks</span></span>  
 <span data-ttu-id="593e1-110">\<Bakın > etiketi bağlantı metninde belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="593e1-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="593e1-111">Kullanım [ \<seealso >](../../../csharp/programming-guide/xmldoc/seealso.md) metin ayrıca bölümü yerleştirilmesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="593e1-111">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="593e1-112">Kullanım [cref özniteliği](../../../csharp/programming-guide/xmldoc/cref-attribute.md) iç kod öğeleri için belge sayfalarına köprüler oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="593e1-112">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="593e1-113">Derleme [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="593e1-113">Compile with [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="593e1-114">Aşağıdaki örnekte gösterildiği bir \<bakın > etiketi içinde Özet bölümü.</span><span class="sxs-lookup"><span data-stu-id="593e1-114">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
## <a name="see-also"></a><span data-ttu-id="593e1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="593e1-115">See also</span></span>

- [<span data-ttu-id="593e1-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="593e1-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="593e1-117">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="593e1-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

---
title: '&lt;bkz:&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 78311651593d3d4a47c723f64a9a74d4660f7c90
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535083"
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="f3b40-102">&lt;bkz:&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3b40-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="f3b40-103">Başka bir üyesine bir bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3b40-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3b40-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3b40-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3b40-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3b40-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="f3b40-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="f3b40-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="f3b40-107">Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="f3b40-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="f3b40-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="f3b40-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3b40-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3b40-109">Remarks</span></span>  
 <span data-ttu-id="f3b40-110">Kullanım `<see>` bağlantı metninde belirtmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="f3b40-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="f3b40-111">Kullanım [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) "bir Ayrıca bkz:" bölümünde görünmesini istediğiniz metni belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f3b40-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="f3b40-112">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="f3b40-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3b40-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3b40-113">Example</span></span>  
 <span data-ttu-id="f3b40-114">Bu örnekte `<see>` içindeki `UpdateRecord` başvurmak için bölüm açıklamalar `DoesRecordExist` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f3b40-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f3b40-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3b40-115">See Also</span></span>  
 [<span data-ttu-id="f3b40-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="f3b40-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

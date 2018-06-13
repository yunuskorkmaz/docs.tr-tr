---
title: '&lt;bkz:&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: e790f8abd216e198ff5077beab6f857e39981d2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602086"
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="327f8-102">&lt;bkz:&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="327f8-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="327f8-103">Başka bir üye bağlantısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="327f8-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="327f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="327f8-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="327f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="327f8-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="327f8-106">Bir üye ya da geçerli derleme ortamından çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="327f8-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="327f8-107">Verilen code öğesi var ve geçirir derleyici denetler `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="327f8-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="327f8-108">`member` çift tırnak işaretleri içinde görünmesi gerekir ("").</span><span class="sxs-lookup"><span data-stu-id="327f8-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="327f8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="327f8-109">Remarks</span></span>  
 <span data-ttu-id="327f8-110">Kullanım `<see>` etiket metin içindeki bir bağlantıdan belirtin.</span><span class="sxs-lookup"><span data-stu-id="327f8-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="327f8-111">Kullanım [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) "bir Ayrıca bkz:" bölümünde görünen isteyebilirsiniz metin belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="327f8-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="327f8-112">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="327f8-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="327f8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="327f8-113">Example</span></span>  
 <span data-ttu-id="327f8-114">Bu örnekte `<see>` içinde etiketi `UpdateRecord` başvurmak için bölüm açıklamalar `DoesRecordExist` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="327f8-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="327f8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="327f8-115">See Also</span></span>  
 [<span data-ttu-id="327f8-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="327f8-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

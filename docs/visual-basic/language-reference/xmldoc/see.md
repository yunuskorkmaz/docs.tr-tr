---
title: '&lt;bkz:&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: afc67d744a04f404a275077ecac42556c963d472
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722035"
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="16e14-102">&lt;bkz:&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16e14-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="16e14-103">Başka bir üyesine bir bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="16e14-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16e14-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16e14-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16e14-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="16e14-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="16e14-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="16e14-107">Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="16e14-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="16e14-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="16e14-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16e14-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16e14-109">Remarks</span></span>  
 <span data-ttu-id="16e14-110">Kullanım `<see>` bağlantı metninde belirtmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="16e14-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="16e14-111">Kullanım [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) "bir Ayrıca bkz:" bölümünde görünmesini istediğiniz metni belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="16e14-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="16e14-112">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="16e14-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16e14-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="16e14-113">Example</span></span>  
 <span data-ttu-id="16e14-114">Bu örnekte `<see>` içindeki `UpdateRecord` başvurmak için bölüm açıklamalar `DoesRecordExist` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="16e14-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="16e14-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16e14-115">See also</span></span>
- [<span data-ttu-id="16e14-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="16e14-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

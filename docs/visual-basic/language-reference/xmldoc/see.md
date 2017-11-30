---
title: '&lt;bkz:&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 010a3403d7748653648b323ad07f52bf93db2879
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="67454-102">&lt;bkz:&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67454-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="67454-103">Başka bir üye bağlantısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="67454-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67454-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67454-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67454-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67454-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="67454-106">Bir üye ya da geçerli derleme ortamından çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="67454-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="67454-107">Verilen code öğesi var ve geçirir derleyici denetler `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="67454-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="67454-108">`member`çift tırnak işaretleri içinde görünmesi gerekir ("").</span><span class="sxs-lookup"><span data-stu-id="67454-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67454-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67454-109">Remarks</span></span>  
 <span data-ttu-id="67454-110">Kullanım `<see>` etiket metin içindeki bir bağlantıdan belirtin.</span><span class="sxs-lookup"><span data-stu-id="67454-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="67454-111">Kullanım [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) "bir Ayrıca bkz:" bölümünde görünen isteyebilirsiniz metin belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="67454-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="67454-112">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="67454-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67454-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="67454-113">Example</span></span>  
 <span data-ttu-id="67454-114">Bu örnekte `<see>` içinde etiketi `UpdateRecord` başvurmak için bölüm açıklamalar `DoesRecordExist` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67454-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="67454-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67454-115">See Also</span></span>  
 [<span data-ttu-id="67454-116">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="67454-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

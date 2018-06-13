---
title: '&lt;SeeAlso&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 1d45c0c5fa95de9cfa345c0bdbf496aa227b9af5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604685"
---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="77208-102">&lt;SeeAlso&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77208-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="77208-103">Ayrıca bkz. bölümünde görünen bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="77208-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77208-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77208-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77208-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77208-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="77208-106">Bir üye ya da geçerli derleme ortamından çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="77208-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="77208-107">Verilen code öğesi var ve geçirir derleyici denetler `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="77208-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="77208-108">`member` çift tırnak işaretleri içinde görünmesi gerekir ("").</span><span class="sxs-lookup"><span data-stu-id="77208-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77208-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77208-109">Remarks</span></span>  
 <span data-ttu-id="77208-110">Kullanım `<seealso>` etiketi bir Ayrıca bkz. bölümünde görünmesini istediğiniz metni belirtin.</span><span class="sxs-lookup"><span data-stu-id="77208-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="77208-111">Kullanım [ \<bkz >](../../../visual-basic/language-reference/xmldoc/see.md) metin içindeki bir bağlantıdan belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="77208-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="77208-112">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="77208-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77208-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="77208-113">Example</span></span>  
 <span data-ttu-id="77208-114">Bu örnekte `<seealso>` içinde etiketi `DoesRecordExist` başvurmak için bölüm açıklamalar `UpdateRecord` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77208-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="77208-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77208-115">See Also</span></span>  
 [<span data-ttu-id="77208-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="77208-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

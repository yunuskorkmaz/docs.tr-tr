---
title: '&lt;SeeAlso&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: a792bbea108bcdf33d430c47773466ef3dccdb0c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44182836"
---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="d8fc9-102">&lt;SeeAlso&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8fc9-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="d8fc9-103">Ayrıca bkz. bölümünde görünen bağlantıyı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8fc9-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8fc9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8fc9-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8fc9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8fc9-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="d8fc9-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="d8fc9-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="d8fc9-107">Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="d8fc9-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="d8fc9-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="d8fc9-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8fc9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8fc9-109">Remarks</span></span>  
 <span data-ttu-id="d8fc9-110">Kullanım `<seealso>` ayrıca bölümü görünmesini istediğiniz metni belirtmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="d8fc9-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="d8fc9-111">Kullanım [ \<bakın >](../../../visual-basic/language-reference/xmldoc/see.md) bağlantı metninde belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="d8fc9-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="d8fc9-112">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="d8fc9-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8fc9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8fc9-113">Example</span></span>  
 <span data-ttu-id="d8fc9-114">Bu örnekte `<seealso>` içindeki `DoesRecordExist` başvurmak için bölüm açıklamalar `UpdateRecord` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d8fc9-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d8fc9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8fc9-115">See Also</span></span>  
 [<span data-ttu-id="d8fc9-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d8fc9-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

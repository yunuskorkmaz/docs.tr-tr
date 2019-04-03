---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0df999ef502bf61bdfb65cb472947b93efded36e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823486"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="13312-102">\<SeeAlso > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13312-102">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="13312-103">Ayrıca bkz. bölümünde görünen bağlantıyı belirtir.</span><span class="sxs-lookup"><span data-stu-id="13312-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13312-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13312-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="13312-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13312-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="13312-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="13312-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="13312-107">Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="13312-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="13312-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="13312-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13312-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13312-109">Remarks</span></span>  
 <span data-ttu-id="13312-110">Kullanım `<seealso>` ayrıca bölümü görünmesini istediğiniz metni belirtmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="13312-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="13312-111">Kullanım [ \<bakın >](../../../visual-basic/language-reference/xmldoc/see.md) bağlantı metninde belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="13312-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="13312-112">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="13312-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13312-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="13312-113">Example</span></span>  
 <span data-ttu-id="13312-114">Bu örnekte `<seealso>` içindeki `DoesRecordExist` başvurmak için bölüm açıklamalar `UpdateRecord` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="13312-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="13312-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13312-115">See also</span></span>

- [<span data-ttu-id="13312-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="13312-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

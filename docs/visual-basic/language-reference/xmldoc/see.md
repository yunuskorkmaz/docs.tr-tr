---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 828e55e0ddb0382c16c60ae3d9e5958c18e42c10
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821344"
---
# <a name="see-visual-basic"></a><span data-ttu-id="07298-102">\<bkz: > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07298-102">\<see> (Visual Basic)</span></span>
<span data-ttu-id="07298-103">Başka bir üyesine bir bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="07298-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07298-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07298-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="07298-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07298-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="07298-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="07298-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="07298-107">Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="07298-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="07298-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="07298-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07298-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07298-109">Remarks</span></span>  
 <span data-ttu-id="07298-110">Kullanım `<see>` bağlantı metninde belirtmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="07298-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="07298-111">Kullanım [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) "bir Ayrıca bkz:" bölümünde görünmesini istediğiniz metni belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="07298-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="07298-112">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="07298-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07298-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="07298-113">Example</span></span>  
 <span data-ttu-id="07298-114">Bu örnekte `<see>` içindeki `UpdateRecord` başvurmak için bölüm açıklamalar `DoesRecordExist` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07298-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="07298-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07298-115">See also</span></span>

- [<span data-ttu-id="07298-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="07298-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

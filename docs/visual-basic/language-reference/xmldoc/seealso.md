---
title: '&lt;SeeAlso&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: a792bbea108bcdf33d430c47773466ef3dccdb0c
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326234"
---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="05337-102">&lt;SeeAlso&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05337-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="05337-103">Ayrıca bkz. bölümünde görünen bağlantıyı belirtir.</span><span class="sxs-lookup"><span data-stu-id="05337-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05337-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05337-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05337-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05337-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="05337-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="05337-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="05337-107">Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="05337-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="05337-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="05337-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05337-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05337-109">Remarks</span></span>  
 <span data-ttu-id="05337-110">Kullanım `<seealso>` ayrıca bölümü görünmesini istediğiniz metni belirtmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="05337-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="05337-111">Kullanım [ \<bakın >](../../../visual-basic/language-reference/xmldoc/see.md) bağlantı metninde belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="05337-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="05337-112">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="05337-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05337-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="05337-113">Example</span></span>  
 <span data-ttu-id="05337-114">Bu örnekte `<seealso>` içindeki `DoesRecordExist` başvurmak için bölüm açıklamalar `UpdateRecord` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05337-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="05337-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05337-115">See Also</span></span>  
 [<span data-ttu-id="05337-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="05337-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 27bb2c271631170082709d9e3d76cd39eefbc860
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352215"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="dfe53-101">\<seede > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfe53-101">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="dfe53-102">Ayrıca bkz. bölümünde görüntülenen bir bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfe53-102">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfe53-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfe53-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfe53-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dfe53-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="dfe53-105">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="dfe53-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="dfe53-106">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir.</span><span class="sxs-lookup"><span data-stu-id="dfe53-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="dfe53-107">`member` çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe53-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfe53-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfe53-108">Remarks</span></span>  
 <span data-ttu-id="dfe53-109">Ayrıca bkz. bölümünde görünmesini istediğiniz metni belirtmek için `<seealso>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfe53-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="dfe53-110">Metin içinden bir bağlantı belirtmek için [\<> bakın](../../../visual-basic/language-reference/xmldoc/see.md) .</span><span class="sxs-lookup"><span data-stu-id="dfe53-110">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="dfe53-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="dfe53-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfe53-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfe53-112">Example</span></span>  
 <span data-ttu-id="dfe53-113">Bu örnek `UpdateRecord` yöntemine başvurmak için `DoesRecordExist` açıklamaları bölümündeki `<seealso>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dfe53-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="dfe53-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfe53-114">See also</span></span>

- [<span data-ttu-id="dfe53-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="dfe53-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

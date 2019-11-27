---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 3c149b8ff60bcc2aba06856ad95f461fb18da4b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352223"
---
# <a name="see-visual-basic"></a><span data-ttu-id="2a489-101">\<bkz. > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a489-101">\<see> (Visual Basic)</span></span>
<span data-ttu-id="2a489-102">Başka bir üyeye bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a489-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a489-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a489-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a489-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a489-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="2a489-105">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="2a489-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="2a489-106">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir.</span><span class="sxs-lookup"><span data-stu-id="2a489-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="2a489-107">`member` çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a489-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a489-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a489-108">Remarks</span></span>  
 <span data-ttu-id="2a489-109">Metnin içinden bir bağlantı belirtmek için `<see>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a489-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="2a489-110">"Ayrıca bkz." bölümünde görünmesini isteyebileceğiniz metni göstermek için [>\<de](../../../visual-basic/language-reference/xmldoc/seealso.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a489-110">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="2a489-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="2a489-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a489-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a489-112">Example</span></span>  
 <span data-ttu-id="2a489-113">Bu örnek `DoesRecordExist` yöntemine başvurmak için `UpdateRecord` açıklamaları bölümündeki `<see>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a489-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2a489-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a489-114">See also</span></span>

- [<span data-ttu-id="2a489-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="2a489-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

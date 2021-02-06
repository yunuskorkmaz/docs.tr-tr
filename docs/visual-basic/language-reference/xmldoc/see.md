---
description: 'Hakkında daha fazla bilgi edinin: <see> (Visual Basic)'
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 46dd67710f83d6c4549ddfeb6b7bbc1503b7aa1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640348"
---
# <a name="see-visual-basic"></a><span data-ttu-id="24616-102">\<see> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24616-102">\<see> (Visual Basic)</span></span>

<span data-ttu-id="24616-103">Başka bir üyeye bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="24616-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24616-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24616-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="24616-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24616-105">Parameters</span></span>  

 `member`  
 <span data-ttu-id="24616-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="24616-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="24616-107">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.</span><span class="sxs-lookup"><span data-stu-id="24616-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="24616-108">`member` Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="24616-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24616-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24616-109">Remarks</span></span>  

 <span data-ttu-id="24616-110">`<see>`Metnin içinden bir bağlantı belirtmek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="24616-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="24616-111">[\<seealso>](seealso.md)"Ayrıca bkz." bölümünde görünmesini isteyebileceğiniz metni göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="24616-111">Use [\<seealso>](seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="24616-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="24616-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24616-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="24616-113">Example</span></span>  

 <span data-ttu-id="24616-114">Bu örnek, `<see>` `UpdateRecord` yöntemine başvurmak için açıklamalar bölümündeki etiketini kullanır `DoesRecordExist` .</span><span class="sxs-lookup"><span data-stu-id="24616-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="24616-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24616-115">See also</span></span>

- [<span data-ttu-id="24616-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="24616-116">XML Comment Tags</span></span>](index.md)

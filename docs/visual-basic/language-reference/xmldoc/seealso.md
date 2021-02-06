---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <seealso> (Visual Basic)'
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0bf6fa69ad63db016b42e31f717f521f82bbe20e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640322"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="fb810-103">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb810-103">\<seealso> (Visual Basic)</span></span>

<span data-ttu-id="fb810-104">Ayrıca bkz. bölümünde görüntülenen bir bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb810-104">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb810-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb810-105">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb810-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb810-106">Parameters</span></span>  

 `member`  
 <span data-ttu-id="fb810-107">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="fb810-107">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="fb810-108">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.</span><span class="sxs-lookup"><span data-stu-id="fb810-108">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="fb810-109">`member` Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb810-109">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb810-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb810-110">Remarks</span></span>  

 <span data-ttu-id="fb810-111">`<seealso>`Ayrıca bkz. bölümünde görünmesini istediğiniz metni belirtmek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fb810-111">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="fb810-112">[\<see>](see.md)Metnin içinden bir bağlantı belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="fb810-112">Use [\<see>](see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="fb810-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="fb810-113">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb810-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb810-114">Example</span></span>  

 <span data-ttu-id="fb810-115">Bu örnek, `<seealso>` `DoesRecordExist` yöntemine başvurmak için açıklamalar bölümündeki etiketini kullanır `UpdateRecord` .</span><span class="sxs-lookup"><span data-stu-id="fb810-115">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="fb810-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb810-116">See also</span></span>

- [<span data-ttu-id="fb810-117">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="fb810-117">XML Comment Tags</span></span>](index.md)

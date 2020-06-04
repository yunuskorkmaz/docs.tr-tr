---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 5999a4ebcc90f21ee8331b96ffb2a50f7905b1b6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411518"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="9e50f-101">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e50f-101">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="9e50f-102">Ayrıca bkz. bölümünde görüntülenen bir bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e50f-102">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e50f-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9e50f-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e50f-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e50f-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="9e50f-105">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="9e50f-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="9e50f-106">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.</span><span class="sxs-lookup"><span data-stu-id="9e50f-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="9e50f-107">`member`Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e50f-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e50f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e50f-108">Remarks</span></span>  
 <span data-ttu-id="9e50f-109">`<seealso>`Ayrıca bkz. bölümünde görünmesini istediğiniz metni belirtmek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e50f-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="9e50f-110">[\<see>](see.md)Metnin içinden bir bağlantı belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e50f-110">Use [\<see>](see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="9e50f-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="9e50f-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e50f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e50f-112">Example</span></span>  
 <span data-ttu-id="9e50f-113">Bu örnek, `<seealso>` `DoesRecordExist` yöntemine başvurmak için açıklamalar bölümündeki etiketini kullanır `UpdateRecord` .</span><span class="sxs-lookup"><span data-stu-id="9e50f-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="9e50f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e50f-114">See also</span></span>

- [<span data-ttu-id="9e50f-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="9e50f-115">XML Comment Tags</span></span>](index.md)

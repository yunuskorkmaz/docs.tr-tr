---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 51eaaef2ddb88afbb52ab58b85ed1a58ba251c1e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866449"
---
# <a name="see-visual-basic"></a><span data-ttu-id="a4511-101">\<see> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4511-101">\<see> (Visual Basic)</span></span>

<span data-ttu-id="a4511-102">Başka bir üyeye bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4511-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4511-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4511-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4511-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4511-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="a4511-105">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="a4511-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a4511-106">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.</span><span class="sxs-lookup"><span data-stu-id="a4511-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="a4511-107">`member` Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4511-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4511-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4511-108">Remarks</span></span>  

 <span data-ttu-id="a4511-109">`<see>`Metnin içinden bir bağlantı belirtmek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4511-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="a4511-110">[\<seealso>](seealso.md)"Ayrıca bkz." bölümünde görünmesini isteyebileceğiniz metni göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4511-110">Use [\<seealso>](seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="a4511-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="a4511-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4511-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4511-112">Example</span></span>  

 <span data-ttu-id="a4511-113">Bu örnek, `<see>` `UpdateRecord` yöntemine başvurmak için açıklamalar bölümündeki etiketini kullanır `DoesRecordExist` .</span><span class="sxs-lookup"><span data-stu-id="a4511-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a4511-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4511-114">See also</span></span>

- [<span data-ttu-id="a4511-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="a4511-115">XML Comment Tags</span></span>](index.md)

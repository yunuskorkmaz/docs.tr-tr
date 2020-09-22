---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: ae6167f3582fe22cd10d9ef7a10873d6d9bdfa06
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872546"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="94130-101">\<permission> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94130-101">\<permission> (Visual Basic)</span></span>

<span data-ttu-id="94130-102">Üye için gerekli izinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="94130-102">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94130-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94130-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="94130-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94130-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="94130-105">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="94130-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="94130-106">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="94130-106">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="94130-107">`member`Tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="94130-107">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="94130-108">Üyeye erişim açıklaması.</span><span class="sxs-lookup"><span data-stu-id="94130-108">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94130-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94130-109">Remarks</span></span>  

 <span data-ttu-id="94130-110">`<permission>`Bir üyenin erişimini belgelemek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="94130-110">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="94130-111"><xref:System.Security.PermissionSet>Bir üyeye erişimi belirtmek için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="94130-111">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="94130-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="94130-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94130-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="94130-113">Example</span></span>  

 <span data-ttu-id="94130-114">Bu örnek, `<permission>` yöntemi için gerekli olduğunu betimleyen etiketini kullanır <xref:System.Security.Permissions.FileIOPermission> `ReadFile` .</span><span class="sxs-lookup"><span data-stu-id="94130-114">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="94130-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94130-115">See also</span></span>

- [<span data-ttu-id="94130-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="94130-116">XML Comment Tags</span></span>](index.md)

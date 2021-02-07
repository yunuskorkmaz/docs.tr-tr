---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <permission> (Visual Basic)'
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 7a227e97051002c834c96297d3028f08e3ed07ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700266"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="572a7-103">\<permission> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="572a7-103">\<permission> (Visual Basic)</span></span>

<span data-ttu-id="572a7-104">Üye için gerekli izinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="572a7-104">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="572a7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="572a7-105">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="572a7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="572a7-106">Parameters</span></span>  

 `member`  
 <span data-ttu-id="572a7-107">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="572a7-107">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="572a7-108">Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="572a7-108">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="572a7-109">`member`Tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="572a7-109">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="572a7-110">Üyeye erişim açıklaması.</span><span class="sxs-lookup"><span data-stu-id="572a7-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="572a7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="572a7-111">Remarks</span></span>  

 <span data-ttu-id="572a7-112">`<permission>`Bir üyenin erişimini belgelemek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="572a7-112">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="572a7-113"><xref:System.Security.PermissionSet>Bir üyeye erişimi belirtmek için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="572a7-113">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="572a7-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="572a7-114">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="572a7-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="572a7-115">Example</span></span>  

 <span data-ttu-id="572a7-116">Bu örnek, `<permission>` yöntemi için gerekli olduğunu betimleyen etiketini kullanır <xref:System.Security.Permissions.FileIOPermission> `ReadFile` .</span><span class="sxs-lookup"><span data-stu-id="572a7-116">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="572a7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="572a7-117">See also</span></span>

- [<span data-ttu-id="572a7-118">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="572a7-118">XML Comment Tags</span></span>](index.md)

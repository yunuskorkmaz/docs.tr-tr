---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: dbd99997fed33c192a2160fb45a739addbae254a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524614"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="17678-102">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17678-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="17678-103">Bir tür parametresi adı ve açıklaması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17678-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17678-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17678-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="17678-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17678-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="17678-106">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="17678-106">The name of the type parameter.</span></span> <span data-ttu-id="17678-107">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="17678-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="17678-108">Tür parametresinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="17678-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17678-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17678-109">Remarks</span></span>  
 <span data-ttu-id="17678-110">Tür parametrelerinden birini belirtmek için genel bir tür veya genel üye bildirimi açıklamasında `<typeparam>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="17678-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="17678-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="17678-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17678-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="17678-112">Example</span></span>  
 <span data-ttu-id="17678-113">Bu örnek, `id` parametresini anlatmak için `<typeparam>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="17678-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="17678-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17678-114">See also</span></span>

- [<span data-ttu-id="17678-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="17678-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

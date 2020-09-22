---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 0a68cf0a495c2809961e8ec99effa459b0647fec
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866386"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="d4583-101">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4583-101">\<typeparam> (Visual Basic)</span></span>

<span data-ttu-id="d4583-102">Bir tür parametresi adı ve açıklaması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4583-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4583-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4583-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4583-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4583-104">Parameters</span></span>  

 `name`  
 <span data-ttu-id="d4583-105">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="d4583-105">The name of the type parameter.</span></span> <span data-ttu-id="d4583-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="d4583-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d4583-107">Tür parametresinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="d4583-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4583-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4583-108">Remarks</span></span>  

 <span data-ttu-id="d4583-109">`<typeparam>`Tür parametrelerinden birini belirtmek için genel bir tür veya genel üye bildirimi için açıklamadaki etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4583-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="d4583-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="d4583-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4583-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4583-111">Example</span></span>  

 <span data-ttu-id="d4583-112">Bu örnek, `<typeparam>` parametresini anlatmak için etiketini kullanır `id` .</span><span class="sxs-lookup"><span data-stu-id="d4583-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="d4583-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4583-113">See also</span></span>

- [<span data-ttu-id="d4583-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d4583-114">XML Comment Tags</span></span>](index.md)

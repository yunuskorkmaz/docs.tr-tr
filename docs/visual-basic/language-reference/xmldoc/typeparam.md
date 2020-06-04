---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 2ad54845645172acb5b91935f5347a828510e3aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411492"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="72b10-101">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b10-101">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="72b10-102">Bir tür parametresi adı ve açıklaması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72b10-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72b10-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="72b10-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="72b10-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72b10-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="72b10-105">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="72b10-105">The name of the type parameter.</span></span> <span data-ttu-id="72b10-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="72b10-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="72b10-107">Tür parametresinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="72b10-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72b10-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72b10-108">Remarks</span></span>  
 <span data-ttu-id="72b10-109">`<typeparam>`Tür parametrelerinden birini belirtmek için genel bir tür veya genel üye bildirimi için açıklamadaki etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="72b10-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="72b10-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="72b10-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72b10-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="72b10-111">Example</span></span>  
 <span data-ttu-id="72b10-112">Bu örnek, `<typeparam>` parametresini anlatmak için etiketini kullanır `id` .</span><span class="sxs-lookup"><span data-stu-id="72b10-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="72b10-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72b10-113">See also</span></span>

- [<span data-ttu-id="72b10-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="72b10-114">XML Comment Tags</span></span>](index.md)

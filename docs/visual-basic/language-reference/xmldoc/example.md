---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <example> (Visual Basic)'
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 643e06fd24e38123dd2693d671b9ab33da5b413e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787493"
---
# <a name="example-visual-basic"></a><span data-ttu-id="140d0-103">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="140d0-103">\<example> (Visual Basic)</span></span>

<span data-ttu-id="140d0-104">Üye için bir örnek belirtir.</span><span class="sxs-lookup"><span data-stu-id="140d0-104">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="140d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="140d0-105">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="140d0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="140d0-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="140d0-107">Kod örneğinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="140d0-107">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="140d0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="140d0-108">Remarks</span></span>  

 <span data-ttu-id="140d0-109">`<example>`Etiketi, bir yöntemi veya diğer kitaplık üyesini nasıl kullanacağınızı gösteren bir örnek belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="140d0-109">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="140d0-110">Bu genellikle etiketinin kullanılmasını içerir [\<code>](code.md) .</span><span class="sxs-lookup"><span data-stu-id="140d0-110">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="140d0-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="140d0-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="140d0-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="140d0-112">Example</span></span>  

 <span data-ttu-id="140d0-113">Bu örnek, `<example>` alanı kullanmak için bir örnek eklemek için etiketini kullanır `ID` .</span><span class="sxs-lookup"><span data-stu-id="140d0-113">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="140d0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="140d0-114">See also</span></span>

- [<span data-ttu-id="140d0-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="140d0-115">XML Comment Tags</span></span>](index.md)

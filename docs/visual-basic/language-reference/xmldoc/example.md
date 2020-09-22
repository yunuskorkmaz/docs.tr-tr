---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 6e9f63e4d31df7790f51ae4d166b606f2c63f14b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872980"
---
# <a name="example-visual-basic"></a><span data-ttu-id="f44eb-101">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f44eb-101">\<example> (Visual Basic)</span></span>

<span data-ttu-id="f44eb-102">Üye için bir örnek belirtir.</span><span class="sxs-lookup"><span data-stu-id="f44eb-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f44eb-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f44eb-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="f44eb-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f44eb-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="f44eb-105">Kod örneğinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="f44eb-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f44eb-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f44eb-106">Remarks</span></span>  

 <span data-ttu-id="f44eb-107">`<example>`Etiketi, bir yöntemi veya diğer kitaplık üyesini nasıl kullanacağınızı gösteren bir örnek belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f44eb-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="f44eb-108">Bu genellikle etiketinin kullanılmasını içerir [\<code>](code.md) .</span><span class="sxs-lookup"><span data-stu-id="f44eb-108">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="f44eb-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="f44eb-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f44eb-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f44eb-110">Example</span></span>  

 <span data-ttu-id="f44eb-111">Bu örnek, `<example>` alanı kullanmak için bir örnek eklemek için etiketini kullanır `ID` .</span><span class="sxs-lookup"><span data-stu-id="f44eb-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f44eb-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f44eb-112">See also</span></span>

- [<span data-ttu-id="f44eb-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="f44eb-113">XML Comment Tags</span></span>](index.md)

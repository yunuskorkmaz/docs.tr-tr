---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: aa65fed863718f1f00b510f82051a13e764e1b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400156"
---
# <a name="code-visual-basic"></a><span data-ttu-id="2d26d-101">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d26d-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="2d26d-102">Metnin birden çok kod satırı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d26d-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d26d-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2d26d-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d26d-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d26d-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="2d26d-105">Kod olarak işaretlemek için metin.</span><span class="sxs-lookup"><span data-stu-id="2d26d-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d26d-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d26d-106">Remarks</span></span>  
 <span data-ttu-id="2d26d-107">`<code>`Birden çok satırı kod olarak göstermek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2d26d-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="2d26d-108">[\<c>](c.md)Açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2d26d-108">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="2d26d-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="2d26d-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d26d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d26d-110">Example</span></span>  
 <span data-ttu-id="2d26d-111">Bu örnek, \<code> alanı kullanmaya yönelik örnek kodu eklemek için etiketini kullanır `ID` .</span><span class="sxs-lookup"><span data-stu-id="2d26d-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2d26d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d26d-112">See also</span></span>

- [<span data-ttu-id="2d26d-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="2d26d-113">XML Comment Tags</span></span>](index.md)

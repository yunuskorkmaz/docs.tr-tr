---
description: 'Hakkında daha fazla bilgi edinin: <code>(Visual Basic)'
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 80fc0988f60d9d82b9c88734f86b20ebccc80b7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787506"
---
# <a name="code-visual-basic"></a><span data-ttu-id="fa2ef-102">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa2ef-102">\<code> (Visual Basic)</span></span>

<span data-ttu-id="fa2ef-103">Metnin birden çok kod satırı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa2ef-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa2ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa2ef-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa2ef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa2ef-105">Parameters</span></span>  

 `content`  
 <span data-ttu-id="fa2ef-106">Kod olarak işaretlemek için metin.</span><span class="sxs-lookup"><span data-stu-id="fa2ef-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa2ef-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa2ef-107">Remarks</span></span>  

 <span data-ttu-id="fa2ef-108">`<code>`Birden çok satırı kod olarak göstermek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa2ef-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="fa2ef-109">[\<c>](c.md)Açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa2ef-109">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="fa2ef-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="fa2ef-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa2ef-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa2ef-111">Example</span></span>  

 <span data-ttu-id="fa2ef-112">Bu örnek, \<code> alanı kullanmaya yönelik örnek kodu eklemek için etiketini kullanır `ID` .</span><span class="sxs-lookup"><span data-stu-id="fa2ef-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fa2ef-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa2ef-113">See also</span></span>

- [<span data-ttu-id="fa2ef-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="fa2ef-114">XML Comment Tags</span></span>](index.md)

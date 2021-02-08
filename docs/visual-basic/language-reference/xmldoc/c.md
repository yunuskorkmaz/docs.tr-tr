---
description: 'Hakkında daha fazla bilgi edinin: <c> (Visual Basic)'
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 350a5dbf2dee2911c356a7c76a9bafbab35fd71e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787519"
---
# <a name="c-visual-basic"></a><span data-ttu-id="842ed-102">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="842ed-102">\<c> (Visual Basic)</span></span>

<span data-ttu-id="842ed-103">Açıklama içindeki metnin kod olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="842ed-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="842ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="842ed-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="842ed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="842ed-105">Parameters</span></span>  
  
|<span data-ttu-id="842ed-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="842ed-106">Parameter</span></span>|<span data-ttu-id="842ed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="842ed-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="842ed-108">Kod olarak göstermek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="842ed-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="842ed-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="842ed-109">Remarks</span></span>  

 <span data-ttu-id="842ed-110">`<c>`Etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="842ed-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="842ed-111">[\<code>](code.md)Birden çok satırı kod olarak göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="842ed-111">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="842ed-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="842ed-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="842ed-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="842ed-113">Example</span></span>  

 <span data-ttu-id="842ed-114">Bu örnek, `<c>` kod olduğunu göstermek için Özet bölümündeki etiketini kullanır `Counter` .</span><span class="sxs-lookup"><span data-stu-id="842ed-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="842ed-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="842ed-115">See also</span></span>

- [<span data-ttu-id="842ed-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="842ed-116">XML Comment Tags</span></span>](index.md)

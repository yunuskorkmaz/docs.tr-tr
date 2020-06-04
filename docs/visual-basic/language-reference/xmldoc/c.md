---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: c8ba03d9cc01c4751d15c01530c6cbf7d499dc3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400169"
---
# <a name="c-visual-basic"></a><span data-ttu-id="8af4c-101">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8af4c-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="8af4c-102">Açıklama içindeki metnin kod olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8af4c-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af4c-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8af4c-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="8af4c-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8af4c-104">Parameters</span></span>  
  
|<span data-ttu-id="8af4c-105">Parametre</span><span class="sxs-lookup"><span data-stu-id="8af4c-105">Parameter</span></span>|<span data-ttu-id="8af4c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8af4c-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="8af4c-107">Kod olarak göstermek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="8af4c-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8af4c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8af4c-108">Remarks</span></span>  
 <span data-ttu-id="8af4c-109">`<c>`Etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8af4c-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="8af4c-110">[\<code>](code.md)Birden çok satırı kod olarak göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8af4c-110">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="8af4c-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="8af4c-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af4c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8af4c-112">Example</span></span>  
 <span data-ttu-id="8af4c-113">Bu örnek, `<c>` kod olduğunu göstermek için Özet bölümündeki etiketini kullanır `Counter` .</span><span class="sxs-lookup"><span data-stu-id="8af4c-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8af4c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8af4c-114">See also</span></span>

- [<span data-ttu-id="8af4c-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="8af4c-115">XML Comment Tags</span></span>](index.md)

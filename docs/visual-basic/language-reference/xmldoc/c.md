---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348505"
---
# <a name="c-visual-basic"></a><span data-ttu-id="01348-101">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01348-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="01348-102">Açıklama içindeki metnin kod olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="01348-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01348-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01348-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="01348-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01348-104">Parameters</span></span>  
  
|<span data-ttu-id="01348-105">Parametre</span><span class="sxs-lookup"><span data-stu-id="01348-105">Parameter</span></span>|<span data-ttu-id="01348-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01348-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="01348-107">Kod olarak göstermek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="01348-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01348-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01348-108">Remarks</span></span>  
 <span data-ttu-id="01348-109">`<c>` etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="01348-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="01348-110">Birden çok satırı kod olarak göstermek için [\<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="01348-110">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="01348-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="01348-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01348-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="01348-112">Example</span></span>  
 <span data-ttu-id="01348-113">Bu örnek, `Counter` kodun olduğunu göstermek için Özet bölümündeki `<c>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="01348-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="01348-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01348-114">See also</span></span>

- [<span data-ttu-id="01348-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="01348-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 1cbac2162bd39cdc8af9a55dfd6e2f90bc40b08a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354317"
---
# <a name="code-visual-basic"></a><span data-ttu-id="e1d78-101">\<kodu > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1d78-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="e1d78-102">Metnin birden çok kod satırı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1d78-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1d78-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1d78-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1d78-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1d78-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="e1d78-105">Kod olarak işaretlemek için metin.</span><span class="sxs-lookup"><span data-stu-id="e1d78-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1d78-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1d78-106">Remarks</span></span>  
 <span data-ttu-id="e1d78-107">Birden çok satırı kod olarak göstermek için `<code>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1d78-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="e1d78-108">Bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için [\<c >](../../../visual-basic/language-reference/xmldoc/c.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1d78-108">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="e1d78-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="e1d78-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1d78-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1d78-110">Example</span></span>  
 <span data-ttu-id="e1d78-111">Bu örnek, `ID` alanının kullanılmasına ilişkin örnek kodu eklemek için \<Code > etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1d78-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e1d78-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1d78-112">See also</span></span>

- [<span data-ttu-id="e1d78-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="e1d78-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

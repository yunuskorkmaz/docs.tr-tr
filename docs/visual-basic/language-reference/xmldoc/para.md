---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: aa4e4c14717b69b9ca4595e20c768a2b91aac1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524731"
---
# <a name="para-visual-basic"></a><span data-ttu-id="96f90-102">\<para > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96f90-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="96f90-103">İçeriğin bir paragraf olarak biçimlendirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="96f90-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f90-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96f90-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="96f90-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96f90-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="96f90-106">Paragrafın metni.</span><span class="sxs-lookup"><span data-stu-id="96f90-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96f90-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96f90-107">Remarks</span></span>  
 <span data-ttu-id="96f90-108">@No__t_0 etiketi, [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md)veya [\<returns](../../../visual-basic/language-reference/xmldoc/returns.md)> gibi bir etiket içinde kullanım içindir ve metne yapı eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="96f90-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="96f90-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="96f90-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96f90-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="96f90-110">Example</span></span>  
 <span data-ttu-id="96f90-111">Bu örnek, `UpdateRecord` yönteminin açıklamalar bölümünü iki paragrafa bölmek için `<para>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="96f90-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="96f90-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96f90-112">See also</span></span>

- [<span data-ttu-id="96f90-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="96f90-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

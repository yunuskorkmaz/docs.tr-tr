---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <para> (Visual Basic)'
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 51dd9ff300d980b4c0576566cad5d17375889ba1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740775"
---
# <a name="para-visual-basic"></a><span data-ttu-id="c3aca-103">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3aca-103">\<para> (Visual Basic)</span></span>

<span data-ttu-id="c3aca-104">İçeriğin bir paragraf olarak biçimlendirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3aca-104">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3aca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3aca-105">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3aca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3aca-106">Parameters</span></span>  

 `content`  
 <span data-ttu-id="c3aca-107">Paragrafın metni.</span><span class="sxs-lookup"><span data-stu-id="c3aca-107">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3aca-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3aca-108">Remarks</span></span>  

 <span data-ttu-id="c3aca-109">`<para>`Etiketi,, veya gibi bir etiket içinde kullanım içindir [\<summary>](summary.md) [\<remarks>](remarks.md) [\<returns>](returns.md) ve metne yapı eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3aca-109">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="c3aca-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="c3aca-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3aca-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3aca-111">Example</span></span>  

 <span data-ttu-id="c3aca-112">Bu örnek, `<para>` yöntemi için açıklamalar bölümünü iki paragrafa bölmek için etiketini kullanır `UpdateRecord` .</span><span class="sxs-lookup"><span data-stu-id="c3aca-112">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c3aca-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3aca-113">See also</span></span>

- [<span data-ttu-id="c3aca-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="c3aca-114">XML Comment Tags</span></span>](index.md)

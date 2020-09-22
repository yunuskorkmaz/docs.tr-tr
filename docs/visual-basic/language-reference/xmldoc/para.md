---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0846efbaf2afacd3d0783a2d2d8e4dae3fc8b715
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872707"
---
# <a name="para-visual-basic"></a><span data-ttu-id="3e8d0-101">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e8d0-101">\<para> (Visual Basic)</span></span>

<span data-ttu-id="3e8d0-102">İçeriğin bir paragraf olarak biçimlendirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e8d0-102">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e8d0-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e8d0-103">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e8d0-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e8d0-104">Parameters</span></span>  

 `content`  
 <span data-ttu-id="3e8d0-105">Paragrafın metni.</span><span class="sxs-lookup"><span data-stu-id="3e8d0-105">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e8d0-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e8d0-106">Remarks</span></span>  

 <span data-ttu-id="3e8d0-107">`<para>`Etiketi,, veya gibi bir etiket içinde kullanım içindir [\<summary>](summary.md) [\<remarks>](remarks.md) [\<returns>](returns.md) ve metne yapı eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e8d0-107">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="3e8d0-108">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="3e8d0-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e8d0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e8d0-109">Example</span></span>  

 <span data-ttu-id="3e8d0-110">Bu örnek, `<para>` yöntemi için açıklamalar bölümünü iki paragrafa bölmek için etiketini kullanır `UpdateRecord` .</span><span class="sxs-lookup"><span data-stu-id="3e8d0-110">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3e8d0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e8d0-111">See also</span></span>

- [<span data-ttu-id="3e8d0-112">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="3e8d0-112">XML Comment Tags</span></span>](index.md)

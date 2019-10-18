---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: b220c2a9aa544413c3692485f6c1eb2b64e54389
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524687"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="30cb1-102">\<returns > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30cb1-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="30cb1-103">Özelliğin veya işlevin dönüş değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="30cb1-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30cb1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30cb1-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="30cb1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30cb1-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="30cb1-106">Dönüş değerinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="30cb1-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30cb1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30cb1-107">Remarks</span></span>  
 <span data-ttu-id="30cb1-108">Dönüş değerini anlatmak için bir yöntem bildirimi açıklamasında `<returns>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="30cb1-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="30cb1-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="30cb1-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30cb1-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="30cb1-110">Example</span></span>  
 <span data-ttu-id="30cb1-111">Bu örnek, `DoesRecordExist` işlevinin döndürdüğü şeyi açıklamak için `<returns>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="30cb1-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="30cb1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30cb1-112">See also</span></span>

- [<span data-ttu-id="30cb1-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="30cb1-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

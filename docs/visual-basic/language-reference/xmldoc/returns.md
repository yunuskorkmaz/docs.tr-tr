---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 37b110cc6e12f11196d2a1c5cc6026d87b453626
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866398"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="1ac87-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ac87-101">\<returns> (Visual Basic)</span></span>

<span data-ttu-id="1ac87-102">Özelliğin veya işlevin dönüş değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ac87-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac87-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ac87-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ac87-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ac87-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="1ac87-105">Dönüş değerinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="1ac87-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ac87-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ac87-106">Remarks</span></span>  

 <span data-ttu-id="1ac87-107">`<returns>`Dönüş değerini anlatmak için bir yöntem bildirimi açıklamasında etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ac87-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="1ac87-108">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="1ac87-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ac87-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ac87-109">Example</span></span>  

 <span data-ttu-id="1ac87-110">Bu örnek, `<returns>` işlevin ne döndürdüğünü açıklamak için etiketini kullanır `DoesRecordExist` .</span><span class="sxs-lookup"><span data-stu-id="1ac87-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1ac87-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ac87-111">See also</span></span>

- [<span data-ttu-id="1ac87-112">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="1ac87-112">XML Comment Tags</span></span>](index.md)

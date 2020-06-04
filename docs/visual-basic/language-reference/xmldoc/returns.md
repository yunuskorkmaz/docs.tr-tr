---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: edbc374332bdcd67b385ac3d061045664e942460
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400001"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="8b9df-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b9df-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="8b9df-102">Özelliğin veya işlevin dönüş değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b9df-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b9df-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8b9df-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b9df-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b9df-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="8b9df-105">Dönüş değerinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="8b9df-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b9df-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b9df-106">Remarks</span></span>  
 <span data-ttu-id="8b9df-107">`<returns>`Dönüş değerini anlatmak için bir yöntem bildirimi açıklamasında etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b9df-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="8b9df-108">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="8b9df-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b9df-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b9df-109">Example</span></span>  
 <span data-ttu-id="8b9df-110">Bu örnek, `<returns>` işlevin ne döndürdüğünü açıklamak için etiketini kullanır `DoesRecordExist` .</span><span class="sxs-lookup"><span data-stu-id="8b9df-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="8b9df-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b9df-111">See also</span></span>

- [<span data-ttu-id="8b9df-112">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="8b9df-112">XML Comment Tags</span></span>](index.md)

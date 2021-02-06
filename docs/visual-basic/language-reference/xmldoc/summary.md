---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <summary> (Visual Basic)'
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 4d4b1ecf0fa054eb625c1a3cf09c1cab4e661ef2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640296"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="5f207-103">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f207-103">\<summary> (Visual Basic)</span></span>

<span data-ttu-id="5f207-104">Üyenin özetini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f207-104">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f207-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f207-105">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f207-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f207-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="5f207-107">Nesnenin Özeti.</span><span class="sxs-lookup"><span data-stu-id="5f207-107">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f207-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f207-108">Remarks</span></span>  

 <span data-ttu-id="5f207-109">`<summary>`Bir tür veya tür üyesini anlatmak için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f207-109">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="5f207-110">[\<remarks>](remarks.md)Bir tür açıklamasına ek bilgi eklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f207-110">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="5f207-111">Etiket metni, `<summary>` IntelliSense 'deki türle ilgili tek bilgi kaynağıdır ve ayrıca nesne tarayıcısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f207-111">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="5f207-112">Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="5f207-112">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="5f207-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="5f207-113">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f207-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f207-114">Example</span></span>  

 <span data-ttu-id="5f207-115">Bu örnek, `<summary>` `ResetCounter` yöntemini ve özelliğini anlatmak için etiketini kullanır `Counter` .</span><span class="sxs-lookup"><span data-stu-id="5f207-115">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5f207-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f207-116">See also</span></span>

- [<span data-ttu-id="5f207-117">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="5f207-117">XML Comment Tags</span></span>](index.md)

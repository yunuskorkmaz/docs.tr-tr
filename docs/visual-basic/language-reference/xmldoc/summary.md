---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 471d3ddb5cf5a234cb77de6d1d93309faf754359
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865842"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="67483-101">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67483-101">\<summary> (Visual Basic)</span></span>

<span data-ttu-id="67483-102">Üyenin özetini belirtir.</span><span class="sxs-lookup"><span data-stu-id="67483-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67483-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67483-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="67483-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67483-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="67483-105">Nesnenin Özeti.</span><span class="sxs-lookup"><span data-stu-id="67483-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67483-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67483-106">Remarks</span></span>  

 <span data-ttu-id="67483-107">`<summary>`Bir tür veya tür üyesini anlatmak için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="67483-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="67483-108">[\<remarks>](remarks.md)Bir tür açıklamasına ek bilgi eklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="67483-108">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="67483-109">Etiket metni, `<summary>` IntelliSense 'deki türle ilgili tek bilgi kaynağıdır ve ayrıca nesne tarayıcısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="67483-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="67483-110">Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="67483-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="67483-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="67483-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67483-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="67483-112">Example</span></span>  

 <span data-ttu-id="67483-113">Bu örnek, `<summary>` `ResetCounter` yöntemini ve özelliğini anlatmak için etiketini kullanır `Counter` .</span><span class="sxs-lookup"><span data-stu-id="67483-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="67483-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67483-114">See also</span></span>

- [<span data-ttu-id="67483-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="67483-115">XML Comment Tags</span></span>](index.md)

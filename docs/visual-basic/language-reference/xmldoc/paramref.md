---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 3ca08016d3cef0c44e4f3c0bd0d017628eda606d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400053"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="a9387-101">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9387-101">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="a9387-102">Bir sözcüğü parametre olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="a9387-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9387-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a9387-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9387-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9387-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a9387-105">Başvurabileceğiniz parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="a9387-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="a9387-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="a9387-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9387-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9387-107">Remarks</span></span>  
 <span data-ttu-id="a9387-108">Etiketi, bir `<paramref>` sözcüğün bir parametre olduğunu göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9387-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="a9387-109">XML dosyası bu parametreyi farklı bir şekilde biçimlendirmek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a9387-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="a9387-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="a9387-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9387-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9387-111">Example</span></span>  
 <span data-ttu-id="a9387-112">Bu örnek, `<paramref>` parametresine başvurmak için etiketini kullanır `id` .</span><span class="sxs-lookup"><span data-stu-id="a9387-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a9387-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9387-113">See also</span></span>

- [<span data-ttu-id="a9387-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="a9387-114">XML Comment Tags</span></span>](index.md)

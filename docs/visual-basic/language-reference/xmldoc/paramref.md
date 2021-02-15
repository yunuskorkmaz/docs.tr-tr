---
description: 'Hakkında daha fazla bilgi edinin: <paramref> (Visual Basic)'
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 0ce748213e26c258b290828c42454b0e7fd316f1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456841"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="6555f-102">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6555f-102">\<paramref> (Visual Basic)</span></span>

<span data-ttu-id="6555f-103">Bir sözcüğü parametre olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="6555f-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6555f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6555f-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6555f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6555f-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="6555f-106">Başvurabileceğiniz parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="6555f-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="6555f-107">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="6555f-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6555f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6555f-108">Remarks</span></span>  

 <span data-ttu-id="6555f-109">Etiketi, bir `<paramref>` sözcüğün bir parametre olduğunu göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6555f-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="6555f-110">XML dosyası bu parametreyi farklı bir şekilde biçimlendirmek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="6555f-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="6555f-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="6555f-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6555f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6555f-112">Example</span></span>  

 <span data-ttu-id="6555f-113">Bu örnek, `<paramref>` parametresine başvurmak için etiketini kullanır `id` .</span><span class="sxs-lookup"><span data-stu-id="6555f-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6555f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6555f-114">See also</span></span>

- [<span data-ttu-id="6555f-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="6555f-115">XML Comment Tags</span></span>](index.md)

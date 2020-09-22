---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: d7aacc5faea22f9c5a4b865a32c832154fe624c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872608"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="7d9a5-101">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d9a5-101">\<paramref> (Visual Basic)</span></span>

<span data-ttu-id="7d9a5-102">Bir sözcüğü parametre olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="7d9a5-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d9a5-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d9a5-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d9a5-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d9a5-104">Parameters</span></span>  

 `name`  
 <span data-ttu-id="7d9a5-105">Başvurabileceğiniz parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="7d9a5-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="7d9a5-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="7d9a5-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d9a5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d9a5-107">Remarks</span></span>  

 <span data-ttu-id="7d9a5-108">Etiketi, bir `<paramref>` sözcüğün bir parametre olduğunu göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d9a5-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="7d9a5-109">XML dosyası bu parametreyi farklı bir şekilde biçimlendirmek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="7d9a5-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="7d9a5-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="7d9a5-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d9a5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d9a5-111">Example</span></span>  

 <span data-ttu-id="7d9a5-112">Bu örnek, `<paramref>` parametresine başvurmak için etiketini kullanır `id` .</span><span class="sxs-lookup"><span data-stu-id="7d9a5-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="7d9a5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d9a5-113">See also</span></span>

- [<span data-ttu-id="7d9a5-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="7d9a5-114">XML Comment Tags</span></span>](index.md)

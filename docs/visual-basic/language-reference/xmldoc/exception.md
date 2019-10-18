---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 16ffb4f6b57dabb3650376c913a7d7608a00646d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523926"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="48961-102">\<exception > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48961-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="48961-103">Hangi özel durumların atılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="48961-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48961-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48961-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="48961-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48961-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="48961-106">Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru.</span><span class="sxs-lookup"><span data-stu-id="48961-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="48961-107">Derleyici verilen özel durumun var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir.</span><span class="sxs-lookup"><span data-stu-id="48961-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="48961-108">`member` çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="48961-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="48961-109">Bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="48961-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48961-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48961-110">Remarks</span></span>  
 <span data-ttu-id="48961-111">Hangi özel durumların atılamayacağını belirtmek için `<exception>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="48961-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="48961-112">Bu etiket bir yöntem tanımına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="48961-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="48961-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="48961-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48961-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="48961-114">Example</span></span>  
 <span data-ttu-id="48961-115">Bu örnek, `IntDivide` işlevinin oluşturabildiğini belirten bir özel durumu tanımlayan `<exception>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="48961-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="48961-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48961-116">See also</span></span>

- [<span data-ttu-id="48961-117">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="48961-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

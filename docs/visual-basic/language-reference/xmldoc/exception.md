---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e3f386d2a1e15ea3e1519d6e1e5e31c34c73fb99
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872895"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="502c0-101">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="502c0-101">\<exception> (Visual Basic)</span></span>

<span data-ttu-id="502c0-102">Hangi özel durumların atılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="502c0-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="502c0-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="502c0-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="502c0-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="502c0-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="502c0-105">Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru.</span><span class="sxs-lookup"><span data-stu-id="502c0-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="502c0-106">Derleyici verilen özel durumun var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="502c0-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="502c0-107">`member` Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="502c0-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="502c0-108">Bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="502c0-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="502c0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="502c0-109">Remarks</span></span>  

 <span data-ttu-id="502c0-110">`<exception>`Hangi özel durumların atılamayacağını belirtmek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="502c0-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="502c0-111">Bu etiket bir yöntem tanımına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="502c0-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="502c0-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="502c0-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="502c0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="502c0-113">Example</span></span>  

 <span data-ttu-id="502c0-114">Bu örnek, `<exception>` işlevin oluşturabildiğini belirten bir özel durumu tanımlayan etiketini kullanır `IntDivide` .</span><span class="sxs-lookup"><span data-stu-id="502c0-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="502c0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="502c0-115">See also</span></span>

- [<span data-ttu-id="502c0-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="502c0-116">XML Comment Tags</span></span>](index.md)

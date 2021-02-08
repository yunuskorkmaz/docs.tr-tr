---
description: 'Hakkında daha fazla bilgi edinin: <exception> (Visual Basic)'
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 14b7f78dd2521f7d5b3d62f635baa5b50969afa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787480"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="bda24-102">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bda24-102">\<exception> (Visual Basic)</span></span>

<span data-ttu-id="bda24-103">Hangi özel durumların atılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bda24-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bda24-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bda24-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="bda24-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bda24-105">Parameters</span></span>  

 `member`  
 <span data-ttu-id="bda24-106">Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru.</span><span class="sxs-lookup"><span data-stu-id="bda24-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="bda24-107">Derleyici verilen özel durumun var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="bda24-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="bda24-108">`member` Çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="bda24-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="bda24-109">Bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="bda24-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bda24-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bda24-110">Remarks</span></span>  

 <span data-ttu-id="bda24-111">`<exception>`Hangi özel durumların atılamayacağını belirtmek için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bda24-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="bda24-112">Bu etiket bir yöntem tanımına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bda24-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="bda24-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="bda24-113">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bda24-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="bda24-114">Example</span></span>  

 <span data-ttu-id="bda24-115">Bu örnek, `<exception>` işlevin oluşturabildiğini belirten bir özel durumu tanımlayan etiketini kullanır `IntDivide` .</span><span class="sxs-lookup"><span data-stu-id="bda24-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="bda24-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bda24-116">See also</span></span>

- [<span data-ttu-id="bda24-117">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="bda24-117">XML Comment Tags</span></span>](index.md)

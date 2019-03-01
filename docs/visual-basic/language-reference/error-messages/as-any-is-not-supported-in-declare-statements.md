---
title: "'Declare' deyimlerinde 'As Any' desteklenmiyor"
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: b3fb3f208f3396f454388ec0c10406815fa957d8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974802"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a><span data-ttu-id="59e87-102">'Declare' deyimlerinde 'As Any' desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="59e87-102">'As Any' is not supported in 'Declare' statements</span></span>
<span data-ttu-id="59e87-103">`Any` Veri türü ile kullanıldığında `Declare` deyimleri Visual Basic 6.0 ve önceki sürümlerinde her türden veriyi içerebilir bağımsız değişkenleri kullanımına izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="59e87-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="59e87-104">Bunu yapar ve Visual Basic destekler, ancak aşırı `Any` veri türü geçersiz.</span><span class="sxs-lookup"><span data-stu-id="59e87-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="59e87-105">**Hata Kimliği:** BC30828</span><span class="sxs-lookup"><span data-stu-id="59e87-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="59e87-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="59e87-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="59e87-107">Kullanmak istediğiniz belirli türdeki parametreleri bildirme; Örneğin.</span><span class="sxs-lookup"><span data-stu-id="59e87-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2.  <span data-ttu-id="59e87-108">Kullanım <xref:System.Runtime.InteropServices.MarshalAsAttribute> belirtmek için özniteliği `As Any` olduğunda `Void*` çağrılan yordam tarafından beklenir.</span><span class="sxs-lookup"><span data-stu-id="59e87-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a><span data-ttu-id="59e87-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59e87-109">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="59e87-110">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="59e87-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="59e87-111">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="59e87-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="59e87-112">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="59e87-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)

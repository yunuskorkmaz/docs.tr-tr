---
title: '#ExternalSource yönergesi'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586597"
---
# <a name="externalsource-directive"></a><span data-ttu-id="db613-102">#ExternalSource Yönergesi</span><span class="sxs-lookup"><span data-stu-id="db613-102">#ExternalSource Directive</span></span>
<span data-ttu-id="db613-103">Belirli satırları kaynak kodu ve metin kaynağına dış arasında bir eşleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="db613-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db613-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db613-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="db613-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="db613-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="db613-106">Dış kaynak yolu.</span><span class="sxs-lookup"><span data-stu-id="db613-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="db613-107">Dış kaynak ilk satırının satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="db613-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="db613-108">Dış kaynak hatanın oluştuğu satır.</span><span class="sxs-lookup"><span data-stu-id="db613-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="db613-109">Sonlandırır `#ExternalSource` bloğu.</span><span class="sxs-lookup"><span data-stu-id="db613-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db613-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db613-110">Remarks</span></span>  
 <span data-ttu-id="db613-111">Bu yönerge, yalnızca derleme ve hata ayıklayıcısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db613-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="db613-112">Bir kaynak dosyası belirli satırları kaynak dosyasında kod ve metin kaynağına .aspx dosyası gibi dış arasında bir eşleme belirtmek dış kaynak yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="db613-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="db613-113">Belirtilen kaynak kodunda derleme sırasında bir hatayla karşılaşılmazsa, dış kaynak gelen olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="db613-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="db613-114">Dış kaynak yönergeleri derleme üzerinde hiçbir etkisi yoktur ve iç içe olamaz.</span><span class="sxs-lookup"><span data-stu-id="db613-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="db613-115">Yalnızca uygulama tarafından bunlar iç kullanım için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="db613-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db613-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db613-116">See Also</span></span>  
 [<span data-ttu-id="db613-117">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="db613-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

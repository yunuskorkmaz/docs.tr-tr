---
title: '#ExternalSource yönergesi (Visual Basic)'
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
ms.openlocfilehash: ac7096e998dd8d2a416dc739e1d7625e1abff7a6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696833"
---
# <a name="externalsource-directive"></a><span data-ttu-id="9138f-102">#ExternalSource Yönergesi</span><span class="sxs-lookup"><span data-stu-id="9138f-102">#ExternalSource Directive</span></span>
<span data-ttu-id="9138f-103">Kaynak kodunun belirli satırları ve kaynağın dış metni arasındaki eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="9138f-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9138f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9138f-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="9138f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9138f-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="9138f-106">Dış kaynağın yolu.</span><span class="sxs-lookup"><span data-stu-id="9138f-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="9138f-107">Dış kaynağın ilk satırının satır numarası.</span><span class="sxs-lookup"><span data-stu-id="9138f-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="9138f-108">Dış kaynakta Hatanın gerçekleştiği satır.</span><span class="sxs-lookup"><span data-stu-id="9138f-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="9138f-109">@No__t-0 bloğunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="9138f-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9138f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9138f-110">Remarks</span></span>  
 <span data-ttu-id="9138f-111">Bu yönerge yalnızca derleyici ve hata ayıklayıcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9138f-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="9138f-112">Kaynak dosya, kaynak dosyadaki belirli kod satırları ve bir. aspx dosyası gibi, kaynağın harici metni arasındaki eşlemeyi gösteren dış kaynak yönergeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9138f-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="9138f-113">Derleme sırasında belirlenen kaynak kodunda hatalarla karşılaşılırsa, bunlar dış kaynaktan geldiği şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9138f-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="9138f-114">Dış kaynak yönergelerinin derleme üzerinde hiçbir etkisi yoktur ve iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="9138f-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="9138f-115">Bunlar yalnızca uygulama tarafından dahili kullanım için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9138f-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9138f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9138f-116">See also</span></span>

- [<span data-ttu-id="9138f-117">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="9138f-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

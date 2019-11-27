---
title: '#ExternalSource Yönergesi'
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
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343825"
---
# <a name="externalsource-directive"></a><span data-ttu-id="a2ddd-102">#ExternalSource Yönergesi</span><span class="sxs-lookup"><span data-stu-id="a2ddd-102">#ExternalSource Directive</span></span>

<span data-ttu-id="a2ddd-103">Kaynak kodunun belirli satırları ve kaynağın dış metni arasındaki eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ddd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2ddd-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="a2ddd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a2ddd-105">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="a2ddd-106">Dış kaynağın yolu.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="a2ddd-107">Dış kaynağın ilk satırının satır numarası.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="a2ddd-108">Dış kaynakta Hatanın gerçekleştiği satır.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="a2ddd-109">`#ExternalSource` bloğunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2ddd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2ddd-110">Remarks</span></span>  

 <span data-ttu-id="a2ddd-111">Bu yönerge yalnızca derleyici ve hata ayıklayıcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="a2ddd-112">Kaynak dosya, kaynak dosyadaki belirli kod satırları ve bir. aspx dosyası gibi, kaynağın harici metni arasındaki eşlemeyi gösteren dış kaynak yönergeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="a2ddd-113">Derleme sırasında belirlenen kaynak kodunda hatalarla karşılaşılırsa, bunlar dış kaynaktan geldiği şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="a2ddd-114">Dış kaynak yönergelerinin derleme üzerinde hiçbir etkisi yoktur ve iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="a2ddd-115">Bunlar yalnızca uygulama tarafından dahili kullanım için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ddd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2ddd-116">See also</span></span>

- [<span data-ttu-id="a2ddd-117">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="a2ddd-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

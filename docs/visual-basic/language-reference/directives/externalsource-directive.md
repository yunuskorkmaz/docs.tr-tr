---
description: 'Daha fazla bilgi edinin: #ExternalSource yönergesi'
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
ms.openlocfilehash: 1f2e73aa152fbe2d97edcde912626696faacd5af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797243"
---
# <a name="externalsource-directive"></a><span data-ttu-id="7592b-103">#ExternalSource Yönergesi</span><span class="sxs-lookup"><span data-stu-id="7592b-103">#ExternalSource Directive</span></span>

<span data-ttu-id="7592b-104">Kaynak kodunun belirli satırları ve kaynağın dış metni arasındaki eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7592b-104">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7592b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7592b-105">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="7592b-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7592b-106">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="7592b-107">Dış kaynağın yolu.</span><span class="sxs-lookup"><span data-stu-id="7592b-107">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="7592b-108">Dış kaynağın ilk satırının satır numarası.</span><span class="sxs-lookup"><span data-stu-id="7592b-108">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="7592b-109">Dış kaynakta Hatanın gerçekleştiği satır.</span><span class="sxs-lookup"><span data-stu-id="7592b-109">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="7592b-110">Bloğu sonlandırır `#ExternalSource` .</span><span class="sxs-lookup"><span data-stu-id="7592b-110">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7592b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7592b-111">Remarks</span></span>  

 <span data-ttu-id="7592b-112">Bu yönerge yalnızca derleyici ve hata ayıklayıcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7592b-112">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="7592b-113">Kaynak dosya, kaynak dosyadaki belirli kod satırları ve bir. aspx dosyası gibi, kaynağın harici metni arasındaki eşlemeyi gösteren dış kaynak yönergeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7592b-113">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="7592b-114">Derleme sırasında belirlenen kaynak kodunda hatalarla karşılaşılırsa, bunlar dış kaynaktan geldiği şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7592b-114">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="7592b-115">Dış kaynak yönergelerinin derleme üzerinde hiçbir etkisi yoktur ve iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="7592b-115">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="7592b-116">Bunlar yalnızca uygulama tarafından dahili kullanım için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7592b-116">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7592b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7592b-117">See also</span></span>

- [<span data-ttu-id="7592b-118">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="7592b-118">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)

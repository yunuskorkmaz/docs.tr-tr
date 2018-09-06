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
ms.openlocfilehash: dcde8507eb033d0a47d5c5d3fa36176cd63b0856
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861799"
---
# <a name="externalsource-directive"></a><span data-ttu-id="aac95-102">#ExternalSource Yönergesi</span><span class="sxs-lookup"><span data-stu-id="aac95-102">#ExternalSource Directive</span></span>
<span data-ttu-id="aac95-103">Belirli bir kaynak kodu satırlarını ve dış kaynak metin arasındaki eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="aac95-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aac95-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aac95-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="aac95-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="aac95-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="aac95-106">Dış kaynak yolu.</span><span class="sxs-lookup"><span data-stu-id="aac95-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="aac95-107">Dış kaynağı ilk satırının satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="aac95-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="aac95-108">Dış kaynağında hatanın oluştuğu satırı.</span><span class="sxs-lookup"><span data-stu-id="aac95-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="aac95-109">Sonlandırır `#ExternalSource` blok.</span><span class="sxs-lookup"><span data-stu-id="aac95-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aac95-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aac95-110">Remarks</span></span>  
 <span data-ttu-id="aac95-111">Bu yönerge, yalnızca derleyici ve hata ayıklayıcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aac95-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="aac95-112">Kaynak dosyada kodun belirli satırlarını ve dış .aspx dosyası gibi bir kaynak metin arasındaki eşlemeyi belirtmek dış kaynak yönergelerini, bir kaynak dosyası içerebilir.</span><span class="sxs-lookup"><span data-stu-id="aac95-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="aac95-113">Belirtilen kaynak kodunda derleme sırasında bir hatayla karşılaşılmazsa, bir dış kaynaktan gelen olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="aac95-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="aac95-114">Dış kaynak yönergeleri derleme üzerinde hiçbir etkisi yoktur ve iç içe olamaz.</span><span class="sxs-lookup"><span data-stu-id="aac95-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="aac95-115">Bunlar yalnızca uygulama tarafından iç kullanım için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aac95-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac95-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aac95-116">See Also</span></span>  
 [<span data-ttu-id="aac95-117">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="aac95-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

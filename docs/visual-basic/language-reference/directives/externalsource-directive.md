---
title: "#<a name=\"externalsource-directive\"></a>ExternalSource yönergesi"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="externalsource-directive"></a><span data-ttu-id="d9a3a-102">#ExternalSource Yönergesi</span><span class="sxs-lookup"><span data-stu-id="d9a3a-102">#ExternalSource Directive</span></span>
<span data-ttu-id="d9a3a-103">Belirli satırları kaynak kodu ve metin kaynağına dış arasında bir eşleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9a3a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9a3a-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="d9a3a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d9a3a-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="d9a3a-106">Dış kaynak yolu.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="d9a3a-107">Dış kaynak ilk satırının satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="d9a3a-108">Dış kaynak hatanın oluştuğu satır.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="d9a3a-109">Sonlandırır `#ExternalSource` bloğu.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9a3a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9a3a-110">Remarks</span></span>  
 <span data-ttu-id="d9a3a-111">Bu yönerge, yalnızca derleme ve hata ayıklayıcısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="d9a3a-112">Bir kaynak dosyası belirli satırları kaynak dosyasında kod ve metin kaynağına .aspx dosyası gibi dış arasında bir eşleme belirtmek dış kaynak yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="d9a3a-113">Belirtilen kaynak kodunda derleme sırasında bir hatayla karşılaşılmazsa, dış kaynak gelen olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="d9a3a-114">Dış kaynak yönergeleri derleme üzerinde hiçbir etkisi yoktur ve iç içe olamaz.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="d9a3a-115">Yalnızca uygulama tarafından bunlar iç kullanım için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9a3a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9a3a-116">See Also</span></span>  
 [<span data-ttu-id="d9a3a-117">Koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="d9a3a-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

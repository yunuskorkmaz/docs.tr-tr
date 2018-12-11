---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 21c708ef632cc0ed923713cd49e22d44848b4db3
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131150"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="927c0-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="927c0-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="927c0-103">Derleme sırasında telif hakkı başlığının ve bilgi iletilerinin görüntülenmesini bastırır.</span><span class="sxs-lookup"><span data-stu-id="927c0-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="927c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="927c0-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="927c0-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="927c0-105">Remarks</span></span>  
 <span data-ttu-id="927c0-106">Belirtirseniz `-nologo`, derleyici bir telif hakkı başlık göstermez.</span><span class="sxs-lookup"><span data-stu-id="927c0-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="927c0-107">Varsayılan olarak, `-nologo` etkili değildir.</span><span class="sxs-lookup"><span data-stu-id="927c0-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="927c0-108">`-nologo` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="927c0-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="927c0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="927c0-109">Example</span></span>  
 <span data-ttu-id="927c0-110">Aşağıdaki kod derlenir `T2.vb` ve telif hakkı başlığını göstermez.</span><span class="sxs-lookup"><span data-stu-id="927c0-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="927c0-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="927c0-111">See Also</span></span>  
 [<span data-ttu-id="927c0-112">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="927c0-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="927c0-113">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="927c0-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

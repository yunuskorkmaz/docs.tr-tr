---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e5eb9db7af861a8439b47adb8f5e515331fae6e
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="99023-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99023-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="99023-103">Telif hakkı başlığını ve bilgilendirici iletileri görüntülemeyi derleme sırasında gizler.</span><span class="sxs-lookup"><span data-stu-id="99023-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99023-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99023-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="99023-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99023-105">Remarks</span></span>  
 <span data-ttu-id="99023-106">Belirtirseniz `-nologo`, Derleyici telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="99023-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="99023-107">Varsayılan olarak, `-nologo` etkili değildir.</span><span class="sxs-lookup"><span data-stu-id="99023-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99023-108">`-nologo` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99023-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99023-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="99023-109">Example</span></span>  
 <span data-ttu-id="99023-110">Aşağıdaki kod derlerken `T2.vb` ve telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="99023-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="99023-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99023-111">See Also</span></span>  
 [<span data-ttu-id="99023-112">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="99023-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="99023-113">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="99023-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: /nologo (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c2c7e7a111a3763d7463f67c2d984955da33bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nologo-visual-basic"></a><span data-ttu-id="1cf6c-102">/nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cf6c-102">/nologo (Visual Basic)</span></span>
<span data-ttu-id="1cf6c-103">Telif hakkı başlığını ve bilgilendirici iletileri görüntülemeyi derleme sırasında gizler.</span><span class="sxs-lookup"><span data-stu-id="1cf6c-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cf6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cf6c-104">Syntax</span></span>  
  
```  
/nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="1cf6c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1cf6c-105">Remarks</span></span>  
 <span data-ttu-id="1cf6c-106">Belirtirseniz `/nologo`, Derleyici telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="1cf6c-106">If you specify `/nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="1cf6c-107">Varsayılan olarak, `/nologo` etkili değildir.</span><span class="sxs-lookup"><span data-stu-id="1cf6c-107">By default, `/nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cf6c-108">`/nologo` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1cf6c-108">The `/nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cf6c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cf6c-109">Example</span></span>  
 <span data-ttu-id="1cf6c-110">Aşağıdaki kod derlerken `T2.vb` ve telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="1cf6c-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cf6c-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1cf6c-111">See Also</span></span>  
 [<span data-ttu-id="1cf6c-112">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="1cf6c-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1cf6c-113">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="1cf6c-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

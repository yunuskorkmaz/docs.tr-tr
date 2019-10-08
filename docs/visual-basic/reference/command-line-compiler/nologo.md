---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: bb64a468f67745b80b47b42c4fac18852279035d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005429"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="3d356-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d356-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="3d356-103">Derleme sırasında telif hakkı başlığının ve bilgilendirici mesajların görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="3d356-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d356-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d356-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="3d356-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d356-105">Remarks</span></span>  
 <span data-ttu-id="3d356-106">@No__t-0 belirtirseniz, derleyici bir telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="3d356-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="3d356-107">Varsayılan olarak, `-nologo` geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="3d356-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d356-108">@No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d356-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d356-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d356-109">Example</span></span>  
 <span data-ttu-id="3d356-110">Aşağıdaki kod `T2.vb` derler ve bir telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="3d356-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d356-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d356-111">See also</span></span>

- [<span data-ttu-id="3d356-112">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3d356-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3d356-113">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3d356-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

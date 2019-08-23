---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 07e1718554b158635b9d8b04958834e804e1fe9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964385"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="d1c66-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1c66-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="d1c66-103">Derleme sırasında telif hakkı başlığının ve bilgilendirici mesajların görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="d1c66-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1c66-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="d1c66-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1c66-105">Remarks</span></span>  
 <span data-ttu-id="d1c66-106">Belirtirseniz `-nologo`, derleyici bir telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="d1c66-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="d1c66-107">Varsayılan `-nologo` olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="d1c66-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1c66-108">Bu `-nologo` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1c66-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1c66-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1c66-109">Example</span></span>  
 <span data-ttu-id="d1c66-110">Aşağıdaki kod, bir `T2.vb` telif hakkı başlığını derler ve göstermez.</span><span class="sxs-lookup"><span data-stu-id="d1c66-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1c66-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1c66-111">See also</span></span>

- [<span data-ttu-id="d1c66-112">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d1c66-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d1c66-113">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d1c66-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

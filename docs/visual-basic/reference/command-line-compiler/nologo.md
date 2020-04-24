---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 03dc98c45a894304a67765c3e49cd19bbb089c8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335429"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="457a1-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="457a1-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="457a1-103">Derleme sırasında telif hakkı başlığının ve bilgilendirici mesajların görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="457a1-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="457a1-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="457a1-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="457a1-105">Remarks</span></span>  
 <span data-ttu-id="457a1-106">Belirtirseniz `-nologo`, derleyici bir telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="457a1-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="457a1-107">Varsayılan `-nologo` olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="457a1-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="457a1-108">Bu `-nologo` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="457a1-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="457a1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="457a1-109">Example</span></span>  
 <span data-ttu-id="457a1-110">Aşağıdaki kod, bir `T2.vb` telif hakkı başlığını derler ve göstermez.</span><span class="sxs-lookup"><span data-stu-id="457a1-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="457a1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="457a1-111">See also</span></span>

- [<span data-ttu-id="457a1-112">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="457a1-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="457a1-113">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="457a1-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

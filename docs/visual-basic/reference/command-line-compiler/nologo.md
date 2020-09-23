---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 5557d681c5e6901592936efd35b3c552d43e39b0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097676"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="36387-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36387-102">-nologo (Visual Basic)</span></span>

<span data-ttu-id="36387-103">Derleme sırasında telif hakkı başlığının ve bilgilendirici mesajların görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="36387-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36387-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="36387-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="36387-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36387-105">Remarks</span></span>  

 <span data-ttu-id="36387-106">Belirtirseniz `-nologo` , derleyici bir telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="36387-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="36387-107">Varsayılan olarak `-nologo` etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="36387-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36387-108">`-nologo`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36387-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36387-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="36387-109">Example</span></span>  

 <span data-ttu-id="36387-110">Aşağıdaki kod, `T2.vb` bir telif hakkı başlığını derler ve göstermez.</span><span class="sxs-lookup"><span data-stu-id="36387-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="36387-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36387-111">See also</span></span>

- [<span data-ttu-id="36387-112">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="36387-112">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="36387-113">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="36387-113">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

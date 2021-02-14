---
description: Hakkında daha fazla bilgi edinin:-nologo (Visual Basic)
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 370889fbd5d4e499ba27ff8bee4adc16a7a71876
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434894"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="98ca3-103">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98ca3-103">-nologo (Visual Basic)</span></span>

<span data-ttu-id="98ca3-104">Derleme sırasında telif hakkı başlığının ve bilgilendirici mesajların görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="98ca3-104">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98ca3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="98ca3-105">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="98ca3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98ca3-106">Remarks</span></span>  

 <span data-ttu-id="98ca3-107">Belirtirseniz `-nologo` , derleyici bir telif hakkı başlığını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="98ca3-107">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="98ca3-108">Varsayılan olarak `-nologo` etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="98ca3-108">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98ca3-109">`-nologo`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98ca3-109">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98ca3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="98ca3-110">Example</span></span>  

 <span data-ttu-id="98ca3-111">Aşağıdaki kod, `T2.vb` bir telif hakkı başlığını derler ve göstermez.</span><span class="sxs-lookup"><span data-stu-id="98ca3-111">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="98ca3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98ca3-112">See also</span></span>

- [<span data-ttu-id="98ca3-113">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="98ca3-113">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="98ca3-114">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="98ca3-114">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

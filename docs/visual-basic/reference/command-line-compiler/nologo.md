---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: c1824e4a086ecdd4b6a776bd6894f6e003d02867
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789014"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="832a6-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="832a6-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="832a6-103">Derleme sırasında telif hakkı başlığının ve bilgi iletilerinin görüntülenmesini bastırır.</span><span class="sxs-lookup"><span data-stu-id="832a6-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="832a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="832a6-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="832a6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="832a6-105">Remarks</span></span>  
 <span data-ttu-id="832a6-106">Belirtirseniz `-nologo`, derleyici bir telif hakkı başlık göstermez.</span><span class="sxs-lookup"><span data-stu-id="832a6-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="832a6-107">Varsayılan olarak, `-nologo` etkili değildir.</span><span class="sxs-lookup"><span data-stu-id="832a6-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="832a6-108">`-nologo` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="832a6-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="832a6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="832a6-109">Example</span></span>  
 <span data-ttu-id="832a6-110">Aşağıdaki kod derlenir `T2.vb` ve telif hakkı başlığını göstermez.</span><span class="sxs-lookup"><span data-stu-id="832a6-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="832a6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="832a6-111">See also</span></span>

- [<span data-ttu-id="832a6-112">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="832a6-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="832a6-113">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="832a6-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

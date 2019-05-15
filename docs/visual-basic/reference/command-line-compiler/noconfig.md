---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: b707899c845b6b08e008fe229497f682c930044a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588852"
---
# <a name="-noconfig"></a><span data-ttu-id="d20f6-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="d20f6-102">-noconfig</span></span>
<span data-ttu-id="d20f6-103">Derleyicinin otomatik olarak yaygın olarak kullanılan .NET Framework derlemelerine veya içeri aktarma belirtir `System` ve `Microsoft.VisualBasic` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="d20f6-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d20f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d20f6-104">Syntax</span></span>  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="d20f6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d20f6-105">Remarks</span></span>  
 <span data-ttu-id="d20f6-106">`-noconfig` Vbc.exe dosyasıyla aynı dizinde bulunan nezahrnovat dosyası derleme değil derleyici seçeneği söyler.</span><span class="sxs-lookup"><span data-stu-id="d20f6-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="d20f6-107">Nezahrnovat dosya yaygın olarak kullanılan .NET Framework derlemeleri atıfta bulunan ve içeri aktarır `System` ve `Microsoft.VisualBasic` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="d20f6-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="d20f6-108">Derleyici örtük olarak sürece System.dll derlemeye başvuran `-nostdlib` seçeneği belirtildi.</span><span class="sxs-lookup"><span data-stu-id="d20f6-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="d20f6-109">`-nostdlib` Seçeneği söyler derleyicinin nezahrnovat ile derleyin veya otomatik olarak System.dll derleme başvurusu değil.</span><span class="sxs-lookup"><span data-stu-id="d20f6-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d20f6-110">Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin derlemeler her zaman başvurulur.</span><span class="sxs-lookup"><span data-stu-id="d20f6-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="d20f6-111">Her Vbc.exe derlemede dahil edilmesi gereken ek derleyici seçeneklerini belirtmek için nezahrnovat dosyasını değiştirebilirsiniz (belirtirken dışındaki `-noconfig` seçeneği).</span><span class="sxs-lookup"><span data-stu-id="d20f6-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="d20f6-112">Daha fazla bilgi için [@ (yanıt dosyası belirtme)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="d20f6-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="d20f6-113">Derleyici geçirilecek seçeneklerini işler `vbc` son komutu.</span><span class="sxs-lookup"><span data-stu-id="d20f6-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="d20f6-114">Bu nedenle, komut satırında herhangi bir seçenek nezahrnovat dosyasında aynı seçeneğinin ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="d20f6-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d20f6-115">`-noconfig` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d20f6-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d20f6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d20f6-116">See also</span></span>

- [<span data-ttu-id="d20f6-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d20f6-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [<span data-ttu-id="d20f6-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d20f6-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d20f6-119">@ (Yanıt Dosyasını Belirtin)</span><span class="sxs-lookup"><span data-stu-id="d20f6-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [<span data-ttu-id="d20f6-120">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d20f6-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)

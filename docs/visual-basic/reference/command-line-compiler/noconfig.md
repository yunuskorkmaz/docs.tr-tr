---
title: -noconfig
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2cebc617aea9ebbb16197f27841794b2e6ad46ea
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-noconfig"></a><span data-ttu-id="f2892-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="f2892-102">-noconfig</span></span>
<span data-ttu-id="f2892-103">Derleyici otomatik olarak yaygın olarak kullanılan başvuru vermemelisiniz olduğunu belirtir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler veya içeri aktarma `System` ve `Microsoft.VisualBasic` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="f2892-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2892-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2892-104">Syntax</span></span>  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="f2892-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2892-105">Remarks</span></span>  
 <span data-ttu-id="f2892-106">`-noconfig` Seçenek Vbc.exe dosya ile aynı dizinde bulunan Vbc.rsp dosyayla değil derlemeye derleyici söyler.</span><span class="sxs-lookup"><span data-stu-id="f2892-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="f2892-107">Vbc.rsp dosya yaygın olarak kullanılan başvuran [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler ve içeri aktarmalar `System` ve `Microsoft.VisualBasic` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="f2892-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="f2892-108">Derleyici örtük olarak sürece System.dll bütünleştirilmiş koduna başvuruyor `-nostdlib` seçeneği belirtildi.</span><span class="sxs-lookup"><span data-stu-id="f2892-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="f2892-109">`-nostdlib` Seçeneği ile Vbc.rsp derleme veya otomatik olarak System.dll derleme başvurusu derleyici söyler.</span><span class="sxs-lookup"><span data-stu-id="f2892-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2892-110">Her zaman başvurulan Mscorlib.dll ve Microsoft.VisualBasic.dll içinde derlemeler.</span><span class="sxs-lookup"><span data-stu-id="f2892-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="f2892-111">Her Vbc.exe derlemede dahil edilmesi gereken ek derleyici seçeneklerini belirtmek için Vbc.rsp dosyasını değiştirebilirsiniz (belirtirken dışındaki `-noconfig` seçeneği).</span><span class="sxs-lookup"><span data-stu-id="f2892-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="f2892-112">Daha fazla bilgi için bkz: [@ (yanıt dosyasını belirtin)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="f2892-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="f2892-113">Derleyici geçirilen seçenekleri işler `vbc` son komutu.</span><span class="sxs-lookup"><span data-stu-id="f2892-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="f2892-114">Bu nedenle, komut satırında herhangi bir seçenek Vbc.rsp dosyasındaki aynı seçeneği ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f2892-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2892-115">`-noconfig` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2892-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2892-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2892-116">See Also</span></span>  
 [<span data-ttu-id="f2892-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2892-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [<span data-ttu-id="f2892-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="f2892-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f2892-119">@ (Yanıt Dosyasını Belirtin)</span><span class="sxs-lookup"><span data-stu-id="f2892-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [<span data-ttu-id="f2892-120">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2892-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)

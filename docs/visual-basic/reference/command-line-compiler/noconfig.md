---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ca184fa130d62dc118d0de551ac58f3165064029
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964389"
---
# <a name="-noconfig"></a><span data-ttu-id="624a9-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="624a9-102">-noconfig</span></span>
<span data-ttu-id="624a9-103">Derleyicinin yaygın olarak kullanılan .NET Framework derlemelerine otomatik olarak başvurmamalıdır veya `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktaramamalıdır.</span><span class="sxs-lookup"><span data-stu-id="624a9-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="624a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="624a9-104">Syntax</span></span>  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="624a9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="624a9-105">Remarks</span></span>  
 <span data-ttu-id="624a9-106">`-noconfig` Seçeneği, derleyicinin Vbc. exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyası ile derlenmeyeceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="624a9-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="624a9-107">Vbc. rsp dosyası, yaygın olarak kullanılan .NET Framework derlemelerine başvurur ve `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="624a9-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="624a9-108">`-nostdlib` Seçenek belirtilmediği takdirde derleyici System. dll derlemesine dolaylı olarak başvurur.</span><span class="sxs-lookup"><span data-stu-id="624a9-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="624a9-109">`-nostdlib` Seçeneği, derleyicinin Vbc. rsp ile derlenmeyeceğini veya System. dll derlemesine otomatik olarak başvurmayacağını söyler.</span><span class="sxs-lookup"><span data-stu-id="624a9-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="624a9-110">Mscorlib. dll ve Microsoft. VisualBasic. dll derlemelerine her zaman başvurulur.</span><span class="sxs-lookup"><span data-stu-id="624a9-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="624a9-111">Vbc. rsp dosyasını, her Vbc. exe derlemesine dahil edilecek ek derleyici seçeneklerini belirtmek için değiştirebilirsiniz ( `-noconfig` seçeneğini belirtirken hariç).</span><span class="sxs-lookup"><span data-stu-id="624a9-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="624a9-112">Daha fazla bilgi için bkz. [@ (yanıt dosyası belirtme)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="624a9-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="624a9-113">Derleyici, son `vbc` komuta geçirilen seçenekleri işler.</span><span class="sxs-lookup"><span data-stu-id="624a9-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="624a9-114">Bu nedenle, komut satırındaki herhangi bir seçenek, vbc. rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="624a9-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="624a9-115">Bu `-noconfig` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="624a9-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="624a9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="624a9-116">See also</span></span>

- [<span data-ttu-id="624a9-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="624a9-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [<span data-ttu-id="624a9-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="624a9-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="624a9-119">@ (Yanıt Dosyasını Belirtin)</span><span class="sxs-lookup"><span data-stu-id="624a9-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [<span data-ttu-id="624a9-120">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="624a9-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)

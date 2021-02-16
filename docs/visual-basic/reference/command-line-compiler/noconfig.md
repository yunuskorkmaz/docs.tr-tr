---
description: :-Noconfig hakkında daha fazla bilgi edinin
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: e97d44427b537e73a404a47d30db202e2c3b1f41
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481694"
---
# <a name="-noconfig"></a><span data-ttu-id="31527-103">-noconfig</span><span class="sxs-lookup"><span data-stu-id="31527-103">-noconfig</span></span>

<span data-ttu-id="31527-104">Derleyicinin yaygın olarak kullanılan .NET Framework derlemelerine otomatik olarak başvurmamalıdır veya `System` ve ad alanlarını içeri aktaramamalıdır `Microsoft.VisualBasic` .</span><span class="sxs-lookup"><span data-stu-id="31527-104">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31527-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="31527-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="31527-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31527-106">Remarks</span></span>  

 <span data-ttu-id="31527-107">`-noconfig`Seçeneği, derleyicinin Vbc.exe dosyasıyla aynı dizinde bulunan Vbc. rsp dosyası ile derlenmeyeceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="31527-107">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="31527-108">Vbc. rsp dosyası, yaygın olarak kullanılan .NET Framework derlemelerine başvurur ve `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="31527-108">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="31527-109">Seçenek belirtilmediği takdirde derleyici System.dll derlemesine örtülü olarak başvurur `-nostdlib` .</span><span class="sxs-lookup"><span data-stu-id="31527-109">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="31527-110">`-nostdlib`Seçeneği, derleyicinin Vbc. rsp ile derlenmeyeceğini veya System.dll derlemesine otomatik olarak başvurmayacağını söyler.</span><span class="sxs-lookup"><span data-stu-id="31527-110">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31527-111">Mscorlib.dll ve Microsoft.VisualBasic.dll derlemelerine her zaman başvurulur.</span><span class="sxs-lookup"><span data-stu-id="31527-111">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="31527-112">Her Vbc.exe derlemesinde bulunması gereken ek derleyici seçeneklerini belirtmek için Vbc. rsp dosyasını değiştirebilirsiniz (seçenek belirtildiğinde hariç `-noconfig` ).</span><span class="sxs-lookup"><span data-stu-id="31527-112">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="31527-113">Daha fazla bilgi için bkz. [@ (yanıt dosyası belirtme)](specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="31527-113">For more information, see [@ (Specify Response File)](specify-response-file.md).</span></span>  
  
 <span data-ttu-id="31527-114">Derleyici, son komuta geçirilen seçenekleri işler `vbc` .</span><span class="sxs-lookup"><span data-stu-id="31527-114">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="31527-115">Bu nedenle, komut satırındaki herhangi bir seçenek, vbc. rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="31527-115">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31527-116">`-noconfig`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31527-116">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31527-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31527-117">See also</span></span>

- [<span data-ttu-id="31527-118">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31527-118">-nostdlib (Visual Basic)</span></span>](nostdlib.md)
- [<span data-ttu-id="31527-119">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="31527-119">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="31527-120">@ (Yanıt Dosyasını Belirtin)</span><span class="sxs-lookup"><span data-stu-id="31527-120">@ (Specify Response File)</span></span>](specify-response-file.md)
- [<span data-ttu-id="31527-121">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31527-121">-reference (Visual Basic)</span></span>](reference.md)

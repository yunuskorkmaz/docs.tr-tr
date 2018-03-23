---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14361c01d13238db8f820b43889716e2528097f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="eac44-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eac44-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="eac44-103">Otomatik olarak standart kitaplıkları değil, başvuru için derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="eac44-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eac44-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eac44-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="eac44-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eac44-105">Remarks</span></span>  
 <span data-ttu-id="eac44-106">`-nostdlib` Seçeneği otomatik System.dll derleme başvurusu kaldırır ve derleyici Vbc.rsp dosyayı okumasını önler.</span><span class="sxs-lookup"><span data-stu-id="eac44-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="eac44-107">Vbc.exe dosya ile aynı dizinde bulunan Vbc.rsp dosyasını yaygın olarak kullanılan başvuran [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler ve içeri aktarmalar `System` ve `Microsoft.VisualBasic` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="eac44-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eac44-108">Her zaman başvurulan Mscorlib.dll ve Microsoft.VisualBasic.dll içinde derlemeler.</span><span class="sxs-lookup"><span data-stu-id="eac44-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eac44-109">`-nostdlib` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eac44-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eac44-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="eac44-110">Example</span></span>  
 <span data-ttu-id="eac44-111">Aşağıdaki kod derlerken `T2.vb` standart kitaplıkları başvuran olmadan.</span><span class="sxs-lookup"><span data-stu-id="eac44-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="eac44-112">Ayarlamalısınız `_MYTYPE` koşullu derleme sabiti kaldırmak için "boş" dizeye `My` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="eac44-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="eac44-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eac44-113">See Also</span></span>  
 [<span data-ttu-id="eac44-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="eac44-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="eac44-115">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="eac44-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="eac44-116">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="eac44-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="eac44-117">My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="eac44-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)

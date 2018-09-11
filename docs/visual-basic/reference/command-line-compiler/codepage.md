---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: fda75383435fdff718d1d50bc8583afc9858e7e2
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276493"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="15843-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15843-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="15843-103">Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15843-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15843-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15843-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="15843-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="15843-105">Arguments</span></span>  
  
|<span data-ttu-id="15843-106">Terim</span><span class="sxs-lookup"><span data-stu-id="15843-106">Term</span></span>|<span data-ttu-id="15843-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="15843-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="15843-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="15843-108">Required.</span></span> <span data-ttu-id="15843-109">Derleyici tarafından belirtilen kod sayfası kullanır `id` kaynak dosyalarını kodlama yorumlamak için.</span><span class="sxs-lookup"><span data-stu-id="15843-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15843-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15843-110">Remarks</span></span>  
 <span data-ttu-id="15843-111">Belirli bir kodlama ile kaydedilmiş kaynak kodu derlemek için kullanabileceğiniz `-codepage` hangi kod sayfası kullanılması gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="15843-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="15843-112">`-codepage` Derlemenizdeki tüm kaynak kodu dosyaları seçeneğini uygular.</span><span class="sxs-lookup"><span data-stu-id="15843-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="15843-113">Daha fazla bilgi için [karakter kodlaması .NET Framework'teki](../../../standard/base-types/character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="15843-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="15843-114">`-codepage` Seçeneği kaynak kodu dosyaları bir imza ile geçerli ANSI kod sayfası, Unicode veya UTF-8 kullanarak kaydedildiyse gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="15843-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="15843-115">Visual Studio kaydeder tüm kaynak kodu dosyaları geçerli ANSI kod sayfasıyla varsayılan olarak, kullanıcı, başka bir kodlama belirtmediği sürece **kodlama** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="15843-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="15843-116">Visual Studio kullanan **kodlama** farklı bir kod sayfası ile kaydedilen kaynak kodu dosyaları açmak için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="15843-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15843-117">`-codepage` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="15843-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15843-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15843-118">See also</span></span>

- [<span data-ttu-id="15843-119">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="15843-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

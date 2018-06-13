---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 383b6adae94c27efdd236de31ddfa8d16a6d4648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648534"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="e316a-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e316a-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="e316a-103">Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e316a-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e316a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e316a-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="e316a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e316a-105">Arguments</span></span>  
  
|<span data-ttu-id="e316a-106">Terim</span><span class="sxs-lookup"><span data-stu-id="e316a-106">Term</span></span>|<span data-ttu-id="e316a-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="e316a-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="e316a-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e316a-108">Required.</span></span> <span data-ttu-id="e316a-109">Derleyici tarafından belirtilen kod sayfası kullanan `id` kaynak dosyalarını kodlama yorumlayamadı.</span><span class="sxs-lookup"><span data-stu-id="e316a-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e316a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e316a-110">Remarks</span></span>  
 <span data-ttu-id="e316a-111">Belirli bir kodlama ile kaydedilmiş kaynak kodu derlemek için kullanabileceğiniz `-codepage` hangi kod sayfası kullanılması gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="e316a-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="e316a-112">`-codepage` Seçenek derlemeniz tüm kaynak kodu dosyaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e316a-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="e316a-113">Daha fazla bilgi için bkz: [karakter kodlamasını .NET Framework'teki](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="e316a-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="e316a-114">`-codepage` Seçeneği kaynak kodu dosyaları geçerli ANSI kod sayfası, Unicode veya UTF-8 bir imza ile kullanılarak kaydedildiyse gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e316a-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="e316a-115">Visual Studio kaydeder tüm kaynak kodu dosyaları geçerli ANSI kod sayfası ile varsayılan olarak, kullanıcı, başka bir kodlama belirtmedikçe **kodlama** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e316a-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="e316a-116">Visual Studio kullanan **kodlama** farklı kod sayfası ile kaydedilen kaynak kodu dosyaları açmak için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e316a-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e316a-117">`-codepage` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e316a-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e316a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e316a-118">See Also</span></span>  
 [<span data-ttu-id="e316a-119">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e316a-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

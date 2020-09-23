---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 769f3586ddef7f430fa96d6101b250a5bbc4e26c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065742"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="e6b72-102">-CodePage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6b72-102">-codepage (Visual Basic)</span></span>

<span data-ttu-id="e6b72-103">Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6b72-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b72-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e6b72-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6b72-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="e6b72-105">Arguments</span></span>  
  
|<span data-ttu-id="e6b72-106">Terim</span><span class="sxs-lookup"><span data-stu-id="e6b72-106">Term</span></span>|<span data-ttu-id="e6b72-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="e6b72-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="e6b72-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e6b72-108">Required.</span></span> <span data-ttu-id="e6b72-109">Derleyici, `id` kaynak dosyaların kodlamasını yorumlamak için tarafından belirtilen kod sayfasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6b72-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6b72-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6b72-110">Remarks</span></span>  

 <span data-ttu-id="e6b72-111">Belirli bir kodlamayla kaydedilen kaynak kodu derlemek için, `-codepage` hangi kod sayfasının kullanılacağını belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6b72-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="e6b72-112">Bu `-codepage` seçenek, derinizdeki tüm kaynak kodu dosyaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e6b72-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="e6b72-113">Daha fazla bilgi için [.NET Framework karakter kodlaması](../../../standard/base-types/character-encoding.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e6b72-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="e6b72-114">`-codepage`Kaynak kodu dosyaları bir imzayla GEÇERLI ANSI kod sayfası, Unicode veya UTF-8 kullanılarak kaydedilmişse seçenek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e6b72-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="e6b72-115">Kullanıcı **kodlama** iletişim kutusunda başka bir kodlama belirtmediği takdirde, Visual Studio tüm kaynak kodu dosyalarını varsayılan olarak geçerli ANSI kod sayfasıyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e6b72-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="e6b72-116">Visual Studio, farklı bir kod sayfasıyla kaydedilen kaynak kodu dosyalarını açmak için **kodlama** iletişim kutusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6b72-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6b72-117">`-codepage`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6b72-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b72-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b72-118">See also</span></span>

- [<span data-ttu-id="e6b72-119">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e6b72-119">Visual Basic Command-Line Compiler</span></span>](index.md)

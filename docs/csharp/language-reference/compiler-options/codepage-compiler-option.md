---
title: -codepage (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 59dc1abc3f678a4cf15543c11f9f200ff318ce8f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876921"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="af739-102">-codepage (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="af739-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="af739-103">Bu seçenek, gerekli sayfa sistemi için geçerli varsayılan kod sayfası değilse derleme sırasında kullanılacak hangi kod sayfasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="af739-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af739-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af739-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="af739-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="af739-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="af739-106">Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını kimliği.</span><span class="sxs-lookup"><span data-stu-id="af739-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af739-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af739-107">Remarks</span></span>  
 <span data-ttu-id="af739-108">Derleyici, tüm kaynak dosyaları UTF-8 yorumlamak ilk kez deneyecek.</span><span class="sxs-lookup"><span data-stu-id="af739-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="af739-109">Kaynak kod dosyalarınızı bir UTF-8'den başka bir kodlama içinde olan ve 7 bit ASCII karakterleri dışında karakterler kullanırsanız kullanın **- kod sayfası** hangi kod sayfası kullanılması gerektiğini belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="af739-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="af739-110">**-codepage** derlemenizdeki tüm kaynak kodu dosyaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="af739-110">**-codepage** applies to all source code files in your compilation.</span></span>  
    
 <span data-ttu-id="af739-111">Bkz: [desteklendiğinin](/windows/desktop/api/winnls/nf-winnls-getcpinfo) nasıl hangi kodun bulunacağı hakkında bilgi için sisteminizde sayfaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="af739-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="af739-112">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="af739-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af739-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af739-113">See also</span></span>

- [<span data-ttu-id="af739-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="af739-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="af739-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="af739-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

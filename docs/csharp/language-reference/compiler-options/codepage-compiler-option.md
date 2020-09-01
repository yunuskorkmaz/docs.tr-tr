---
description: -CodePage (C# derleyici seçenekleri)
title: -CodePage (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 4c812314ed9c1abcd7d2f34b2281140175621312
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125962"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="786ec-103">-CodePage (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="786ec-103">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="786ec-104">Bu seçenek, gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse, derleme sırasında kullanılacak kod sayfasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="786ec-104">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="786ec-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="786ec-105">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="786ec-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="786ec-106">Arguments</span></span>  
 `id`  
 <span data-ttu-id="786ec-107">Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasının kimliği.</span><span class="sxs-lookup"><span data-stu-id="786ec-107">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="786ec-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="786ec-108">Remarks</span></span>  
 <span data-ttu-id="786ec-109">Derleyici önce tüm kaynak dosyalarını UTF-8 olarak yorumlamaya çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="786ec-109">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="786ec-110">Kaynak kodu dosyalarınız UTF-8 dışındaki bir kodlamadeyse ve 7 bit ASCII karakterlerden farklı karakterler kullanıyorsa, hangi kod sayfasının kullanılacağını belirtmek için **-CodePage** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="786ec-110">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="786ec-111">**-CodePage** , derinizdeki tüm kaynak kodu dosyaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="786ec-111">**-codepage** applies to all source code files in your compilation.</span></span>  

 <span data-ttu-id="786ec-112">Sisteminizde hangi kod sayfalarının desteklendiğini bulma hakkında bilgi için bkz. [Getcpınfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) .</span><span class="sxs-lookup"><span data-stu-id="786ec-112">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="786ec-113">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="786ec-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="786ec-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="786ec-114">See also</span></span>

- [<span data-ttu-id="786ec-115">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="786ec-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="786ec-116">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="786ec-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

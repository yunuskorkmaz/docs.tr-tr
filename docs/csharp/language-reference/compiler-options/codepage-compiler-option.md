---
title: -CodePage (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: c85cd8935bcefd1353707624052b62ee982f7b07
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603057"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="48979-102">-CodePage (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="48979-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="48979-103">Bu seçenek, gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse, derleme sırasında kullanılacak kod sayfasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="48979-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48979-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48979-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="48979-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="48979-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="48979-106">Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasının kimliği.</span><span class="sxs-lookup"><span data-stu-id="48979-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48979-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48979-107">Remarks</span></span>  
 <span data-ttu-id="48979-108">Derleyici önce tüm kaynak dosyalarını UTF-8 olarak yorumlamaya çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="48979-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="48979-109">Kaynak kodu dosyalarınız UTF-8 dışındaki bir kodlamadeyse ve 7 bit ASCII karakterlerden farklı karakterler kullanıyorsa, hangi kod sayfasının kullanılacağını belirtmek için **-CodePage** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="48979-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="48979-110">**-CodePage** , derinizdeki tüm kaynak kodu dosyaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="48979-110">**-codepage** applies to all source code files in your compilation.</span></span>  
    
 <span data-ttu-id="48979-111">Sisteminizde hangi kod sayfalarının desteklendiğini bulma hakkında bilgi için bkz. [Getcpınfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) .</span><span class="sxs-lookup"><span data-stu-id="48979-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="48979-112">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="48979-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48979-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48979-113">See also</span></span>

- [<span data-ttu-id="48979-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="48979-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="48979-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="48979-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

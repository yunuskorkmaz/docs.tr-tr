---
title: -kod sayfası (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 3352e7fc446ace391540360a3b6b36d604ca5f13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173763"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="bc17f-102">-kod sayfası (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="bc17f-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="bc17f-103">Bu seçenek, gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse, derleme sırasında hangi kod sayfasının kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc17f-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc17f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc17f-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="bc17f-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="bc17f-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="bc17f-106">Derlemedeki tüm kaynak kod dosyaları için kullanılacak kod sayfasının kimliği.</span><span class="sxs-lookup"><span data-stu-id="bc17f-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc17f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc17f-107">Remarks</span></span>  
 <span data-ttu-id="bc17f-108">Derleyici ilk olarak tüm kaynak dosyaları UTF-8 olarak yorumlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="bc17f-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="bc17f-109">Kaynak kod dosyalarınız UTF-8 dışındaki bir kodlamadaysa ve 7 bit ASCII karakterleri dışındaki karakterleri kullanıyorsa, hangi kod sayfasının kullanılması gerektiğini belirtmek için **-codepage** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc17f-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="bc17f-110">**-codepage** derlemenizdeki tüm kaynak kod dosyaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc17f-110">**-codepage** applies to all source code files in your compilation.</span></span>  

 <span data-ttu-id="bc17f-111">Sisteminizde hangi kod sayfalarının desteklendiği hakkında bilgi için [GetCPInfo'ya](/windows/desktop/api/winnls/nf-winnls-getcpinfo) bakın.</span><span class="sxs-lookup"><span data-stu-id="bc17f-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="bc17f-112">Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="bc17f-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc17f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc17f-113">See also</span></span>

- [<span data-ttu-id="bc17f-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bc17f-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="bc17f-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="bc17f-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

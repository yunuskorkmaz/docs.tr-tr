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
ms.openlocfilehash: 7cbd3ec1b2d134106c6c9429341f5603444dac27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693989"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="5f7aa-102">-codepage (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5f7aa-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="5f7aa-103">Bu seçenek, gerekli sayfa sistemi için geçerli varsayılan kod sayfası değilse derleme sırasında kullanılacak hangi kod sayfasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f7aa-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f7aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f7aa-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="5f7aa-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5f7aa-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="5f7aa-106">Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını kimliği.</span><span class="sxs-lookup"><span data-stu-id="5f7aa-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f7aa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f7aa-107">Remarks</span></span>  
 <span data-ttu-id="5f7aa-108">Bilgisayarınızda varsayılan kod sayfası kullanılacak oluşturulmayan bir veya daha fazla kaynak kodu dosyaları derleme yaparsanız, kullanabileceğiniz **- kod sayfası** hangi kod sayfası kullanılması gerektiğini belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5f7aa-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="5f7aa-109">**-codepage** derlemenizdeki tüm kaynak kodu dosyaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f7aa-109">**-codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="5f7aa-110">Kaynak kodu dosyaları bilgisayarınızda geçerli olan kod sayfası ile oluşturulan veya kaynak kodu dosyaları UNICODE veya UTF-8 ile oluşturulduysa, kullanılmıyor ihtiyacınız varsa **- kod sayfası**.</span><span class="sxs-lookup"><span data-stu-id="5f7aa-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **-codepage**.</span></span>  
  
 <span data-ttu-id="5f7aa-111">Bkz: [desteklendiğinin](/windows/desktop/api/winnls/nf-winnls-getcpinfo) nasıl hangi kodun bulunacağı hakkında bilgi için sisteminizde sayfaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5f7aa-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="5f7aa-112">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="5f7aa-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f7aa-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f7aa-113">See also</span></span>

- [<span data-ttu-id="5f7aa-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5f7aa-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="5f7aa-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="5f7aa-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

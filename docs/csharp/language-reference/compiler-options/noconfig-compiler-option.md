---
description: -noconfig (C# derleyici seçenekleri)
title: -noconfig (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: d62f16a3926aaa78e79c25b1c9b8d84e4401795a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194082"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="6e4e2-103">-noconfig (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6e4e2-103">-noconfig (C# Compiler Options)</span></span>

<span data-ttu-id="6e4e2-104">**-Noconfig** seçeneği, derleyicinin ' de bulunan ve csc.exe dosyasıyla aynı dizinden yüklenen csc. rsp dosyası ile derlenmeyeceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="6e4e2-104">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e4e2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e4e2-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="6e4e2-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e4e2-106">Remarks</span></span>  

 <span data-ttu-id="6e4e2-107">Csc. rsp dosyası .NET Framework ile gönderilen tüm derlemelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="6e4e2-107">The csc.rsp file references all the assemblies shipped with .NET Framework.</span></span> <span data-ttu-id="6e4e2-108">Visual Studio .NET geliştirme ortamının içerdiği gerçek başvurular proje türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6e4e2-108">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="6e4e2-109">Csc. rsp dosyasını değiştirebilir ve csc.exe ( **-noconfig** seçeneği dışında) komut satırından her derlemede yer alan ek derleyici seçeneklerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e4e2-109">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="6e4e2-110">Derleyici, son olarak **CSC** komutuna geçirilen seçenekleri işler.</span><span class="sxs-lookup"><span data-stu-id="6e4e2-110">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="6e4e2-111">Bu nedenle, komut satırındaki herhangi bir seçenek CSC. rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6e4e2-111">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="6e4e2-112">Derleyicinin Csc. rsp dosyasındaki ayarları bulup kullanmasını istemiyorsanız **-noconfig**' i belirtin.</span><span class="sxs-lookup"><span data-stu-id="6e4e2-112">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="6e4e2-113">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="6e4e2-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4e2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e4e2-114">See also</span></span>

- [<span data-ttu-id="6e4e2-115">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6e4e2-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6e4e2-116">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6e4e2-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

---
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
ms.openlocfilehash: 2d6d0c52be2306292224d7831f8818c6f865f2f4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602745"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="b3825-102">-noconfig (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="b3825-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="b3825-103">**-Noconfig** seçeneği, derleyicinin ' de bulunan ve CSC. exe dosyası ile aynı dizinden yüklenen csc. rsp dosyası ile derlenmeyeceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="b3825-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3825-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3825-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="b3825-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3825-105">Remarks</span></span>  
 <span data-ttu-id="b3825-106">Csc. rsp dosyası .NET Framework ile gönderilen tüm derlemelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="b3825-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="b3825-107">Visual Studio .NET geliştirme ortamının içerdiği gerçek başvurular proje türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b3825-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="b3825-108">Csc. rsp dosyasını değiştirebilir ve CSC. exe ile komut satırından her derlemeye dahil edilecek ek derleyici seçeneklerini belirtebilirsiniz ( **-noconfig** seçeneği hariç).</span><span class="sxs-lookup"><span data-stu-id="b3825-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="b3825-109">Derleyici, son olarak **CSC** komutuna geçirilen seçenekleri işler.</span><span class="sxs-lookup"><span data-stu-id="b3825-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="b3825-110">Bu nedenle, komut satırındaki herhangi bir seçenek CSC. rsp dosyasında aynı seçeneğin ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b3825-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="b3825-111">Derleyicinin Csc. rsp dosyasındaki ayarları bulup kullanmasını istemiyorsanız **-noconfig**' i belirtin.</span><span class="sxs-lookup"><span data-stu-id="b3825-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="b3825-112">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="b3825-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3825-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3825-113">See also</span></span>

- [<span data-ttu-id="b3825-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b3825-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b3825-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="b3825-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

---
title: -noconfig (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: b689a4bf0d8a1e57bf36f8ded7f2c9308f241670
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527309"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="e890e-102">-noconfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e890e-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="e890e-103">**- Noconfig** seçeneği bulunan ve aynı dizinden csc.exe dosyası olarak yüklenen csc.rsp dosyasını derlemek değil derleyicinin söyler.</span><span class="sxs-lookup"><span data-stu-id="e890e-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e890e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e890e-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="e890e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e890e-105">Remarks</span></span>  
 <span data-ttu-id="e890e-106">Csc.rsp dosyasını .NET Framework ile birlikte gelen tüm derlemelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="e890e-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="e890e-107">Visual Studio .NET geliştirme ortamını içeren gerçek başvuruları proje türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e890e-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="e890e-108">Csc.rsp dosyasını değiştirebilir ve her derleme komut satırından csc.exe dahil edilmesi gereken ek derleyici seçeneklerini belirtin (dışında **- noconfig** seçeneği).</span><span class="sxs-lookup"><span data-stu-id="e890e-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="e890e-109">Derleyici geçirilecek seçeneklerini işler **csc** son komutu.</span><span class="sxs-lookup"><span data-stu-id="e890e-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="e890e-110">Bu nedenle, komut satırında herhangi bir seçenek csc.rsp dosyasını aynı seçeneğinin ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e890e-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="e890e-111">Derleyicinin arayın ve csc.rsp dosyasındaki ayarları kullanın, belirtmek istemiyorsanız **- noconfig**.</span><span class="sxs-lookup"><span data-stu-id="e890e-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="e890e-112">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e890e-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e890e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e890e-113">See Also</span></span>  

- [<span data-ttu-id="e890e-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e890e-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="e890e-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="e890e-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

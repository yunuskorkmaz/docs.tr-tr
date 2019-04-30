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
ms.openlocfilehash: 8d28ef1334df847865721783fa98aaa9d8c576be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662692"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="21141-102">-noconfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="21141-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="21141-103">**- Noconfig** seçeneği bulunan ve aynı dizinden csc.exe dosyası olarak yüklenen csc.rsp dosyasını derlemek değil derleyicinin söyler.</span><span class="sxs-lookup"><span data-stu-id="21141-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21141-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21141-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="21141-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21141-105">Remarks</span></span>  
 <span data-ttu-id="21141-106">Csc.rsp dosyasını .NET Framework ile birlikte gelen tüm derlemelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="21141-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="21141-107">Visual Studio .NET geliştirme ortamını içeren gerçek başvuruları proje türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="21141-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="21141-108">Csc.rsp dosyasını değiştirebilir ve her derleme komut satırından csc.exe dahil edilmesi gereken ek derleyici seçeneklerini belirtin (dışında **- noconfig** seçeneği).</span><span class="sxs-lookup"><span data-stu-id="21141-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="21141-109">Derleyici geçirilecek seçeneklerini işler **csc** son komutu.</span><span class="sxs-lookup"><span data-stu-id="21141-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="21141-110">Bu nedenle, komut satırında herhangi bir seçenek csc.rsp dosyasını aynı seçeneğinin ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="21141-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="21141-111">Derleyicinin arayın ve csc.rsp dosyasındaki ayarları kullanın, belirtmek istemiyorsanız **- noconfig**.</span><span class="sxs-lookup"><span data-stu-id="21141-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="21141-112">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="21141-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21141-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21141-113">See also</span></span>

- [<span data-ttu-id="21141-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="21141-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="21141-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="21141-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

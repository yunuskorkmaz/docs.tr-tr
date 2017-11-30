---
title: "-noconfig (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2b15853cdd6ee9fe12b8b3ba3388a74e49c9701
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig-c-compiler-options"></a><span data-ttu-id="7348c-102">/noconfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="7348c-102">/noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="7348c-103">**/Noconfig** seçeneği bulunan ve csc.exe dosyasıyla aynı dizinden yüklenen csc.rsp dosyasıyla değil derlemeye derleyici söyler.</span><span class="sxs-lookup"><span data-stu-id="7348c-103">The **/noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7348c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7348c-104">Syntax</span></span>  
  
```console  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="7348c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7348c-105">Remarks</span></span>  
 <span data-ttu-id="7348c-106">Csc.rsp dosyasını .NET Framework ile gönderilen tüm derlemelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="7348c-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="7348c-107">Visual Studio .NET geliştirme ortamı içerir gerçek başvurular proje türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7348c-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="7348c-108">Csc.rsp dosyasını değiştirebilir ve csc.exe ile komut satırından her derlemeyi dahil edilmesi gereken ek derleyici seçeneklerini belirtin (dışında **/noconfig** seçeneği).</span><span class="sxs-lookup"><span data-stu-id="7348c-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **/noconfig** option).</span></span>  
  
 <span data-ttu-id="7348c-109">Derleyici geçirilen seçenekleri işler **csc** son komutu.</span><span class="sxs-lookup"><span data-stu-id="7348c-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="7348c-110">Bu nedenle, komut satırında herhangi bir seçenek csc.rsp dosyasındaki aynı seçeneği ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7348c-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="7348c-111">Derleyicinin arayın ve csc.rsp dosyasındaki ayarları kullanmak için belirtmek istemiyorsanız **/noconfig**.</span><span class="sxs-lookup"><span data-stu-id="7348c-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **/noconfig**.</span></span>  
  
 <span data-ttu-id="7348c-112">Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="7348c-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7348c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7348c-113">See Also</span></span>  
 [<span data-ttu-id="7348c-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="7348c-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="7348c-115">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="7348c-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

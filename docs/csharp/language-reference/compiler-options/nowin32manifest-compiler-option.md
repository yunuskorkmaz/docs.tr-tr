---
description: -nowin32manifest (C# derleyici seçenekleri)
title: -nowin32manifest (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 13bbee66901149d54632d9b164431f8898cdf52e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194004"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="714a7-103">-nowin32manifest (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="714a7-103">-nowin32manifest (C# Compiler Options)</span></span>

<span data-ttu-id="714a7-104">Derleyicinin herhangi bir uygulama bildirimini yürütülebilir dosyaya katıştırmamasını sağlamak için **-nowin32manifest** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="714a7-104">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="714a7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="714a7-105">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="714a7-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="714a7-106">Remarks</span></span>  

 <span data-ttu-id="714a7-107">Bu seçenek kullanıldığında, bir Win32 kaynak dosyasında veya sonraki bir derleme adımı sırasında uygulama bildirimi belirtmediğiniz müddetçe uygulama Windows Vista 'da sanallaştırmaya tabi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="714a7-107">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="714a7-108">Visual Studio 'da, **bildirim** açılan listesinde **bildirim olmadan uygulama oluştur** seçeneğini belirleyerek **uygulama özelliği** sayfasında bu seçeneği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714a7-108">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="714a7-109">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="714a7-109">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="714a7-110">Bildirim oluşturma hakkında daha fazla bilgi için bkz. [-win32manifest (C# derleyici seçenekleri)](./win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="714a7-110">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714a7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="714a7-111">See also</span></span>

- [<span data-ttu-id="714a7-112">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="714a7-112">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="714a7-113">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="714a7-113">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

---
title: -nowin32manifest (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602720"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="21dbf-102">-nowin32manifest (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="21dbf-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="21dbf-103">Derleyiciye yürütülebilir dosyaya herhangi bir uygulama bildirimi yerleştirmemesi için talimat vermek için **-nowin32manifest** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="21dbf-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21dbf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21dbf-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="21dbf-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21dbf-105">Remarks</span></span>  
 <span data-ttu-id="21dbf-106">Bu seçenek kullanıldığında, Win32 Kaynak dosyasında veya daha sonraki bir yapı adımında bir uygulama bildirimi sağlamadığınız sürece uygulama Windows Vista'da sanallaştırmaya tabi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="21dbf-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="21dbf-107">Visual Studio'da, **Bildirim** açılır listesinde **Manifest olmayan Uygulama Oluştur** seçeneğini seçerek bu seçeneği Uygulama **Özelliği** sayfasında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="21dbf-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="21dbf-108">Daha fazla bilgi için [Uygulama Sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="21dbf-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="21dbf-109">Bildirim oluşturma hakkında daha fazla bilgi için bkz: [-win32manifest (C# Derleyici Seçenekleri)](./win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="21dbf-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21dbf-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21dbf-110">See also</span></span>

- [<span data-ttu-id="21dbf-111">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="21dbf-111">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="21dbf-112">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="21dbf-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

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
ms.openlocfilehash: a07ead99ddd4e230fff8d1452ef81171ed849b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214938"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="5d9e3-102">-nowin32manifest (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5d9e3-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="5d9e3-103">Kullanım **-nowin32manifest** herhangi bir uygulama bildirimi yürütülebilir dosyasına katıştırma değil görevlendirin seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d9e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d9e3-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="5d9e3-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d9e3-105">Remarks</span></span>  
 <span data-ttu-id="5d9e3-106">Bu seçenek kullanıldığında, bir uygulama bildirimi Win32 kaynak dosyasını ya da daha yeni bir derleme adımı sırasında sağladığınız sürece uygulama Windows Vista sanallaştırma tabi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="5d9e3-107">Bu seçenek Visual Studio'da kümesinde **uygulama özelliği** seçerek sayfa **oluşturma uygulamayı bildirim olmadan** seçeneğini **bildirim** açılan liste.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="5d9e3-108">Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="5d9e3-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="5d9e3-109">Bildirim oluşturma hakkında daha fazla bilgi için bkz: [-win32manifest (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5d9e3-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d9e3-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-110">See Also</span></span>  
 [<span data-ttu-id="5d9e3-111">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5d9e3-111">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="5d9e3-112">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="5d9e3-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

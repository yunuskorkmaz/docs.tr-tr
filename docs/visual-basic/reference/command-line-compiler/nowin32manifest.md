---
description: Hakkında daha fazla bilgi edinin:-nowin32manifest (Visual Basic)
title: -nowin32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: 3aa07ee26e47d48da69f1d1b34c8ec4643b7422e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426731"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="d4ae2-103">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4ae2-103">-nowin32manifest (Visual Basic)</span></span>

<span data-ttu-id="d4ae2-104">Derleyicinin hiçbir uygulama bildirimini yürütülebilir dosyaya katıştırmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4ae2-104">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4ae2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d4ae2-105">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="d4ae2-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4ae2-106">Remarks</span></span>  

 <span data-ttu-id="d4ae2-107">Bu seçenek kullanıldığında, bir Win32 kaynak dosyasında veya sonraki bir derleme adımı sırasında uygulama bildirimi belirtmediğiniz müddetçe uygulama Windows Vista 'da sanallaştırmaya tabi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d4ae2-107">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="d4ae2-108">Sanallaştırma hakkında daha fazla bilgi için bkz. [Windows Vista 'Da ClickOnce dağıtımı](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="d4ae2-108">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="d4ae2-109">Bildirim oluşturma hakkında daha fazla bilgi için bkz. [-win32manifest (Visual Basic)](win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="d4ae2-109">For more information about manifest creation, see [-win32manifest (Visual Basic)](win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ae2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4ae2-110">See also</span></span>

- [<span data-ttu-id="d4ae2-111">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d4ae2-111">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d4ae2-112">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4ae2-112">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)

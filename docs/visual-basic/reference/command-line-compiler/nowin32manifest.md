---
title: -nowin32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: 8fd902e1317c7c767303bcaa30cdc56cff712558
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097624"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="bb1f8-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb1f8-102">-nowin32manifest (Visual Basic)</span></span>

<span data-ttu-id="bb1f8-103">Derleyicinin hiçbir uygulama bildirimini yürütülebilir dosyaya katıştırmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb1f8-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb1f8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bb1f8-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="bb1f8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb1f8-105">Remarks</span></span>  

 <span data-ttu-id="bb1f8-106">Bu seçenek kullanıldığında, bir Win32 kaynak dosyasında veya sonraki bir derleme adımı sırasında uygulama bildirimi belirtmediğiniz müddetçe uygulama Windows Vista 'da sanallaştırmaya tabi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bb1f8-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="bb1f8-107">Sanallaştırma hakkında daha fazla bilgi için bkz. [Windows Vista 'Da ClickOnce dağıtımı](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="bb1f8-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="bb1f8-108">Bildirim oluşturma hakkında daha fazla bilgi için bkz. [-win32manifest (Visual Basic)](win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="bb1f8-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb1f8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb1f8-109">See also</span></span>

- [<span data-ttu-id="bb1f8-110">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="bb1f8-110">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="bb1f8-111">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb1f8-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)

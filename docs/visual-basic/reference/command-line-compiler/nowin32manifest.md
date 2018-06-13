---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba4abc4a94a4938d54b3c34fbea2a5041a99454f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648768"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="ab3ee-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab3ee-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="ab3ee-103">Herhangi bir uygulama bildirimi yürütülebilir dosyasına katıştırma değil derleyiciye.</span><span class="sxs-lookup"><span data-stu-id="ab3ee-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab3ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab3ee-104">Syntax</span></span>  
  
```  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="ab3ee-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab3ee-105">Remarks</span></span>  
 <span data-ttu-id="ab3ee-106">Bu seçenek kullanıldığında, bir uygulama bildirimi Win32 kaynak dosyasını ya da daha yeni bir derleme adımı sırasında sağladığınız sürece uygulama Windows Vista sanallaştırma tabi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ab3ee-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="ab3ee-107">Sanallaştırma hakkında daha fazla bilgi için bkz: [Windows Vista'da ClickOnce dağıtımı](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="ab3ee-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="ab3ee-108">Bildirim oluşturma hakkında daha fazla bilgi için bkz: [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="ab3ee-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab3ee-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab3ee-109">See Also</span></span>  
 [<span data-ttu-id="ab3ee-110">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ab3ee-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ab3ee-111">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab3ee-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)

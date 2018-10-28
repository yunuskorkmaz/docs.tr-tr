---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: 382e8fd089211f6d23a1e6baff93bf08f19248c8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192303"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="15d09-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15d09-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="15d09-103">Herhangi bir uygulama bildirimi yürütülebilir dosyasına katıştırma değil derleyicinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="15d09-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d09-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15d09-104">Syntax</span></span>  
  
```  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="15d09-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15d09-105">Remarks</span></span>  
 <span data-ttu-id="15d09-106">Bu seçenek kullanıldığında, bir uygulama bildirimi bir Win32 kaynak dosyası veya üzeri bir derleme adımı sırasında sağladığınız sürece uygulama Windows Vista sanallaştırma tabi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="15d09-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="15d09-107">Sanallaştırma hakkında daha fazla bilgi için bkz. [Windows Vista'da ClickOnce dağıtımı](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="15d09-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="15d09-108">Bildirim oluşturma hakkında daha fazla bilgi için bkz. [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="15d09-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d09-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15d09-109">See Also</span></span>  
 [<span data-ttu-id="15d09-110">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="15d09-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="15d09-111">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15d09-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)

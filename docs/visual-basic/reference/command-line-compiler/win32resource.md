---
title: -win32resource
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e210d88d32ac7341ab881ca6ff0e44961469a31
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-win32resource"></a><span data-ttu-id="36983-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="36983-102">-win32resource</span></span>
<span data-ttu-id="36983-103">Win32 kaynak dosyasını çıktı dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="36983-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36983-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36983-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="36983-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="36983-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="36983-106">Çıkış dosyanızın eklemek için kaynak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="36983-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="36983-107">Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="36983-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36983-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36983-108">Remarks</span></span>  
 <span data-ttu-id="36983-109">Microsoft Windows Kaynak Derleyici (RC) ile Win32 kaynak dosyasını oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36983-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="36983-110">Win32 kaynak sürüm içerebilir veya yardım eden bir bit eşlem (simgesi) bilgi tanımlamak, uygulamanızda **dosya Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="36983-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="36983-111">Belirtmezseniz, `-win32resource`, derleyici derleme sürümünü temel alan sürüm bilgisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36983-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="36983-112">`-win32resource` Ve `-win32icon` seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="36983-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="36983-113">Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) başvurusu için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) eklemek için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="36983-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36983-114">`-win32resource` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36983-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36983-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="36983-115">Example</span></span>  
 <span data-ttu-id="36983-116">Aşağıdaki kod derlerken `In.vb` ve Win32 kaynak dosyasını, iliştirir `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="36983-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="36983-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36983-117">See Also</span></span>  
 [<span data-ttu-id="36983-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="36983-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="36983-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="36983-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

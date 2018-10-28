---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 4ecac4ffe665d724d625aaeb7cc1e008eb13ca54
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186089"
---
# <a name="-win32resource"></a><span data-ttu-id="0406a-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="0406a-102">-win32resource</span></span>
<span data-ttu-id="0406a-103">Bir Win32 kaynak dosyası çıkış dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="0406a-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0406a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0406a-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0406a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0406a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="0406a-106">Çıkış dosyanızı eklemek için kaynak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="0406a-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="0406a-107">Dosya adı tırnak içine alın ("") bir boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="0406a-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0406a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0406a-108">Remarks</span></span>  
 <span data-ttu-id="0406a-109">Microsoft Windows Kaynak derleyicisi (RC) ile bir Win32 kaynak dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0406a-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="0406a-110">Bir Win32 kaynağı sürümü içerebilir veya yardımcı olan bit eşlem (simge) bilgileri, uygulamanızda tanımlamak **dosya Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="0406a-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="0406a-111">Siz belirtmezseniz `-win32resource`, derleyici derleme sürümünü temel alan sürüm bilgisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0406a-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="0406a-112">`-win32resource` Ve `-win32icon` seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="0406a-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="0406a-113">Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) başvurmak için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) eklemek için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="0406a-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0406a-114">`-win32resource` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0406a-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0406a-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0406a-115">Example</span></span>  
 <span data-ttu-id="0406a-116">Aşağıdaki kod derlenir `In.vb` ve bir Win32 kaynak dosyası ekler `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="0406a-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0406a-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0406a-117">See Also</span></span>  
 [<span data-ttu-id="0406a-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="0406a-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0406a-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="0406a-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

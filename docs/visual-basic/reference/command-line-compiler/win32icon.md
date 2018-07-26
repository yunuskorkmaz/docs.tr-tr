---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 045e621f0104c4c958d77d2443c1524b33410b7a
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39221029"
---
# <a name="-win32icon"></a><span data-ttu-id="6b830-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="6b830-102">-win32icon</span></span>
<span data-ttu-id="6b830-103">Çıktı dosyasına bir .ico simge dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="6b830-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="6b830-104">Bu .ico dosyasını temsil eder çıkış dosyasında **dosya Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="6b830-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b830-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b830-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b830-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="6b830-106">Arguments</span></span>  
  
|<span data-ttu-id="6b830-107">Terim</span><span class="sxs-lookup"><span data-stu-id="6b830-107">Term</span></span>|<span data-ttu-id="6b830-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="6b830-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="6b830-109">Çıkış dosyanızı eklemek için .ico dosyası.</span><span class="sxs-lookup"><span data-stu-id="6b830-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="6b830-110">Dosya adı tırnak içine alın ("") bir boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="6b830-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b830-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b830-111">Remarks</span></span>  
 <span data-ttu-id="6b830-112">Microsoft Windows Kaynak derleyicisi (RC) olan bir .ico simge dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b830-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="6b830-113">Kaynak derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .ico simge dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b830-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="6b830-114">`-win32icon` Ve `-win32resource` seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="6b830-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="6b830-115">Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) başvurmak için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) eklemek için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="6b830-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="6b830-116">Bkz: [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) bir .res dosyası içeri aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="6b830-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="6b830-117">Ayarlanacak - Visual Studio IDE'de win32icon</span><span class="sxs-lookup"><span data-stu-id="6b830-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="6b830-118">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="6b830-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6b830-119">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6b830-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="6b830-120">2.  Tıklayın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="6b830-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="6b830-121">3.  Değer değiştirme **simgesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="6b830-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6b830-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b830-122">Example</span></span>  
 <span data-ttu-id="6b830-123">Aşağıdaki kod derlenir `In.vb` ve bir .ico simge dosyası ekler `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="6b830-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b830-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b830-124">See Also</span></span>  
 [<span data-ttu-id="6b830-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="6b830-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="6b830-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="6b830-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

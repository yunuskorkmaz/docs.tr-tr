---
title: -win32icon
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b2e2b4542f2e396a136f6a3d9baeb3e0c037a3
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-win32icon"></a><span data-ttu-id="018d4-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="018d4-102">-win32icon</span></span>
<span data-ttu-id="018d4-103">Bir .ico dosyasını çıktı dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="018d4-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="018d4-104">Çıktı dosyasında bu .ico dosyasını temsil eden **dosya Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="018d4-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="018d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="018d4-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="018d4-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="018d4-106">Arguments</span></span>  
  
|<span data-ttu-id="018d4-107">Terim</span><span class="sxs-lookup"><span data-stu-id="018d4-107">Term</span></span>|<span data-ttu-id="018d4-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="018d4-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="018d4-109">Çıkış dosyanızın eklemek için .ico dosyasını.</span><span class="sxs-lookup"><span data-stu-id="018d4-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="018d4-110">Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="018d4-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="018d4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="018d4-111">Remarks</span></span>  
 <span data-ttu-id="018d4-112">Microsoft Windows Kaynak Derleyici (RC) ile bir .ico dosyasını oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="018d4-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="018d4-113">Kaynak derleyicisi bir Visual C++ programını derleme yaparken çağrılır; .rc dosyasından bir .ico dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="018d4-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="018d4-114">`-win32icon` Ve `-win32resource` seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="018d4-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="018d4-115">Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) başvurusu için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) eklemek için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="018d4-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="018d4-116">Bkz: [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res dosyasını içeri aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="018d4-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="018d4-117">Ayarlanacak - win32icon Visual Studio IDE içinde</span><span class="sxs-lookup"><span data-stu-id="018d4-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="018d4-118">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="018d4-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="018d4-119">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="018d4-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="018d4-120">2.  Tıklatın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="018d4-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="018d4-121">3.  Değer değiştirme **simgesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="018d4-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="018d4-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="018d4-122">Example</span></span>  
 <span data-ttu-id="018d4-123">Aşağıdaki kod derlerken `In.vb` ve bir .ico dosyasını ekler `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="018d4-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="018d4-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="018d4-124">See Also</span></span>  
 [<span data-ttu-id="018d4-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="018d4-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="018d4-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="018d4-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

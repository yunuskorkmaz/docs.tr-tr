---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: dc48a8f79aa04892c514917da00b8fd6489695b1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593092"
---
# <a name="-win32icon"></a><span data-ttu-id="bd70d-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="bd70d-102">-win32icon</span></span>
<span data-ttu-id="bd70d-103">Çıktı dosyasına bir .ico simge dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="bd70d-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="bd70d-104">Bu .ico dosyasını temsil eder çıkış dosyasında **dosya Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="bd70d-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd70d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd70d-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd70d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="bd70d-106">Arguments</span></span>  
  
|<span data-ttu-id="bd70d-107">Terim</span><span class="sxs-lookup"><span data-stu-id="bd70d-107">Term</span></span>|<span data-ttu-id="bd70d-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="bd70d-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="bd70d-109">Çıkış dosyanızı eklemek için .ico dosyası.</span><span class="sxs-lookup"><span data-stu-id="bd70d-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="bd70d-110">Dosya adı tırnak içine alın ("") bir boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="bd70d-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd70d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd70d-111">Remarks</span></span>  
 <span data-ttu-id="bd70d-112">Microsoft Windows Kaynak derleyicisi (RC) olan bir .ico simge dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd70d-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="bd70d-113">Kaynak derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .ico simge dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bd70d-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="bd70d-114">`-win32icon` Ve `-win32resource` seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="bd70d-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="bd70d-115">Bkz: [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) bir .NET Framework kaynak dosyası başvurmak veya [-kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) bir .NET Framework kaynak dosyası eklemek için.</span><span class="sxs-lookup"><span data-stu-id="bd70d-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="bd70d-116">Bkz: [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) bir .res dosyası içeri aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="bd70d-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="bd70d-117">Ayarlanacak - Visual Studio IDE'de win32icon</span><span class="sxs-lookup"><span data-stu-id="bd70d-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="bd70d-118">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="bd70d-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bd70d-119">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="bd70d-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="bd70d-120">2.  Tıklayın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="bd70d-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="bd70d-121">3.  Değer değiştirme **simgesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="bd70d-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bd70d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd70d-122">Example</span></span>  
 <span data-ttu-id="bd70d-123">Aşağıdaki kod derlenir `In.vb` ve bir .ico simge dosyası ekler `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="bd70d-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd70d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd70d-124">See also</span></span>

- [<span data-ttu-id="bd70d-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="bd70d-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="bd70d-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="bd70d-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: /win32icon
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65149c617220966bc3bb6897d757a71cd60167d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="win32icon"></a><span data-ttu-id="7c29b-102">/win32icon</span><span class="sxs-lookup"><span data-stu-id="7c29b-102">/win32icon</span></span>
<span data-ttu-id="7c29b-103">Bir .ico dosyasını çıktı dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="7c29b-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="7c29b-104">Çıktı dosyasında bu .ico dosyasını temsil eden **dosya Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="7c29b-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c29b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c29b-105">Syntax</span></span>  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="7c29b-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="7c29b-106">Arguments</span></span>  
  
|<span data-ttu-id="7c29b-107">Terim</span><span class="sxs-lookup"><span data-stu-id="7c29b-107">Term</span></span>|<span data-ttu-id="7c29b-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="7c29b-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="7c29b-109">Çıkış dosyanızın eklemek için .ico dosyasını.</span><span class="sxs-lookup"><span data-stu-id="7c29b-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="7c29b-110">Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="7c29b-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c29b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c29b-111">Remarks</span></span>  
 <span data-ttu-id="7c29b-112">Microsoft Windows Kaynak Derleyici (RC) ile bir .ico dosyasını oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c29b-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="7c29b-113">Kaynak derleyicisi bir Visual C++ programını derleme yaparken çağrılır; .rc dosyasından bir .ico dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7c29b-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="7c29b-114">`/win32icon` Ve `/win32resource` seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="7c29b-114">The `/win32icon` and `/win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="7c29b-115">Bkz: [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) başvurusu için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası veya [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) eklemek için bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="7c29b-115">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="7c29b-116">Bkz: [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res dosyasını içeri aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="7c29b-116">See [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="7c29b-117">/ Win32icon Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7c29b-117">To set /win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="7c29b-118">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="7c29b-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7c29b-119">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="7c29b-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="7c29b-120">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="7c29b-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="7c29b-121">2.  Tıklatın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="7c29b-121">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="7c29b-122">3.  Değer değiştirme **simgesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="7c29b-122">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7c29b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c29b-123">Example</span></span>  
 <span data-ttu-id="7c29b-124">Aşağıdaki kod derlerken `In.vb` ve bir .ico dosyasını ekler `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="7c29b-124">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c29b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c29b-125">See Also</span></span>  
 [<span data-ttu-id="7c29b-126">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7c29b-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7c29b-127">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="7c29b-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

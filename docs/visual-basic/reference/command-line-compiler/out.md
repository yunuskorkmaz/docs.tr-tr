---
title: -out (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cc3779f9efda8cf48107a7c16e31f8ff05a456d
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-out-visual-basic"></a><span data-ttu-id="ac266-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac266-102">-out (Visual Basic)</span></span>
<span data-ttu-id="ac266-103">Çıktı dosyası adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac266-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac266-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac266-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac266-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ac266-105">Arguments</span></span>  
  
|<span data-ttu-id="ac266-106">Terim</span><span class="sxs-lookup"><span data-stu-id="ac266-106">Term</span></span>|<span data-ttu-id="ac266-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="ac266-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="ac266-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ac266-108">Required.</span></span> <span data-ttu-id="ac266-109">Derleyici çıktı dosyası adını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac266-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="ac266-110">Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="ac266-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac266-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac266-111">Remarks</span></span>  
 <span data-ttu-id="ac266-112">Tam adı ve uzantısı oluşturmak için dosya belirtin.</span><span class="sxs-lookup"><span data-stu-id="ac266-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="ac266-113">Bunu yapmazsanız, .exe dosya gelen kaynak kodu içeren dosyanın adını alır `Sub Main` yordamı ve .dll dosyasının ilk kaynak kod dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="ac266-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="ac266-114">Bir .exe veya .dll uzantısı olmadan dosya adı belirtirseniz, derleyici uzantısını otomatik sizin için belirtilen değer bağlı olarak ekler `-target` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ac266-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="ac266-115">-Out Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ac266-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ac266-116">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="ac266-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ac266-117">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="ac266-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ac266-118">2.  Tıklatın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="ac266-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="ac266-119">3.  Değer değiştirme **derleme adı** kutusu.</span><span class="sxs-lookup"><span data-stu-id="ac266-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ac266-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac266-120">Example</span></span>  
 <span data-ttu-id="ac266-121">Aşağıdaki kod derlerken `T2.vb` ve çıktı dosyası oluşturur `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="ac266-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac266-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac266-122">See Also</span></span>  
 [<span data-ttu-id="ac266-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ac266-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ac266-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac266-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="ac266-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ac266-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

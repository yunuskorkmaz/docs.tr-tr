---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 5dcf9dc5cc0987e965aba7fd2b8821252e19a655
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815998"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="1f9da-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f9da-102">-out (Visual Basic)</span></span>
<span data-ttu-id="1f9da-103">Çıkış dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f9da-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f9da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f9da-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f9da-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f9da-105">Arguments</span></span>  
  
|<span data-ttu-id="1f9da-106">Terim</span><span class="sxs-lookup"><span data-stu-id="1f9da-106">Term</span></span>|<span data-ttu-id="1f9da-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="1f9da-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="1f9da-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1f9da-108">Required.</span></span> <span data-ttu-id="1f9da-109">Derleyici çıktı dosyası adını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1f9da-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="1f9da-110">Dosya adı boşluk içeriyorsa adı tırnak içine alın. ("").</span><span class="sxs-lookup"><span data-stu-id="1f9da-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f9da-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f9da-111">Remarks</span></span>  
 <span data-ttu-id="1f9da-112">Oluşturulacak dosyanın uzantısı ve tam adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="1f9da-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="1f9da-113">Bunu yapmazsanız, .exe dosyasını dan kaynak kodu içeren dosyanın adını alır. `Sub Main` yordam ve .dll dosyası ilk kaynak kodu dosyasından adını alır.</span><span class="sxs-lookup"><span data-stu-id="1f9da-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="1f9da-114">Bir .exe veya .dll uzantısı olmadan bir dosya adı belirtirseniz, derleyicinin uzantısını otomatik sizin için belirtilen değer bağlı olarak ekler `-target` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="1f9da-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="1f9da-115">-Out Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1f9da-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1f9da-116">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="1f9da-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1f9da-117">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1f9da-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1f9da-118">2.  Tıklayın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="1f9da-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="1f9da-119">3.  Değer değiştirme **derleme adı** kutusu.</span><span class="sxs-lookup"><span data-stu-id="1f9da-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f9da-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f9da-120">Example</span></span>  
 <span data-ttu-id="1f9da-121">Aşağıdaki kod derlenir `T2.vb` ve çıktı dosyası oluşturur `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="1f9da-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f9da-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f9da-122">See also</span></span>

- [<span data-ttu-id="1f9da-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="1f9da-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="1f9da-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f9da-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="1f9da-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="1f9da-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

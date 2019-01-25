---
title: -LIBPATH
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: 6285deb97b05659283071b8940fe8730890b98e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609869"
---
# <a name="-libpath"></a><span data-ttu-id="d53fc-102">-LIBPATH</span><span class="sxs-lookup"><span data-stu-id="d53fc-102">-libpath</span></span>
<span data-ttu-id="d53fc-103">Başvurulan bütünleştirilmiş kodların konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d53fc-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d53fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d53fc-104">Syntax</span></span>  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="d53fc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d53fc-105">Arguments</span></span>  
  
|<span data-ttu-id="d53fc-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d53fc-106">Term</span></span>|<span data-ttu-id="d53fc-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d53fc-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="d53fc-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d53fc-108">Required.</span></span> <span data-ttu-id="d53fc-109">Sahipse başvurulan bir derleme aramak derleyicinin dizinlerin noktalı virgülle ayrılmış listesi bulunamadı veya geçerli çalışma dizinine (içinden, derleyiciyi çağırdığınız dizin) veya ortak dil çalışma zamanının sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="d53fc-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="d53fc-110">Dizin adı boşluk içeriyorsa adı tırnak içine alın. ("").</span><span class="sxs-lookup"><span data-stu-id="d53fc-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d53fc-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d53fc-111">Remarks</span></span>  
 <span data-ttu-id="d53fc-112">`-libpath` Seçeneği tarafından başvurulan derlemelerin konumunu belirten [-başvuru](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d53fc-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="d53fc-113">Derleyici şu sıralamadaki tam olmayan bütünleştirilmiş kod başvuruları arar:</span><span class="sxs-lookup"><span data-stu-id="d53fc-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="d53fc-114">Geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="d53fc-114">Current working directory.</span></span> <span data-ttu-id="d53fc-115">Bu, derleyicinin çağırıldığı dizinidir.</span><span class="sxs-lookup"><span data-stu-id="d53fc-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="d53fc-116">Ortak dil çalışma zamanı sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="d53fc-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="d53fc-117">Tarafından belirtilen dizinlerde `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="d53fc-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="d53fc-118">LIB ortam değişkeni tarafından belirtilen dizinler.</span><span class="sxs-lookup"><span data-stu-id="d53fc-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="d53fc-119">`-libpath` Eklenebilir; belirtme seçeneği, birden çok kez önceki tüm değerlere ekler.</span><span class="sxs-lookup"><span data-stu-id="d53fc-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="d53fc-120">Kullanım `-reference` bir bütünleştirilmiş kod başvurusu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="d53fc-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="d53fc-121">/ Libpath Visual Studio'da ayarlamak için tümleşik geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="d53fc-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d53fc-122">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="d53fc-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d53fc-123">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d53fc-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d53fc-124">2.  Tıklayın **başvuruları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="d53fc-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="d53fc-125">3.  Tıklayın **başvuru yolları...**  düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d53fc-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="d53fc-126">4.  İçinde **başvuru yolları** iletişim kutusunda, dizin adı girin **klasör:** kutusu.</span><span class="sxs-lookup"><span data-stu-id="d53fc-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="d53fc-127">5.  Tıklayın **klasörü Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d53fc-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d53fc-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="d53fc-128">Example</span></span>  
 <span data-ttu-id="d53fc-129">Aşağıdaki kod derlenir `T2.vb` bir .exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d53fc-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="d53fc-130">Derleyici, derleme başvuruları için çalışma dizininde, C: sürücüsünün kök dizinindeki ve C: sürücüsünde yeni derlemeler dizininde arar.</span><span class="sxs-lookup"><span data-stu-id="d53fc-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d53fc-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d53fc-131">See also</span></span>
- [<span data-ttu-id="d53fc-132">Derlemeler ve Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="d53fc-132">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [<span data-ttu-id="d53fc-133">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d53fc-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d53fc-134">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d53fc-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

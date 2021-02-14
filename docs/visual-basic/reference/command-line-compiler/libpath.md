---
description: :-Libpath hakkında daha fazla bilgi edinin
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: cdc3f557e0d069930032ac3b0af7a0e88762189d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455684"
---
# <a name="-libpath"></a><span data-ttu-id="a0c5b-103">-libpath</span><span class="sxs-lookup"><span data-stu-id="a0c5b-103">-libpath</span></span>

<span data-ttu-id="a0c5b-104">Başvurulan derlemelerin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-104">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c5b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a0c5b-105">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="a0c5b-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a0c5b-106">Arguments</span></span>  
  
|<span data-ttu-id="a0c5b-107">Terim</span><span class="sxs-lookup"><span data-stu-id="a0c5b-107">Term</span></span>|<span data-ttu-id="a0c5b-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="a0c5b-108">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="a0c5b-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-109">Required.</span></span> <span data-ttu-id="a0c5b-110">Başvurulan bir derlemenin geçerli çalışma dizininde (derleyicisini çağırmakta olduğunuz dizin) veya ortak dil çalışma zamanının sistem dizininde bulunamaması halinde, derleyicinin aranacağı dizinlerin noktalı virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-110">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="a0c5b-111">Dizin adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-111">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0c5b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0c5b-112">Remarks</span></span>  

 <span data-ttu-id="a0c5b-113">`-libpath`Seçeneği, [-Reference](reference.md) seçeneğinin başvurduğu derlemelerin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-113">The `-libpath` option specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>  
  
 <span data-ttu-id="a0c5b-114">Derleyici, aşağıdaki sırada tam olarak nitelenen derleme başvurularını arar:</span><span class="sxs-lookup"><span data-stu-id="a0c5b-114">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="a0c5b-115">Geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-115">Current working directory.</span></span> <span data-ttu-id="a0c5b-116">Bu, derleyicinin çağrıldığı dizindir.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-116">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="a0c5b-117">Ortak dil çalışma zamanı sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-117">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="a0c5b-118">Tarafından belirtilen dizinler `-libpath` .</span><span class="sxs-lookup"><span data-stu-id="a0c5b-118">Directories specified by `-libpath`.</span></span>  
  
4. <span data-ttu-id="a0c5b-119">LıB ortam değişkeni tarafından belirtilen dizinler.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-119">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="a0c5b-120">`-libpath`Seçenek eklenebilir; bir defadan fazla belirtmek önceki değerlere ekler.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-120">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="a0c5b-121">`-reference`Derleme başvurusunu belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-121">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="a0c5b-122">Visual Studio tümleşik geliştirme ortamında Set-libpath</span><span class="sxs-lookup"><span data-stu-id="a0c5b-122">To set -libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="a0c5b-123">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-123">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a0c5b-124">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-124">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="a0c5b-125">2. **Başvurular** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="a0c5b-126">3. **başvuru yolları...** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="a0c5b-127">4. **başvuru yolları** iletişim kutusunda dizin adını **klasör:** kutusuna girin.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="a0c5b-128">5. **Klasör Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a0c5b-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0c5b-129">Example</span></span>  

 <span data-ttu-id="a0c5b-130">Aşağıdaki kod, `T2.vb` bir. exe dosyası oluşturmak için derlenir.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="a0c5b-131">Derleyici, C: sürücüsünün kök dizininde ve derleme başvuruları için C: sürücüsünün yeni derlemeler dizininde çalışma dizinine bakar.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0c5b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0c5b-132">See also</span></span>

- [<span data-ttu-id="a0c5b-133">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="a0c5b-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="a0c5b-134">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a0c5b-134">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a0c5b-135">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a0c5b-135">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

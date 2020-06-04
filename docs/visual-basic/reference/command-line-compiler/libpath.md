---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: dff7e0c3eb696b9b18f4c4e59240a26c1cb9782c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408555"
---
# <a name="-libpath"></a><span data-ttu-id="3619d-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="3619d-102">-libpath</span></span>
<span data-ttu-id="3619d-103">Başvurulan derlemelerin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3619d-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3619d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3619d-104">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="3619d-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="3619d-105">Arguments</span></span>  
  
|<span data-ttu-id="3619d-106">Terim</span><span class="sxs-lookup"><span data-stu-id="3619d-106">Term</span></span>|<span data-ttu-id="3619d-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="3619d-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="3619d-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3619d-108">Required.</span></span> <span data-ttu-id="3619d-109">Başvurulan bir derlemenin geçerli çalışma dizininde (derleyicisini çağırmakta olduğunuz dizin) veya ortak dil çalışma zamanının sistem dizininde bulunamaması halinde, derleyicinin aranacağı dizinlerin noktalı virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="3619d-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="3619d-110">Dizin adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="3619d-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3619d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3619d-111">Remarks</span></span>  
 <span data-ttu-id="3619d-112">`-libpath`Seçeneği, [-Reference](reference.md) seçeneğinin başvurduğu derlemelerin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3619d-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>  
  
 <span data-ttu-id="3619d-113">Derleyici, aşağıdaki sırada tam olarak nitelenen derleme başvurularını arar:</span><span class="sxs-lookup"><span data-stu-id="3619d-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="3619d-114">Geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="3619d-114">Current working directory.</span></span> <span data-ttu-id="3619d-115">Bu, derleyicinin çağrıldığı dizindir.</span><span class="sxs-lookup"><span data-stu-id="3619d-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="3619d-116">Ortak dil çalışma zamanı sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="3619d-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="3619d-117">Tarafından belirtilen dizinler `-libpath` .</span><span class="sxs-lookup"><span data-stu-id="3619d-117">Directories specified by `-libpath`.</span></span>  
  
4. <span data-ttu-id="3619d-118">LıB ortam değişkeni tarafından belirtilen dizinler.</span><span class="sxs-lookup"><span data-stu-id="3619d-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="3619d-119">`-libpath`Seçenek eklenebilir; bir defadan fazla belirtmek önceki değerlere ekler.</span><span class="sxs-lookup"><span data-stu-id="3619d-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="3619d-120">`-reference`Derleme başvurusunu belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3619d-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="3619d-121">Visual Studio tümleşik geliştirme ortamında Set-libpath</span><span class="sxs-lookup"><span data-stu-id="3619d-121">To set -libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="3619d-122">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3619d-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3619d-123">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3619d-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="3619d-124">2. **Başvurular** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3619d-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="3619d-125">3. **başvuru yolları...** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3619d-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="3619d-126">4. **başvuru yolları** iletişim kutusunda dizin adını **klasör:** kutusuna girin.</span><span class="sxs-lookup"><span data-stu-id="3619d-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="3619d-127">5. **Klasör Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3619d-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3619d-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3619d-128">Example</span></span>  
 <span data-ttu-id="3619d-129">Aşağıdaki kod, `T2.vb` bir. exe dosyası oluşturmak için derlenir.</span><span class="sxs-lookup"><span data-stu-id="3619d-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="3619d-130">Derleyici, C: sürücüsünün kök dizininde ve derleme başvuruları için C: sürücüsünün yeni derlemeler dizininde çalışma dizinine bakar.</span><span class="sxs-lookup"><span data-stu-id="3619d-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3619d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3619d-131">See also</span></span>

- [<span data-ttu-id="3619d-132">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="3619d-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="3619d-133">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3619d-133">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3619d-134">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3619d-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

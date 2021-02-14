---
description: Hakkında daha fazla bilgi edinin:-win32icon
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 32a46771012708a42beb5450d28daf2fbab3f1c0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433555"
---
# <a name="-win32icon"></a><span data-ttu-id="d9ef3-103">-win32icon</span><span class="sxs-lookup"><span data-stu-id="d9ef3-103">-win32icon</span></span>

<span data-ttu-id="d9ef3-104">Çıkış dosyasına bir. ico dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-104">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="d9ef3-105">Bu. ico dosyası, **Dosya Gezgini**'nde çıkış dosyasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-105">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ef3-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d9ef3-106">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d9ef3-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="d9ef3-107">Arguments</span></span>  
  
|<span data-ttu-id="d9ef3-108">Terim</span><span class="sxs-lookup"><span data-stu-id="d9ef3-108">Term</span></span>|<span data-ttu-id="d9ef3-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="d9ef3-109">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="d9ef3-110">Çıkış dosyanıza eklenecek. ico dosyası.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-110">The .ico file to add to your output file.</span></span> <span data-ttu-id="d9ef3-111">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9ef3-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9ef3-112">Remarks</span></span>  

 <span data-ttu-id="d9ef3-113">Microsoft Windows Kaynak derleyicisi (RC) ile bir. ico dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-113">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="d9ef3-114">Visual C++ programı derlerken kaynak derleyicisi çağrılır; . ico dosyası. rc dosyasından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-114">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="d9ef3-115">`-win32icon`Ve `-win32resource` seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-115">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="d9ef3-116">Bir .NET Framework kaynak dosyasına başvurmak için bkz. [-linkresource (Visual Basic)](linkresource.md) veya .NET Framework kaynak dosyası iliştirmek için [-Resource (Visual Basic)](resource.md) .</span><span class="sxs-lookup"><span data-stu-id="d9ef3-116">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="d9ef3-117">. Res dosyasını içeri aktarmak için bkz. [-Win32Resource](win32resource.md) .</span><span class="sxs-lookup"><span data-stu-id="d9ef3-117">See [-win32resource](win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="d9ef3-118">Visual Studio IDE 'de set-win32icon</span><span class="sxs-lookup"><span data-stu-id="d9ef3-118">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d9ef3-119">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d9ef3-120">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d9ef3-121">2. **uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-121">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="d9ef3-122">3. **simge** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-122">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d9ef3-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9ef3-123">Example</span></span>  

 <span data-ttu-id="d9ef3-124">Aşağıdaki kod `In.vb` bir. ico dosyasını derler ve iliştirir `Rf.ico` .</span><span class="sxs-lookup"><span data-stu-id="d9ef3-124">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9ef3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9ef3-125">See also</span></span>

- [<span data-ttu-id="d9ef3-126">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d9ef3-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d9ef3-127">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d9ef3-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

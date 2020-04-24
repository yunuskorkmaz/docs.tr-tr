---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 6b4b69d227c857442de6857fac023090b3698e81
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004637"
---
# <a name="-win32icon"></a><span data-ttu-id="51322-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="51322-102">-win32icon</span></span>
<span data-ttu-id="51322-103">Çıkış dosyasına bir. ico dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="51322-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="51322-104">Bu. ico dosyası, **Dosya Gezgini**'nde çıkış dosyasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="51322-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51322-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51322-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="51322-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="51322-106">Arguments</span></span>  
  
|<span data-ttu-id="51322-107">Sözleşme Dönemi</span><span class="sxs-lookup"><span data-stu-id="51322-107">Term</span></span>|<span data-ttu-id="51322-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="51322-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="51322-109">Çıkış dosyanıza eklenecek. ico dosyası.</span><span class="sxs-lookup"><span data-stu-id="51322-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="51322-110">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="51322-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51322-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51322-111">Remarks</span></span>  
 <span data-ttu-id="51322-112">Microsoft Windows Kaynak derleyicisi (RC) ile bir. ico dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51322-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="51322-113">Visual C++ programı derlerken kaynak derleyicisi çağrılır; . ico dosyası. rc dosyasından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="51322-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="51322-114">`-win32icon` Ve `-win32resource` seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="51322-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="51322-115">Bir .NET Framework kaynak dosyasına başvurmak için bkz. [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) veya .NET Framework kaynak dosyası iliştirmek için [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) .</span><span class="sxs-lookup"><span data-stu-id="51322-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="51322-116">. Res dosyasını içeri aktarmak için bkz. [-Win32Resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .</span><span class="sxs-lookup"><span data-stu-id="51322-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="51322-117">Visual Studio IDE 'de set-win32icon</span><span class="sxs-lookup"><span data-stu-id="51322-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="51322-118">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51322-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="51322-119">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="51322-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="51322-120">2. **uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="51322-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="51322-121">3. **simge** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="51322-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51322-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="51322-122">Example</span></span>  
 <span data-ttu-id="51322-123">Aşağıdaki kod bir. `In.vb` ico dosyasını derler ve iliştirir `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="51322-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="51322-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51322-124">See also</span></span>

- [<span data-ttu-id="51322-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="51322-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="51322-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="51322-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
description: -win32icon (C# derleyici seçenekleri)
title: -win32icon (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 5b62bbfe28bb5aa82605a88a83cf82eff9278807
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168874"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="f86c8-103">-win32icon (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f86c8-103">-win32icon (C# Compiler Options)</span></span>

<span data-ttu-id="f86c8-104">**-Win32icon** seçeneği çıkış dosyasına bir. ico dosyası ekler ve bu, çıktı dosyasına dosya Gezgini 'nde istenen görünümü verir.</span><span class="sxs-lookup"><span data-stu-id="f86c8-104">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86c8-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f86c8-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="f86c8-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="f86c8-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="f86c8-107">Çıkış dosyanıza eklemek istediğiniz. ico dosyası.</span><span class="sxs-lookup"><span data-stu-id="f86c8-107">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f86c8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f86c8-108">Remarks</span></span>  

 <span data-ttu-id="f86c8-109">[Kaynak derleyicisi](/windows/desktop/menurc/resource-compiler)ile bir. ico dosyası oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="f86c8-109">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="f86c8-110">Visual C++ programı derlerken kaynak derleyicisi çağrılır; . ico dosyası. rc dosyasından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f86c8-110">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="f86c8-111">Bir .NET Framework kaynak dosyası için bkz. [-linkresource](./linkresource-compiler-option.md) (başvuruya) veya [-Resource](./resource-compiler-option.md) (iliştirilecek).</span><span class="sxs-lookup"><span data-stu-id="f86c8-111">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="f86c8-112">. Res dosyasını içeri aktarmak için bkz. [-win32res](./win32res-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="f86c8-112">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f86c8-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="f86c8-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f86c8-114">Projenin **Özellikler** sayfalarını açın.</span><span class="sxs-lookup"><span data-stu-id="f86c8-114">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="f86c8-115">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f86c8-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="f86c8-116">**Uygulama simgesi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f86c8-116">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="f86c8-117">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A> ..</span><span class="sxs-lookup"><span data-stu-id="f86c8-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f86c8-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f86c8-118">Example</span></span>  

 <span data-ttu-id="f86c8-119">`in.cs`Üretmek için bir. ico dosyası derleyin ve ekleyin `rf.ico` `in.exe` :</span><span class="sxs-lookup"><span data-stu-id="f86c8-119">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f86c8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f86c8-120">See also</span></span>

- [<span data-ttu-id="f86c8-121">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f86c8-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f86c8-122">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="f86c8-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

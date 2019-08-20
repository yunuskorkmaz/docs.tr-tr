---
title: -win32icon (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606280"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="1f875-102">-win32icon (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1f875-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="1f875-103">**-Win32icon** seçeneği çıkış dosyasına bir. ico dosyası ekler ve bu, çıktı dosyasına dosya Gezgini 'nde istenen görünümü verir.</span><span class="sxs-lookup"><span data-stu-id="1f875-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f875-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f875-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f875-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f875-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="1f875-106">Çıkış dosyanıza eklemek istediğiniz. ico dosyası.</span><span class="sxs-lookup"><span data-stu-id="1f875-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f875-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f875-107">Remarks</span></span>  
 <span data-ttu-id="1f875-108">[Kaynak derleyicisi](/windows/desktop/menurc/resource-compiler)ile bir. ico dosyası oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="1f875-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="1f875-109">Visual C++ program derlerken kaynak derleyicisi çağrılır; . ico dosyası. rc dosyasından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f875-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="1f875-110">Bir .NET Framework kaynak dosyası için bkz. [-linkresource](./linkresource-compiler-option.md) (başvuruya) veya [-Resource](./resource-compiler-option.md) (iliştirilecek).</span><span class="sxs-lookup"><span data-stu-id="1f875-110">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="1f875-111">. Res dosyasını içeri aktarmak için bkz. [-win32res](./win32res-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="1f875-111">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1f875-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1f875-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1f875-113">Projenin **Özellikler** sayfalarını açın.</span><span class="sxs-lookup"><span data-stu-id="1f875-113">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="1f875-114">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1f875-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="1f875-115">**Uygulama simgesi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1f875-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="1f875-116">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f875-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f875-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f875-117">Example</span></span>  
 <span data-ttu-id="1f875-118">`rf.ico` Üretmek `in.cs` için`in.exe`bir. ico dosyası derleyin ve ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1f875-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f875-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f875-119">See also</span></span>

- [<span data-ttu-id="1f875-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1f875-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1f875-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="1f875-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

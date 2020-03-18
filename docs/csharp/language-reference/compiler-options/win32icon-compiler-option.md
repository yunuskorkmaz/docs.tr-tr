---
title: -win32icon (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606280"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="26fc9-102">-win32icon (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="26fc9-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="26fc9-103">**-win32icon** seçeneği çıktı dosyasına bir .ico dosyası ekler ve bu da çıktı dosyasına Dosya Gezgini'nde istenen görünümü verir.</span><span class="sxs-lookup"><span data-stu-id="26fc9-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26fc9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26fc9-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="26fc9-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="26fc9-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="26fc9-106">Çıktı dosyanıza eklemek istediğiniz .ico dosyası.</span><span class="sxs-lookup"><span data-stu-id="26fc9-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26fc9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26fc9-107">Remarks</span></span>  
 <span data-ttu-id="26fc9-108">[Kaynak Derleyicisi](/windows/desktop/menurc/resource-compiler)ile bir .ico dosyası oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="26fc9-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="26fc9-109">Visual C++ programı derlediğinizde Kaynak Derleyicisi çağrılır; .rc dosyasından bir .ico dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="26fc9-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="26fc9-110">[Bkz.-linkresource](./linkresource-compiler-option.md) (başvuru için) veya [-kaynak](./resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="26fc9-110">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="26fc9-111">[Bkz.-win32res](./win32res-compiler-option.md) bir .res dosyasını almak için.</span><span class="sxs-lookup"><span data-stu-id="26fc9-111">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="26fc9-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="26fc9-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="26fc9-113">Projenin **Özellikleri** sayfalarını açın.</span><span class="sxs-lookup"><span data-stu-id="26fc9-113">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="26fc9-114">**Uygulama** özelliği sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="26fc9-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="26fc9-115">Uygulama **simgesi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="26fc9-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="26fc9-116">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A></span><span class="sxs-lookup"><span data-stu-id="26fc9-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26fc9-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="26fc9-117">Example</span></span>  
 <span data-ttu-id="26fc9-118">Derlemek `in.cs` ve üretmek `rf.ico` `in.exe`için bir .ico dosyası eklemek:</span><span class="sxs-lookup"><span data-stu-id="26fc9-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="26fc9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26fc9-119">See also</span></span>

- [<span data-ttu-id="26fc9-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="26fc9-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="26fc9-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="26fc9-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

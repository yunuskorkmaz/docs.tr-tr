---
description: '-target: appcontainerexe (C# derleyici seçenekleri)'
title: '-target: appcontainerexe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: e4aa60ebc9dcc1a63b63863385b0ee9f13d6d78d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193744"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="27c09-103">-target: appcontainerexe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="27c09-103">-target:appcontainerexe (C# Compiler Options)</span></span>

<span data-ttu-id="27c09-104">**-Target: appcontainerexe** derleyici seçeneğini kullanırsanız, derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows çalıştırılabilir (. exe) dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27c09-104">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="27c09-105">Bu seçenek [-target: winexe](./target-winexe-compiler-option.md) ile eşdeğerdir, ancak Windows 8. x Mağazası uygulamaları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="27c09-105">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27c09-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="27c09-106">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="27c09-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27c09-107">Remarks</span></span>  

 <span data-ttu-id="27c09-108">Uygulamanın bir uygulama kapsayıcısında çalışmasını gerektirmek için, bu seçenek [taşınabilir yürütülebilir](/windows/desktop/Debug/pe-format) (PE) dosyasında bir bit ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27c09-108">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="27c09-109">Bu bit ayarlandığında, CreateProcess yöntemi bir uygulama kapsayıcısının dışında yürütülebilir dosyayı başlatmaya çalışırsa bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="27c09-109">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="27c09-110">[-Out](./out-compiler-option.md) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı [Main](../../programming-guide/main-and-command-args/index.md) metodunu içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="27c09-110">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="27c09-111">Bu seçeneği bir komut isteminde belirttiğinizde, yürütülebilir dosyayı oluşturmak için bir sonraki **dışarı** veya **-hedef** seçeneğine kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="27c09-111">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="27c09-112">Bu derleyici seçeneğini IDE içinde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="27c09-112">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="27c09-113">**Çözüm Gezgini**' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="27c09-113">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="27c09-114">**Uygulama** sekmesinde, **Çıkış türü** listesinde, **Windows Mağazası uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="27c09-114">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="27c09-115">Bu seçenek yalnızca Windows 8. x Mağazası uygulama şablonları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27c09-115">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="27c09-116">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..</span><span class="sxs-lookup"><span data-stu-id="27c09-116">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27c09-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="27c09-117">Example</span></span>  

 <span data-ttu-id="27c09-118">Aşağıdaki komut, `filename.cs` yalnızca bir uygulama kapsayıcısında çalıştırılabilen bir Windows yürütülebilir dosyası için derlenir.</span><span class="sxs-lookup"><span data-stu-id="27c09-118">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="27c09-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27c09-119">See also</span></span>

- [<span data-ttu-id="27c09-120">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="27c09-120">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="27c09-121">-target: winexe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="27c09-121">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="27c09-122">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="27c09-122">C# Compiler Options</span></span>](./index.md)

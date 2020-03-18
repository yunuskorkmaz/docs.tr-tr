---
title: -hedef:appcontainerexe (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204532"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="4d8a8-102">-hedef:appcontainerexe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4d8a8-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="4d8a8-103">**-target:appcontainerexe** derleyici seçeneğini kullanırsanız, derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows çalıştırılabilir (.exe) dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="4d8a8-104">Bu seçenek [-hedef:winexe'ye](./target-winexe-compiler-option.md) eşdeğerdir, ancak Windows 8.x Store uygulamaları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-104">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d8a8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d8a8-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="4d8a8-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d8a8-106">Remarks</span></span>  
 <span data-ttu-id="4d8a8-107">Uygulamanın bir uygulama kapsayıcısında çalışmasını gerektirmek için, bu seçenek [Taşınabilir Yürütülebilir](/windows/desktop/Debug/pe-format) (PE) dosyasında biraz ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="4d8a8-108">Bu bit ayarlandığında, CreateProcess yöntemi yürütülebilir dosyayı bir uygulama kapsayıcısının dışına başlatmaya çalışırsa bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="4d8a8-109">[-out](./out-compiler-option.md) seçeneğini kullanmadığınız sürece, çıktı dosyası adı [Ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-109">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="4d8a8-110">Bu seçeneği komut isteminde belirttiğiniz zaman, yürütülebilir dosyayı oluşturmak için bir sonraki **-out** **veya-hedef** seçeneğine kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="4d8a8-111">Bu derleyici seçeneğini IDE içinde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4d8a8-111">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="4d8a8-112">**Çözüm Gezgini'nde,** projenizin kısayol menüsünü açın ve ardından **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="4d8a8-113">**Uygulama** sekmesinde, **Çıktı türü** listesinde **Windows Mağazası Uygulamasını**seçin.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="4d8a8-114">Bu seçenek yalnızca Windows 8.x Store uygulama şablonları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-114">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="4d8a8-115">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A></span><span class="sxs-lookup"><span data-stu-id="4d8a8-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d8a8-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d8a8-116">Example</span></span>  
 <span data-ttu-id="4d8a8-117">Aşağıdaki komut, `filename.cs` yalnızca bir uygulama kapsayıcısında çalıştırılabilen bir Windows çalıştırılabilir dosyasında derler.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d8a8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d8a8-118">See also</span></span>

- [<span data-ttu-id="4d8a8-119">-hedef (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4d8a8-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="4d8a8-120">-hedef:winexe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4d8a8-120">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="4d8a8-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4d8a8-121">C# Compiler Options</span></span>](./index.md)

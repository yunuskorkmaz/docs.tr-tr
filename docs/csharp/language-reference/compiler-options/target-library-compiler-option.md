---
description: '-target: Library (C# derleyici seçenekleri)'
title: '-target: Library (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 953249c4d0168ed3d279d03a0b2fb63d8ff6d5f5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128484"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="463f5-103">-target: Library (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="463f5-103">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="463f5-104">**-Target: Library** seçeneği derleyicinin yürütülebilir dosya (exe) yerine bir dinamik bağlantı KITAPLıĞı (dll) oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="463f5-104">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="463f5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="463f5-105">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="463f5-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="463f5-106">Remarks</span></span>  
 <span data-ttu-id="463f5-107">DLL,. dll uzantısıyla oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="463f5-107">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="463f5-108">Aksi belirtilmediği [takdirde, çıkış](./out-compiler-option.md) dosyası adı ilk giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="463f5-108">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="463f5-109">Komut satırında belirtildiğinde, bir sonraki **-Out** veya **-target: Module** seçeneğine kadar olan tüm dosyalar,. dll dosyasını oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="463f5-109">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="463f5-110">Bir. dll dosyası oluştururken [Main](../../programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="463f5-110">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="463f5-111">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="463f5-111">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="463f5-112">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="463f5-112">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="463f5-113">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="463f5-113">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="463f5-114">**Çıktı türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="463f5-114">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="463f5-115">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..</span><span class="sxs-lookup"><span data-stu-id="463f5-115">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="463f5-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="463f5-116">Example</span></span>  
 <span data-ttu-id="463f5-117">Derle `in.cs` , oluşturma `in.dll` :</span><span class="sxs-lookup"><span data-stu-id="463f5-117">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="463f5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="463f5-118">See also</span></span>

- [<span data-ttu-id="463f5-119">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="463f5-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="463f5-120">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="463f5-120">C# Compiler Options</span></span>](./index.md)

---
title: '-target: Library (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606399"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="db197-102">-target: Library (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="db197-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="db197-103">**-Target: Library** seçeneği derleyicinin yürütülebilir dosya (exe) yerine bir dinamik bağlantı KITAPLıĞı (dll) oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="db197-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db197-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db197-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="db197-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db197-105">Remarks</span></span>  
 <span data-ttu-id="db197-106">DLL,. dll uzantısıyla oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="db197-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="db197-107">Aksi belirtilmediği takdirde, çıkış [](./out-compiler-option.md) dosyası adı ilk giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="db197-107">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="db197-108">Komut satırında belirtildiğinde, bir sonraki **-Out** veya **-target: Module** seçeneğine kadar olan tüm dosyalar,. dll dosyasını oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db197-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="db197-109">Bir. dll dosyası oluştururken [Main](../../programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="db197-109">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="db197-110">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="db197-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="db197-111">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="db197-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="db197-112">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="db197-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="db197-113">**Çıktı türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="db197-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="db197-114">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="db197-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db197-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="db197-115">Example</span></span>  
 <span data-ttu-id="db197-116">Derle `in.cs`, oluşturma `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="db197-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="db197-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db197-117">See also</span></span>

- [<span data-ttu-id="db197-118">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="db197-118">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="db197-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="db197-119">C# Compiler Options</span></span>](./index.md)

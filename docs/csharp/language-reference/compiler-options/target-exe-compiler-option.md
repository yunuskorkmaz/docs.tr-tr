---
title: '-target: exe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606459"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="e6888-102">-target: exe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e6888-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="e6888-103">**-Target: exe** seçeneği derleyicinin YÜRÜTÜLEBILIR (exe), konsol uygulaması oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e6888-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6888-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6888-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="e6888-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6888-105">Remarks</span></span>  
 <span data-ttu-id="e6888-106">**-Target: exe** seçeneği varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="e6888-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="e6888-107">Yürütülebilir dosya,. exe uzantısıyla oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="e6888-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="e6888-108">Bir Windows program yürütülebilir dosyası oluşturmak için [-target: winexe](./target-winexe-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6888-108">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="e6888-109">Aksi belirtilmedikçe, çıkış dosyası [](./out-compiler-option.md) adı, [ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="e6888-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="e6888-110">Komut satırında belirtildiğinde, bir sonraki **-Out** veya **-target: Module** seçeneğine kadar olan tüm dosyalar,. exe dosyasını oluşturmak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="e6888-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="e6888-111">Bir. exe dosyasına derlenen kaynak kodu dosyalarında bir ve yalnızca bir **ana** Yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e6888-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="e6888-112">[-Main](./main-compiler-option.md) derleyici seçeneği, kodunuzun bir **Main** yöntemi olan birden fazla sınıfa sahip olduğu durumlarda **Main** yöntemini hangi sınıfın içerdiğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6888-112">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e6888-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e6888-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="e6888-114">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="e6888-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="e6888-115">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e6888-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="e6888-116">**Çıktı türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e6888-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="e6888-117">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6888-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6888-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6888-118">Example</span></span>  
 <span data-ttu-id="e6888-119">Aşağıdaki komut satırlarından her biri derler `in.cs`, şunu oluşturur: `in.exe`</span><span class="sxs-lookup"><span data-stu-id="e6888-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6888-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6888-120">See also</span></span>

- [<span data-ttu-id="e6888-121">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e6888-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="e6888-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e6888-122">C# Compiler Options</span></span>](./index.md)

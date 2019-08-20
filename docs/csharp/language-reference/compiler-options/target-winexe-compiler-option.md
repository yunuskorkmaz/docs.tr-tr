---
title: '-target: winexe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606384"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="45f63-102">-target: winexe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="45f63-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="45f63-103">**-Target: winexe** seçeneği derleyicinin YÜRÜTÜLEBILIR (exe), Windows programı oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="45f63-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f63-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45f63-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="45f63-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45f63-105">Remarks</span></span>  
 <span data-ttu-id="45f63-106">Yürütülebilir dosya,. exe uzantısıyla oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="45f63-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="45f63-107">Windows programı, .NET Framework kitaplığından veya Windows API 'Leriyle bir kullanıcı arabirimi sağlayan bir programdır.</span><span class="sxs-lookup"><span data-stu-id="45f63-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="45f63-108">Bir konsol uygulaması oluşturmak için [-target: exe](./target-exe-compiler-option.md) ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="45f63-108">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="45f63-109">Aksi belirtilmedikçe, çıkış dosyası [](./out-compiler-option.md) adı, [ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="45f63-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="45f63-110">Komut satırında belirtildiğinde, Windows programını oluşturmak için sonraki **dışarı** veya [-hedef](./target-compiler-option.md) seçeneğine kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45f63-110">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="45f63-111">Bir. exe dosyasına derlenen kaynak kodu dosyalarında bir ve yalnızca bir **ana** Yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="45f63-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="45f63-112">[-Main](./main-compiler-option.md) seçeneği, kodunuzun bir **Main** yöntemi olan birden fazla sınıfa sahip olduğu durumlarda, hangi sınıfın **ana** yöntemi içerdiğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="45f63-112">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="45f63-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="45f63-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="45f63-114">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="45f63-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="45f63-115">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="45f63-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="45f63-116">**Çıktı türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="45f63-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="45f63-117">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="45f63-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f63-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="45f63-118">Example</span></span>  
 <span data-ttu-id="45f63-119">Bir `in.cs` Windows programında derle:</span><span class="sxs-lookup"><span data-stu-id="45f63-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="45f63-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45f63-120">See also</span></span>

- [<span data-ttu-id="45f63-121">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="45f63-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="45f63-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="45f63-122">C# Compiler Options</span></span>](./index.md)

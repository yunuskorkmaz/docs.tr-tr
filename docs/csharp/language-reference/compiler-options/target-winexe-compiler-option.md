---
title: -hedef:winexe (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606384"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="6f9b0-102">-hedef:winexe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6f9b0-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="6f9b0-103">**-target:winexe** seçeneği derleyicinin çalıştırılabilir (EXE), Windows programı oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f9b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f9b0-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="6f9b0-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f9b0-105">Remarks</span></span>  
 <span data-ttu-id="6f9b0-106">Çalıştırılabilir dosya .exe uzantısı ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="6f9b0-107">Windows programı, .NET Framework kitaplığından veya Windows API'lerinden kullanıcı arabirimi sağlayan programdır.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="6f9b0-108">Konsol uygulaması oluşturmak için [-target:exe'yi](./target-exe-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-108">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="6f9b0-109">[-out](./out-compiler-option.md) seçeneğinde aksi belirtilmedikçe, çıktı dosyası adı [Ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="6f9b0-110">Komut satırında belirtildiğinde, Windows programını oluşturmak için bir sonraki **-out** [veya-hedef](./target-compiler-option.md) seçeneğine kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-110">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="6f9b0-111">.exe dosyasında derlenen kaynak kod dosyalarında bir ve tek bir **Ana** yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="6f9b0-112">[-ana](./main-compiler-option.md) seçenek, kodunuzu **bir Ana** yöntem ile birden fazla sınıf ait olduğu durumlarda, Hangi sınıfın **Ana** yöntemi içerdiğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-112">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6f9b0-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6f9b0-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6f9b0-114">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="6f9b0-115">**Uygulama** özelliği sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="6f9b0-116">Çıktı **türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="6f9b0-117">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A></span><span class="sxs-lookup"><span data-stu-id="6f9b0-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f9b0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f9b0-118">Example</span></span>  
 <span data-ttu-id="6f9b0-119">Bir `in.cs` Windows programına derleme:</span><span class="sxs-lookup"><span data-stu-id="6f9b0-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f9b0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f9b0-120">See also</span></span>

- [<span data-ttu-id="6f9b0-121">-hedef (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6f9b0-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="6f9b0-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6f9b0-122">C# Compiler Options</span></span>](./index.md)

---
title: '-target: winexe (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: f77137e3cc2f734435d3b1d391a303fcd3e16332
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273326"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="4912c-102">-target: winexe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4912c-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="4912c-103">**-Target: winexe** seçeneği bir yürütülebilir (EXE), Windows programı oluşturmak derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="4912c-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4912c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4912c-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="4912c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4912c-105">Remarks</span></span>  
 <span data-ttu-id="4912c-106">Yürütülebilir dosyanın .exe uzantısı ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4912c-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="4912c-107">Bir Windows ya da .NET Framework Kitaplığı'ndan veya Win32 API'ları ile bir kullanıcı arabirimi sağlayan bir programdır.</span><span class="sxs-lookup"><span data-stu-id="4912c-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="4912c-108">Kullanım [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) bir konsol uygulaması oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="4912c-108">Use [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="4912c-109">İle aksi belirtilmediği sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıkış dosyası adını içeren giriş dosyasının adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4912c-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="4912c-110">Tüm komut satırında belirtildiğinde kadar sonraki dosyalar **-out** veya [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) seçeneği, Windows programı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4912c-110">When specified at the command line, all files until the next **-out** or [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="4912c-111">Bir ve yalnızca bir **ana** yöntemi bir .exe dosyasına derlenir kaynak kodu dosyalarında gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4912c-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="4912c-112">[-Ana](../../../csharp/language-reference/compiler-options/main-compiler-option.md) seçeneği hangi sınıfı içeren belirtmenize olanak tanır **ana** yöntemi ile birden fazla sınıf kodunuzu sahip olduğu durumlarda bir **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4912c-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4912c-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4912c-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="4912c-114">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="4912c-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="4912c-115">Tıklayın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="4912c-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="4912c-116">Değiştirme **çıkış türü** özelliği.</span><span class="sxs-lookup"><span data-stu-id="4912c-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="4912c-117">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="4912c-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4912c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="4912c-118">Example</span></span>  
 <span data-ttu-id="4912c-119">Derleme `in.cs` Windows programı:</span><span class="sxs-lookup"><span data-stu-id="4912c-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4912c-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4912c-120">See Also</span></span>  

- [<span data-ttu-id="4912c-121">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4912c-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="4912c-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4912c-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

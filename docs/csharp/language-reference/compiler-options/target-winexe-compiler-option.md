---
title: "-target: winexe (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b13af4e665a2bf5a75472bc8f4a501e90c59281a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="e5d20-102">-target: winexe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e5d20-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="e5d20-103">**-Target: winexe** seçeneği bir yürütülebilir dosya (EXE), Windows programı oluşturmak derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="e5d20-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d20-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5d20-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="e5d20-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5d20-105">Remarks</span></span>  
 <span data-ttu-id="e5d20-106">Yürütülebilir dosyanın .exe uzantısı ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e5d20-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="e5d20-107">Bir .NET Framework kitaplığından veya Win32 API'ları ile bir kullanıcı arabirimi sağlayan bir programdır.</span><span class="sxs-lookup"><span data-stu-id="e5d20-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="e5d20-108">Kullanım [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) bir konsol uygulaması oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e5d20-108">Use [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="e5d20-109">İle aksi belirtilmediği sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adını içeren giriş dosyası adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e5d20-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="e5d20-110">Tüm komut satırında belirtildiğinde kadar sonraki dosyaları **-out** veya [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) seçeneği, Windows programı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5d20-110">When specified at the command line, all files until the next **-out** or [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="e5d20-111">Yalnızca tek **ana** yöntemi bir .exe dosyasına derlenmiş kaynak kodu dosyaları gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5d20-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="e5d20-112">[-Ana](../../../csharp/language-reference/compiler-options/main-compiler-option.md) seçeneği hangi sınıfı içeren belirtmenize olanak sağlar **ana** yöntemi ile birden fazla sınıf kodunuzu sahip olduğu durumlarda bir **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e5d20-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e5d20-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e5d20-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="e5d20-114">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="e5d20-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="e5d20-115">Tıklatın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="e5d20-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="e5d20-116">Değiştirme **çıktı türü** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e5d20-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="e5d20-117">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5d20-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5d20-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5d20-118">Example</span></span>  
 <span data-ttu-id="e5d20-119">Derleme `in.cs` bir Windows programı içine:</span><span class="sxs-lookup"><span data-stu-id="e5d20-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5d20-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5d20-120">See Also</span></span>  
 [<span data-ttu-id="e5d20-121">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e5d20-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="e5d20-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e5d20-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

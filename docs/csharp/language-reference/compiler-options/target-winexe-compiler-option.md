---
title: "-target: winexe (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e155c64689f34c89443c7ff0a3dee38d6c190fcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="targetwinexe-c-compiler-options"></a><span data-ttu-id="e78c8-102">/target:winexe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e78c8-102">/target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="e78c8-103">**/Target: winexe** seçeneği bir yürütülebilir dosya (EXE), Windows programı oluşturmak derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="e78c8-103">The **/target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e78c8-104">Syntax</span></span>  
  
```console  
/target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="e78c8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e78c8-105">Remarks</span></span>  
 <span data-ttu-id="e78c8-106">Yürütülebilir dosyanın .exe uzantısı ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e78c8-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="e78c8-107">Bir .NET Framework kitaplığından veya Win32 API'ları ile bir kullanıcı arabirimi sağlayan bir programdır.</span><span class="sxs-lookup"><span data-stu-id="e78c8-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="e78c8-108">Kullanım [/target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) bir konsol uygulaması oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e78c8-108">Use [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="e78c8-109">İle aksi belirtilmediği sürece [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adını içeren giriş dosyası adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e78c8-109">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="e78c8-110">Tüm komut satırında belirtildiğinde kadar sonraki dosyaları **/out** veya [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) seçeneği, Windows programı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e78c8-110">When specified at the command line, all files until the next **/out** or [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="e78c8-111">Yalnızca tek **ana** yöntemi bir .exe dosyasına derlenmiş kaynak kodu dosyaları gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e78c8-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="e78c8-112">[/Ana](../../../csharp/language-reference/compiler-options/main-compiler-option.md) seçeneği hangi sınıfı içeren belirtmenize olanak sağlar **ana** yöntemi ile birden fazla sınıf kodunuzu sahip olduğu durumlarda bir **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e78c8-112">The [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e78c8-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e78c8-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="e78c8-114">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="e78c8-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="e78c8-115">Tıklatın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="e78c8-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="e78c8-116">Değiştirme **çıktı türü** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e78c8-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="e78c8-117">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e78c8-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e78c8-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e78c8-118">Example</span></span>  
 <span data-ttu-id="e78c8-119">Derleme `in.cs` bir Windows programı içine:</span><span class="sxs-lookup"><span data-stu-id="e78c8-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc /target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e78c8-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e78c8-120">See Also</span></span>  
 [<span data-ttu-id="e78c8-121">/ target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e78c8-121">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="e78c8-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e78c8-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

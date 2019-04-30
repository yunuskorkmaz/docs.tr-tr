---
title: '-target: exe (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 7d34a25fd614a209761714e1f4eff3042ca240c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662406"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="1f426-102">-target: exe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1f426-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="1f426-103">**-Target: exe** seçeneği derleyicinin, konsol uygulaması yürütülebilir (EXE) oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1f426-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f426-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f426-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="1f426-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f426-105">Remarks</span></span>  
 <span data-ttu-id="1f426-106">**-Target: exe** seçeneği varsayılan olarak etkin olan.</span><span class="sxs-lookup"><span data-stu-id="1f426-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="1f426-107">Yürütülebilir dosyanın .exe uzantısı ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f426-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="1f426-108">Kullanım [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) Windows programı yürütülebilir oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1f426-108">Use [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="1f426-109">İle aksi belirtilmediği sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıkış dosyası adını içeren giriş dosyasının adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1f426-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="1f426-110">Tüm komut satırında belirtildiğinde kadar sonraki dosyalar **-out** veya **-target: module** seçeneği, .exe dosyasını oluşturmak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="1f426-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="1f426-111">Bir ve yalnızca bir **ana** yöntemi bir .exe dosyasına derlenir kaynak kodu dosyalarında gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1f426-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="1f426-112">[-Ana](../../../csharp/language-reference/compiler-options/main-compiler-option.md) derleyici seçeneği hangi sınıfı içeren belirtmenize olanak tanır **ana** yöntemi ile birden fazla sınıf kodunuzu sahip olduğu durumlarda bir **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1f426-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1f426-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1f426-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1f426-114">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="1f426-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="1f426-115">Tıklayın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="1f426-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="1f426-116">Değiştirme **çıkış türü** özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f426-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="1f426-117">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f426-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f426-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f426-118">Example</span></span>  
 <span data-ttu-id="1f426-119">Aşağıdaki komut satırlarını her derleyeceği `in.cs`, oluşturma `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="1f426-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f426-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f426-120">See also</span></span>

- [<span data-ttu-id="1f426-121">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1f426-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="1f426-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1f426-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

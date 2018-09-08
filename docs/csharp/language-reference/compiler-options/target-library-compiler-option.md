---
title: '-target: library (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: e15210d189c4a553da72b418f583e44666bac2fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201185"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="8c1d0-102">-target: library (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="8c1d0-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="8c1d0-103">**-Target: library** seçeneği bir yürütülebilir dosya (EXE) yerine bir dinamik bağlantı kitaplığı (DLL) oluşturmak derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c1d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c1d0-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="8c1d0-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c1d0-105">Remarks</span></span>  
 <span data-ttu-id="8c1d0-106">DLL, .dll uzantısıyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="8c1d0-107">İle aksi belirtilmediği sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıkış dosyası adı ilk giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-107">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="8c1d0-108">Tüm komut satırında belirtildiğinde kadar sonraki dosyalar **-out** veya **-target: module** seçeneği .dll dosyası oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="8c1d0-109">Bir .dll dosyası oluştururken bir [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-109">When building a .dll file, a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8c1d0-110">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8c1d0-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="8c1d0-111">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="8c1d0-112">Tıklayın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="8c1d0-113">Değiştirme **çıkış türü** özelliği.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="8c1d0-114">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c1d0-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c1d0-115">Example</span></span>  
 <span data-ttu-id="8c1d0-116">Derleme `in.cs`, oluşturma `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="8c1d0-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c1d0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c1d0-117">See Also</span></span>  

- [<span data-ttu-id="8c1d0-118">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="8c1d0-118">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="8c1d0-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8c1d0-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

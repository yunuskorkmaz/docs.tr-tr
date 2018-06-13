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
ms.openlocfilehash: 194e4f7efaebd9523791090bcab09c019f8554a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218835"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="0e13d-102">-target: exe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="0e13d-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="0e13d-103">**-Target: exe** seçeneği bir yürütülebilir dosya (EXE) oluşturmak için konsol uygulaması derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="0e13d-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e13d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e13d-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="0e13d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e13d-105">Remarks</span></span>  
 <span data-ttu-id="0e13d-106">**-Target: exe** seçeneği varsayılan olarak etkin olan.</span><span class="sxs-lookup"><span data-stu-id="0e13d-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="0e13d-107">Yürütülebilir dosyanın .exe uzantısı ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0e13d-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="0e13d-108">Kullanım [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) yürütülebilir bir Windows programı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0e13d-108">Use [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="0e13d-109">İle aksi belirtilmediği sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adını içeren giriş dosyası adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e13d-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="0e13d-110">Tüm komut satırında belirtildiğinde kadar sonraki dosyaları **-out** veya **-target: module** seçeneği .exe dosyası oluşturmak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="0e13d-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="0e13d-111">Yalnızca tek **ana** yöntemi bir .exe dosyasına derlenmiş kaynak kodu dosyaları gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0e13d-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="0e13d-112">[-Ana](../../../csharp/language-reference/compiler-options/main-compiler-option.md) derleyici seçeneği hangi sınıfı içeren belirtmenize olanak sağlar **ana** yöntemi ile birden fazla sınıf kodunuzu sahip olduğu durumlarda bir **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e13d-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0e13d-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0e13d-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="0e13d-114">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="0e13d-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="0e13d-115">Tıklatın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="0e13d-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="0e13d-116">Değiştirme **çıktı türü** özelliği.</span><span class="sxs-lookup"><span data-stu-id="0e13d-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="0e13d-117">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e13d-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e13d-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e13d-118">Example</span></span>  
 <span data-ttu-id="0e13d-119">Aşağıdaki komut satırlarını her derlenir `in.cs`, oluşturma `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="0e13d-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e13d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e13d-120">See Also</span></span>  
 [<span data-ttu-id="0e13d-121">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="0e13d-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="0e13d-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0e13d-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

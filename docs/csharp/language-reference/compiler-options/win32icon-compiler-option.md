---
title: "-win32icon (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2ec19bacb975732f2ae04b8cefbfaeaa518b6f15
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="74082-102">-win32icon (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="74082-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="74082-103">**-Win32icon** seçeneği çıkış dosyasını ve dosya Gezgini'ndeki istenen çalışmasıdır çıktı dosyasında bir .ico dosyasını ekler.</span><span class="sxs-lookup"><span data-stu-id="74082-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74082-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74082-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="74082-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="74082-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="74082-106">Çıkış dosyanızın eklemek istediğiniz .ico dosyasını.</span><span class="sxs-lookup"><span data-stu-id="74082-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74082-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74082-107">Remarks</span></span>  
 <span data-ttu-id="74082-108">Bir .ico dosyasını ile oluşturulan [kaynak derleyici](https://msdn.microsoft.com/library/aa381042.aspx).</span><span class="sxs-lookup"><span data-stu-id="74082-108">An .ico file can be created with the [Resource Compiler](https://msdn.microsoft.com/library/aa381042.aspx).</span></span> <span data-ttu-id="74082-109">Kaynak derleyicisi bir Visual C++ programını derleme yaparken çağrılır; .rc dosyasından bir .ico dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="74082-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="74082-110">Bkz: [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (için başvuru) veya [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="74082-110">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="74082-111">Bkz: [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) .res dosyasını içeri aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="74082-111">See [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="74082-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="74082-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="74082-113">Projenin açmak **özellikleri** sayfaları.</span><span class="sxs-lookup"><span data-stu-id="74082-113">Open the project's **Properties** pages.</span></span>  
  
2.  <span data-ttu-id="74082-114">Tıklatın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="74082-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="74082-115">Değiştirme **uygulama simgesi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="74082-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="74082-116">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="74082-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74082-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="74082-117">Example</span></span>  
 <span data-ttu-id="74082-118">Derleme `in.cs` ve bir .ico dosyasını ekleyin `rf.ico` üretmek için `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="74082-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="74082-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74082-119">See Also</span></span>  
 [<span data-ttu-id="74082-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="74082-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="74082-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="74082-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

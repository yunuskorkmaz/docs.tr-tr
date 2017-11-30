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
ms.openlocfilehash: 3f9419470d2f00a9f69aae24e925fea53d90cf10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="win32icon-c-compiler-options"></a><span data-ttu-id="40685-102">/win32icon (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="40685-102">/win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="40685-103">**/Win32icon** seçeneği çıkış dosyasını ve dosya Gezgini'ndeki istenen çalışmasıdır çıktı dosyasında bir .ico dosyasını ekler.</span><span class="sxs-lookup"><span data-stu-id="40685-103">The **/win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40685-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40685-104">Syntax</span></span>  
  
```console  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="40685-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="40685-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="40685-106">Çıkış dosyanızın eklemek istediğiniz .ico dosyasını.</span><span class="sxs-lookup"><span data-stu-id="40685-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40685-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40685-107">Remarks</span></span>  
 <span data-ttu-id="40685-108">Bir .ico dosyasını ile oluşturulan [kaynak derleyici](http://go.microsoft.com/fwlink/?LinkId=148370).</span><span class="sxs-lookup"><span data-stu-id="40685-108">An .ico file can be created with the [Resource Compiler](http://go.microsoft.com/fwlink/?LinkId=148370).</span></span> <span data-ttu-id="40685-109">Kaynak derleyicisi bir Visual C++ programını derleme yaparken çağrılır; .rc dosyasından bir .ico dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="40685-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="40685-110">Bkz: [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (için başvuru) veya [/Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="40685-110">See [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="40685-111">Bkz: [/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) .res dosyasını içeri aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="40685-111">See [/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="40685-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="40685-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="40685-113">Projenin açmak **özellikleri** sayfaları.</span><span class="sxs-lookup"><span data-stu-id="40685-113">Open the project's **Properties** pages.</span></span>  
  
2.  <span data-ttu-id="40685-114">Tıklatın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="40685-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="40685-115">Değiştirme **uygulama simgesi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="40685-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="40685-116">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="40685-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40685-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="40685-117">Example</span></span>  
 <span data-ttu-id="40685-118">Derleme `in.cs` ve bir .ico dosyasını ekleyin `rf.ico` üretmek için `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="40685-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc /win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="40685-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40685-119">See Also</span></span>  
 [<span data-ttu-id="40685-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="40685-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="40685-121">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="40685-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

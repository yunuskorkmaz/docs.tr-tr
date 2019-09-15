---
title: -addmodule (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970182"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="28736-102">-addmodule (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="28736-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="28736-103">Bu seçenek, target: Module anahtarı geçerli derlemeye ile oluşturulmuş bir modül ekler.</span><span class="sxs-lookup"><span data-stu-id="28736-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28736-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28736-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="28736-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="28736-105">Arguments</span></span>  
 <span data-ttu-id="28736-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="28736-106">`file`, `file2`</span></span>  
 <span data-ttu-id="28736-107">Meta veri içeren bir çıkış dosyası.</span><span class="sxs-lookup"><span data-stu-id="28736-107">An output file that contains metadata.</span></span> <span data-ttu-id="28736-108">Dosya, bütünleştirilmiş kod bildirimi içeremez.</span><span class="sxs-lookup"><span data-stu-id="28736-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="28736-109">Birden fazla dosyayı içeri aktarmak için, dosya adlarını virgülle veya noktalı virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="28736-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28736-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28736-110">Remarks</span></span>  
 <span data-ttu-id="28736-111">**-Addmodule** ile eklenen tüm modüller, çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28736-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="28736-112">Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="28736-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="28736-113">Modül, çalışma zamanında uygulama dizininde değilse, bir <xref:System.TypeLoadException>alırsınız.</span><span class="sxs-lookup"><span data-stu-id="28736-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="28736-114">`file`bütünleştirilmiş kod içeremez.</span><span class="sxs-lookup"><span data-stu-id="28736-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="28736-115">Örneğin, çıkış dosyası [-target: Module](./target-module-compiler-option.md)ile oluşturulduysa, meta verileri **-addmodule**ile içeri aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="28736-115">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="28736-116">Çıkış dosyası **-target: Module**dışında bir **-target** seçeneği ile oluşturulduysa, meta verileri **-addmodule** ile içeri aktarılamaz ancak [-Reference](./reference-compiler-option.md)ile içeri aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="28736-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="28736-117">Bu derleyici seçeneği Visual Studio 'da kullanılamaz; bir proje bir modüle başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="28736-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="28736-118">Ayrıca, bu derleyici seçeneği program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="28736-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28736-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="28736-119">Example</span></span>  
 <span data-ttu-id="28736-120">Kaynak dosyasını `input.cs` derleyin, ve ' `metad1.netmodule` `metad2.netmodule` dan meta verileri ekleyin `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="28736-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="28736-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28736-121">See also</span></span>

- [<span data-ttu-id="28736-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="28736-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="28736-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="28736-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="28736-124">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="28736-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="28736-125">Nasıl yapılır: Çoklu dosya derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="28736-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)

---
title: -addmodule (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: f45afd277818d7e1658751f2aae0b2153c940eee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617518"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="a7479-102">-addmodule (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a7479-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="a7479-103">Bu seçenek geçerli derleme için target: module anahtarı ile oluşturulmuş bir modül ekler.</span><span class="sxs-lookup"><span data-stu-id="a7479-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7479-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7479-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a7479-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a7479-105">Arguments</span></span>  
 <span data-ttu-id="a7479-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="a7479-106">`file`, `file2`</span></span>  
 <span data-ttu-id="a7479-107">Meta veriler içeren bir çıkış dosyası.</span><span class="sxs-lookup"><span data-stu-id="a7479-107">An output file that contains metadata.</span></span> <span data-ttu-id="a7479-108">Dosyanın bir derleme bildirimi içeremez.</span><span class="sxs-lookup"><span data-stu-id="a7479-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="a7479-109">Birden fazla dosya aktarmak için dosya adları virgül veya noktalı virgül ile ayırın.</span><span class="sxs-lookup"><span data-stu-id="a7479-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7479-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7479-110">Remarks</span></span>  
 <span data-ttu-id="a7479-111">İle eklenen tüm modüller **- addmodule** çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7479-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="a7479-112">Diğer bir deyişle, derleme zamanında bir modülün herhangi bir dizinini belirtebilirsiniz ancak modülü, çalışma zamanında uygulama dizininde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7479-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="a7479-113">Modül uygulama dizininde, çalışma zamanında değilse, erişmenizi sağlayacak bir <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="a7479-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="a7479-114">`file` bir derlemeyi içeremez.</span><span class="sxs-lookup"><span data-stu-id="a7479-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="a7479-115">Örneğin, çıktı dosyası oluşturulurken [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), meta verileri içeri aktarılabilir **- addmodule**.</span><span class="sxs-lookup"><span data-stu-id="a7479-115">For example, if the output file was created with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="a7479-116">Çıkış dosyası oluşturulurken bir **-hedef** dışında seçeneği **-target: module**, ile meta verilerini içeri aktarılamıyor **- addmodule** ancak ileiçeriaktarılabilir[-başvuru](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a7479-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="a7479-117">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor; bir proje bir modüle başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="a7479-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="a7479-118">Ayrıca, bu derleyici seçeneğini program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="a7479-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7479-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7479-119">Example</span></span>  
 <span data-ttu-id="a7479-120">Kaynak dosyasını derlemek `input.cs` ve meta verileri ekleme `metad1.netmodule` ve `metad2.netmodule` üretmek için `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="a7479-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7479-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7479-121">See also</span></span>

- [<span data-ttu-id="a7479-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a7479-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="a7479-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="a7479-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="a7479-124">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="a7479-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="a7479-125">Nasıl yapılır: Bir çoklu dosya derlemesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="a7479-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)

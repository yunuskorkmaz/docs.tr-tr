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
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970182"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="e56b7-102">-addmodule (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e56b7-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="e56b7-103">Bu seçenek, geçerli derlemeye hedef modülü anahtarı ile oluşturulmuş bir modül ekler.</span><span class="sxs-lookup"><span data-stu-id="e56b7-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e56b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e56b7-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e56b7-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e56b7-105">Arguments</span></span>  
 <span data-ttu-id="e56b7-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="e56b7-106">`file`, `file2`</span></span>  
 <span data-ttu-id="e56b7-107">Meta veri içeren bir çıktı dosyası.</span><span class="sxs-lookup"><span data-stu-id="e56b7-107">An output file that contains metadata.</span></span> <span data-ttu-id="e56b7-108">Dosya bir derleme bildirimi içeremez.</span><span class="sxs-lookup"><span data-stu-id="e56b7-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="e56b7-109">Birden fazla dosya almak için, virgül veya yarı iki nokta üst üste dosya adlarını ayırın.</span><span class="sxs-lookup"><span data-stu-id="e56b7-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e56b7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e56b7-110">Remarks</span></span>  
 <span data-ttu-id="e56b7-111">**-addmodule** ile eklenen tüm modüller, çalışma zamanında çıktı dosyasıyla aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e56b7-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="e56b7-112">Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e56b7-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="e56b7-113">Modül çalışma zamanında uygulama dizininde değilse, bir <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="e56b7-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="e56b7-114">`file`bir derleme içeremez.</span><span class="sxs-lookup"><span data-stu-id="e56b7-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="e56b7-115">Örneğin, çıktı dosyası [-target:module](./target-module-compiler-option.md)ile oluşturulmuşsa, meta verileri **-addmodule**ile içe aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="e56b7-115">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="e56b7-116">Çıktı dosyası **-target:module**dışında bir **-hedef** seçeneği ile oluşturulmuşsa, meta verileri **-addmodule** ile içe aktarılamaz, ancak [-referans](./reference-compiler-option.md)ile içe aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="e56b7-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="e56b7-117">Bu derleyici seçeneği Visual Studio'da kullanılamaz; bir proje bir modüle başvuru yapamaz.</span><span class="sxs-lookup"><span data-stu-id="e56b7-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="e56b7-118">Ayrıca, bu derleyici seçeneği programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e56b7-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e56b7-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="e56b7-119">Example</span></span>  
 <span data-ttu-id="e56b7-120">Kaynak dosyayı `input.cs` derle ve `metad1.netmodule` `metad2.netmodule` meta `out.exe`veri ekleyin ve üretmek için:</span><span class="sxs-lookup"><span data-stu-id="e56b7-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e56b7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e56b7-121">See also</span></span>

- [<span data-ttu-id="e56b7-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e56b7-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e56b7-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="e56b7-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="e56b7-124">Birden Çok Dosya Derlemeleri</span><span class="sxs-lookup"><span data-stu-id="e56b7-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="e56b7-125">Nasıl yapılır: Birden Fazla Dosya Derlemesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e56b7-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)

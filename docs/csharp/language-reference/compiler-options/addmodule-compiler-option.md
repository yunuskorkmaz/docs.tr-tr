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
ms.openlocfilehash: a5b0824774dabd4e0dd26dd1753eaba658299fbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215777"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="85454-102">-addmodule (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="85454-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="85454-103">Bu seçenek geçerli derlemeye target: module anahtarıyla oluşturulan bir modül ekler.</span><span class="sxs-lookup"><span data-stu-id="85454-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85454-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85454-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="85454-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="85454-105">Arguments</span></span>  
 <span data-ttu-id="85454-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="85454-106">`file`, `file2`</span></span>  
 <span data-ttu-id="85454-107">Meta veriler içeren bir çıktı dosyası.</span><span class="sxs-lookup"><span data-stu-id="85454-107">An output file that contains metadata.</span></span> <span data-ttu-id="85454-108">Dosya bir derleme bildirimi içeremez.</span><span class="sxs-lookup"><span data-stu-id="85454-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="85454-109">Birden fazla dosyayı içeri aktarmak için dosya adları virgül veya noktalı virgül ile ayırın.</span><span class="sxs-lookup"><span data-stu-id="85454-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85454-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85454-110">Remarks</span></span>  
 <span data-ttu-id="85454-111">İle eklenen tüm modüller **- addmodule** çalışma zamanında çıktı dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85454-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="85454-112">Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz ancak modülü çalışma zamanında uygulama dizininde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="85454-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="85454-113">Modül uygulama dizininde çalışma zamanında değil alırsa bir <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="85454-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="85454-114">`file` derleme içeremez.</span><span class="sxs-lookup"><span data-stu-id="85454-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="85454-115">Örneğin, çıktı dosyası oluşturulmuşsa [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), ile meta verilerini içe **- addmodule**.</span><span class="sxs-lookup"><span data-stu-id="85454-115">For example, if the output file was created with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="85454-116">Çıktı dosyası oluşturulmuşsa bir **-hedef** dışında seçeneği **-target: module**, ile meta verilerini içeri aktarılamıyor **- addmodule** ancak ileiçeriaktarılabilir[-başvuru](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="85454-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="85454-117">Visual Studio'da Bu derleyici seçeneği kullanılamıyor; bir proje bir modüle başvuru yapamaz.</span><span class="sxs-lookup"><span data-stu-id="85454-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="85454-118">Ayrıca, bu derleyici seçeneği programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="85454-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85454-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="85454-119">Example</span></span>  
 <span data-ttu-id="85454-120">Kaynak dosyasını derleme `input.cs` ve meta verileri ekleme `metad1.netmodule` ve `metad2.netmodule` üretmek için `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="85454-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="85454-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85454-121">See Also</span></span>  
 [<span data-ttu-id="85454-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="85454-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="85454-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="85454-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="85454-124">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="85454-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="85454-125">Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="85454-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)

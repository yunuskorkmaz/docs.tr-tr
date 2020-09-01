---
description: -addmodule (C# derleyici seçenekleri)
title: -addmodule (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: bcc615d52aec0a09ebf3913b3ece71f2cbfcbda9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126131"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="6af1d-103">-addmodule (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6af1d-103">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="6af1d-104">Bu seçenek, target: Module anahtarı geçerli derlemeye ile oluşturulmuş bir modül ekler.</span><span class="sxs-lookup"><span data-stu-id="6af1d-104">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af1d-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6af1d-105">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6af1d-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="6af1d-106">Arguments</span></span>  
 <span data-ttu-id="6af1d-107">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="6af1d-107">`file`, `file2`</span></span>  
 <span data-ttu-id="6af1d-108">Meta veri içeren bir çıkış dosyası.</span><span class="sxs-lookup"><span data-stu-id="6af1d-108">An output file that contains metadata.</span></span> <span data-ttu-id="6af1d-109">Dosya, bütünleştirilmiş kod bildirimi içeremez.</span><span class="sxs-lookup"><span data-stu-id="6af1d-109">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="6af1d-110">Birden fazla dosyayı içeri aktarmak için, dosya adlarını virgülle veya noktalı virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="6af1d-110">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6af1d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6af1d-111">Remarks</span></span>  
 <span data-ttu-id="6af1d-112">**-Addmodule** ile eklenen tüm modüller, çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6af1d-112">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="6af1d-113">Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6af1d-113">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="6af1d-114">Modül, çalışma zamanında uygulama dizininde değilse, bir alırsınız <xref:System.TypeLoadException> .</span><span class="sxs-lookup"><span data-stu-id="6af1d-114">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="6af1d-115">`file` bütünleştirilmiş kod içeremez.</span><span class="sxs-lookup"><span data-stu-id="6af1d-115">`file` cannot contain an assembly.</span></span> <span data-ttu-id="6af1d-116">Örneğin, çıkış dosyası [-target: Module](./target-module-compiler-option.md)ile oluşturulduysa, meta verileri **-addmodule**ile içeri aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="6af1d-116">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="6af1d-117">Çıkış dosyası **-target: Module**dışında bir **-target** seçeneği ile oluşturulduysa, meta verileri **-addmodule** ile içeri aktarılamaz ancak [-Reference](./reference-compiler-option.md)ile içeri aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="6af1d-117">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="6af1d-118">Bu derleyici seçeneği Visual Studio 'da kullanılamaz; bir proje bir modüle başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="6af1d-118">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="6af1d-119">Ayrıca, bu derleyici seçeneği program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="6af1d-119">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6af1d-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="6af1d-120">Example</span></span>  
 <span data-ttu-id="6af1d-121">Kaynak dosyasını derleyin `input.cs` , ve ' dan meta verileri ekleyin `metad1.netmodule` `metad2.netmodule` `out.exe` :</span><span class="sxs-lookup"><span data-stu-id="6af1d-121">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6af1d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6af1d-122">See also</span></span>

- [<span data-ttu-id="6af1d-123">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6af1d-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6af1d-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6af1d-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="6af1d-125">Çoklu dosya derlemeleri</span><span class="sxs-lookup"><span data-stu-id="6af1d-125">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="6af1d-126">Nasıl yapılır: çok dosyalı bütünleştirilmiş kod derleme</span><span class="sxs-lookup"><span data-stu-id="6af1d-126">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)

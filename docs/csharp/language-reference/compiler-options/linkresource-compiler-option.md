---
title: -linkresource (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: feca4713fe0e704799e2abbae3818edd0f3a5c84
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523181"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="a005c-102">-linkresource (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a005c-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="a005c-103">Çıkış dosyasında .NET Framework kaynağına bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a005c-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="a005c-104">Kaynak dosyası çıkış dosyasına eklenmez.</span><span class="sxs-lookup"><span data-stu-id="a005c-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="a005c-105">Bu farklıdır [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) kaynak dosyası çıkış dosyasına ekleme seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a005c-105">This differs from the [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a005c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a005c-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a005c-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="a005c-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="a005c-108">Derlemeden bağlamak istediğiniz .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="a005c-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="a005c-109">`identifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="a005c-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="a005c-110">Kaynağın mantıksal adı; Kaynak yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="a005c-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="a005c-111">Varsayılan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="a005c-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="a005c-112">`accessibility-modifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="a005c-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="a005c-113">Kaynak erişilebilirliğini: genel veya özel.</span><span class="sxs-lookup"><span data-stu-id="a005c-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="a005c-114">Genel varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a005c-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a005c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a005c-115">Remarks</span></span>  
 <span data-ttu-id="a005c-116">Varsayılan olarak, C# derleyicisi ile oluşturulduğunda bağlı kaynaklar derleme içinde geneldir.</span><span class="sxs-lookup"><span data-stu-id="a005c-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="a005c-117">Kaynakları özel hale getirmek için belirtin `private` erişilebilirlik değiştiricisi olarak.</span><span class="sxs-lookup"><span data-stu-id="a005c-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="a005c-118">Dışında bir değiştiriciye `public` veya `private` izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a005c-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="a005c-119">**-linkresource** birini gerektirir [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) dışında seçenekleri **-target: module**.</span><span class="sxs-lookup"><span data-stu-id="a005c-119">**-linkresource** requires one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="a005c-120">Varsa `filename` , örneğin, tarafından oluşturulmuş bir .NET Framework kaynak dosyası [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a005c-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="a005c-121">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a005c-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a005c-122">Diğer tüm kaynaklar için kullanmak `GetManifestResource` yöntemleri <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a005c-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="a005c-123">Belirtilen dosya `filename` herhangi bir biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="a005c-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="a005c-124">Örneğin, böylece genel derleme önbelleğine yüklenebilir ve derlemedeki yönetilen koddan erişilebilir bütünleştirilmiş kodun yerel bir DLL parçası haline getirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a005c-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="a005c-125">Aşağıdaki örnekler, ikinci bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a005c-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="a005c-126">Assembly Linker kullanarak aynı şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a005c-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="a005c-127">Aşağıdaki örnekler, üçüncü bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a005c-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="a005c-128">Daha fazla bilgi için [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) ve [derlemeler ve genel derleme önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="a005c-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="a005c-129">**-linkres** öğesinin kısa biçimidir **- linkresource**.</span><span class="sxs-lookup"><span data-stu-id="a005c-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="a005c-130">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="a005c-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a005c-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="a005c-131">Example</span></span>  
 <span data-ttu-id="a005c-132">Derleme `in.cs` ve kaynak dosyasının bağlantısını `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="a005c-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="a005c-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="a005c-133">Example</span></span>  
 <span data-ttu-id="a005c-134">Derleme `A.cs` bir DLL içine bağlantısını için yerel bir DLL N.dll ve Genel Derleme Önbelleği'ne (GAC) çıktı yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a005c-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="a005c-135">Bu örnekte, A.dll hem N.dll GAC içinde yer alacaktır.</span><span class="sxs-lookup"><span data-stu-id="a005c-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="a005c-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="a005c-136">Example</span></span>  
 <span data-ttu-id="a005c-137">Bu örnek Öncekine, ancak derleme bağlayıcı seçenekleri kullanarak aynı şeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="a005c-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="a005c-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a005c-138">See Also</span></span>  

- [<span data-ttu-id="a005c-139">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a005c-139">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="a005c-140">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="a005c-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)  
- [<span data-ttu-id="a005c-141">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="a005c-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
- [<span data-ttu-id="a005c-142">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="a005c-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

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
ms.openlocfilehash: 5c666b1c6440ac323830780ca5ca6930327ad9d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219186"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="bde91-102">-linkresource (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="bde91-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="bde91-103">.NET Framework kaynağına bağlantı çıktı dosyasında oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bde91-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="bde91-104">Kaynak dosyanın çıkış dosyasına eklenmez.</span><span class="sxs-lookup"><span data-stu-id="bde91-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="bde91-105">Bu farklıdır [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) kaynak dosyasını çıktı dosyasına katıştırma seçeneği.</span><span class="sxs-lookup"><span data-stu-id="bde91-105">This differs from the [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde91-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bde91-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="bde91-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="bde91-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="bde91-108">Derlemeden bağlamak istediğiniz .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="bde91-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="bde91-109">`identifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="bde91-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="bde91-110">Kaynak için mantıksal ad; Kaynak yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="bde91-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="bde91-111">Varsayılan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="bde91-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="bde91-112">`accessibility-modifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="bde91-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="bde91-113">Kaynak erişilebilirliğini: genel veya özel.</span><span class="sxs-lookup"><span data-stu-id="bde91-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="bde91-114">Ortak varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bde91-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bde91-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bde91-115">Remarks</span></span>  
 <span data-ttu-id="bde91-116">C# derleyici ile oluşturduğunuzda varsayılan olarak, bağlantılı derlemede ortak kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="bde91-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="bde91-117">Kaynakları özel hale getirmek için belirtmeniz `private` olarak erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="bde91-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="bde91-118">Herhangi bir değiştiricisi dışında `public` veya `private` izin verilir.</span><span class="sxs-lookup"><span data-stu-id="bde91-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="bde91-119">**-linkresource** birini gerektirir [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) dışında seçenekleri **-target: module**.</span><span class="sxs-lookup"><span data-stu-id="bde91-119">**-linkresource** requires one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="bde91-120">Varsa `filename` , örneğin, tarafından oluşturulan bir .NET Framework kaynak dosyası [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bde91-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="bde91-121">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bde91-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bde91-122">Diğer tüm kaynaklar için kullanmak `GetManifestResource` yöntemleri <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="bde91-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="bde91-123">Belirtilen dosya `filename` herhangi bir biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="bde91-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="bde91-124">Örneğin, böylece genel derleme önbelleğine yüklü ve yönetilen kod derlemesindeki erişilen derleme yerel bir DLL parçası haline getirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bde91-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="bde91-125">Aşağıdaki örnekler ikinci bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bde91-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="bde91-126">Derleme Bağlayıcı aynı şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bde91-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="bde91-127">Aşağıdaki örnekler üçüncü bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bde91-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="bde91-128">Daha fazla bilgi için bkz: [Al.exe (derleme bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md) ve [derlemeler ve genel derleme önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="bde91-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="bde91-129">**-linkres** kısa biçimi olan **- linkresource**.</span><span class="sxs-lookup"><span data-stu-id="bde91-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="bde91-130">Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="bde91-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bde91-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="bde91-131">Example</span></span>  
 <span data-ttu-id="bde91-132">Derleme `in.cs` ve kaynak dosyası bağlantısı `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="bde91-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="bde91-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="bde91-133">Example</span></span>  
 <span data-ttu-id="bde91-134">Derleme `A.cs` bir DLL içerisine bağlamak için yerel bir DLL N.dll ve çıktı Genel Derleme Önbelleği'ne (GAC) yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="bde91-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="bde91-135">Bu örnekte, hem A.dll hem de N.dll GAC'de yer alacaktır.</span><span class="sxs-lookup"><span data-stu-id="bde91-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="bde91-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="bde91-136">Example</span></span>  
 <span data-ttu-id="bde91-137">Bu örnek önceki bir, ancak derleme bağlayıcı seçeneklerini kullanarak aynı şeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="bde91-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="bde91-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bde91-138">See Also</span></span>  
 [<span data-ttu-id="bde91-139">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bde91-139">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="bde91-140">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="bde91-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)  
 [<span data-ttu-id="bde91-141">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="bde91-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="bde91-142">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="bde91-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

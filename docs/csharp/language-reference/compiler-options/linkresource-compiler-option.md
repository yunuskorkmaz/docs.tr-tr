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
ms.openlocfilehash: 41af8e0ba8ffebd07d3cb1d2bc5fbc04b8cd595d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173737"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="d8633-102">-linkresource (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d8633-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="d8633-103">Çıktı dosyasındaki bir .NET Framework kaynağına bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8633-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="d8633-104">Kaynak dosyası çıktı dosyasına eklenmez.</span><span class="sxs-lookup"><span data-stu-id="d8633-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="d8633-105">Bu, çıktı dosyasına bir kaynak dosyası gömmeyi yapan [-kaynak](./resource-compiler-option.md) seçeneğinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d8633-105">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8633-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8633-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d8633-107">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d8633-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d8633-108">Derlemeden bağlamak istediğiniz .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="d8633-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="d8633-109">`identifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="d8633-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="d8633-110">Kaynak için mantıksal ad; kaynağı yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="d8633-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="d8633-111">Varsayılan, dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="d8633-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="d8633-112">`accessibility-modifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="d8633-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="d8633-113">Kaynağın erişilebilirliği: ortak veya özel.</span><span class="sxs-lookup"><span data-stu-id="d8633-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="d8633-114">Varsayılan değer herkese açıktır.</span><span class="sxs-lookup"><span data-stu-id="d8633-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8633-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8633-115">Remarks</span></span>  
 <span data-ttu-id="d8633-116">Varsayılan olarak, bağlı kaynaklar C# derleyicisi ile oluşturulduğunda derlemede herkese açıktır.</span><span class="sxs-lookup"><span data-stu-id="d8633-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="d8633-117">Kaynakları özel yapmak için `private` erişilebilirlik değiştirici olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="d8633-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="d8633-118">Başka bir değiştirici `public` dışında `private` veya izin verilir.</span><span class="sxs-lookup"><span data-stu-id="d8633-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="d8633-119">**-linkresource** **-target:module**dışındaki [-hedef](./target-compiler-option.md) seçeneklerinden birini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d8633-119">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="d8633-120">Örneğin `filename` [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulan bir .NET Framework kaynak dosyasıysa, <xref:System.Resources> ad alanındaki üyelerle erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d8633-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="d8633-121">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d8633-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d8633-122">Diğer tüm kaynaklar için, çalışma <xref:System.Reflection.Assembly> zamanında kaynağa erişmek için sınıftaki `GetManifestResource` yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8633-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="d8633-123">Belirtilen dosya `filename` herhangi bir biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8633-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="d8633-124">Örneğin, genel derleme önbelleğine yüklenmesi ve derlemedeki yönetilen koddan erişilebilmesini sağlamak için derlemenin yerel bir DLL parçası olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8633-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="d8633-125">Aşağıdaki örneklerden ikincisi bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8633-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="d8633-126">Aynı şeyi Derleme Linker'da da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8633-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="d8633-127">Aşağıdaki örneklerin üçüncüsü bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8633-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="d8633-128">Daha fazla bilgi için [Al.exe (Derleme Bağlantı Cısı)](../../../framework/tools/al-exe-assembly-linker.md) ve [Derlemeler ve Küresel Montaj Önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="d8633-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="d8633-129">**-linkres** **-linkresource**kısa şeklidir.</span><span class="sxs-lookup"><span data-stu-id="d8633-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="d8633-130">Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="d8633-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8633-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8633-131">Example</span></span>  
 <span data-ttu-id="d8633-132">Kaynak `in.cs` dosyasını `rf.resource`derleme ve bağlantı:</span><span class="sxs-lookup"><span data-stu-id="d8633-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="d8633-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8633-133">Example</span></span>  
 <span data-ttu-id="d8633-134">Bir `A.cs` DLL'ye kopyala, yerel bir DLL N.dll'ye bağlantı ve çıktıyı Global Assembly Önbelleğine (GAC) koyun.</span><span class="sxs-lookup"><span data-stu-id="d8633-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="d8633-135">Bu örnekte, hem A.dll hem de N.dll GAC'de ikamet edecektir.</span><span class="sxs-lookup"><span data-stu-id="d8633-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="d8633-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8633-136">Example</span></span>  
 <span data-ttu-id="d8633-137">Bu örnek, öncekiyle aynı şeyi yapar, ancak Derleme Bağlayıcı sı seçeneklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d8633-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8633-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8633-138">See also</span></span>

- [<span data-ttu-id="d8633-139">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d8633-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d8633-140">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="d8633-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="d8633-141">Derlemeler ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="d8633-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="d8633-142">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="d8633-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

---
description: -linkresource (C# derleyici seçenekleri)
title: -linkresource (C# derleyici seçenekleri)
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
ms.openlocfilehash: cd1150f3fa0dd0eca4e9352ce3809e73a15126c7
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466111"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="585d8-103">-linkresource (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="585d8-103">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="585d8-104">Çıkış dosyasında .NET kaynağına bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="585d8-104">Creates a link to a .NET resource in the output file.</span></span> <span data-ttu-id="585d8-105">Kaynak dosyası çıkış dosyasına eklenmez.</span><span class="sxs-lookup"><span data-stu-id="585d8-105">The resource file is not added to the output file.</span></span> <span data-ttu-id="585d8-106">Bu, çıkış dosyasına bir kaynak dosyası katıştırabilen [-Resource](./resource-compiler-option.md) seçeneğinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="585d8-106">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="585d8-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="585d8-107">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="585d8-108">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="585d8-108">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="585d8-109">Derlemeden bağlamak istediğiniz .NET kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="585d8-109">The .NET resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="585d8-110">`identifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="585d8-110">`identifier` (optional)</span></span>  
 <span data-ttu-id="585d8-111">Kaynağın mantıksal adı; kaynağı yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="585d8-111">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="585d8-112">Varsayılan değer, dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="585d8-112">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="585d8-113">`accessibility-modifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="585d8-113">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="585d8-114">Kaynağın erişilebilirliği: public veya Private.</span><span class="sxs-lookup"><span data-stu-id="585d8-114">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="585d8-115">Varsayılan değer geneldir.</span><span class="sxs-lookup"><span data-stu-id="585d8-115">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="585d8-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="585d8-116">Remarks</span></span>  
 <span data-ttu-id="585d8-117">Varsayılan olarak, bağlı kaynaklar C# derleyicisi ile oluşturulduklarında derlemede ortaktır.</span><span class="sxs-lookup"><span data-stu-id="585d8-117">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="585d8-118">Kaynakları özel hale getirmek için `private` erişilebilirlik değiştiricisi olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="585d8-118">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="585d8-119">Veya dışında başka bir değiştirici `public` `private` kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="585d8-119">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="585d8-120">**-linkresource** ,- **target: Module**dışındaki [-target](./target-compiler-option.md) seçeneklerinden birini gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="585d8-120">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="585d8-121">`filename`Örneğin, [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .net kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="585d8-121">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="585d8-122">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="585d8-122">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="585d8-123">Diğer tüm kaynaklar için, `GetManifestResource` <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek üzere sınıfındaki yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="585d8-123">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="585d8-124">İçinde belirtilen dosya `filename` herhangi bir biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="585d8-124">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="585d8-125">Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="585d8-125">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="585d8-126">Aşağıdaki örneklerden İkincisi bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="585d8-126">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="585d8-127">Derleme bağlayıcıda aynı şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="585d8-127">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="585d8-128">Aşağıdaki örneklerden üçüncüsü bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="585d8-128">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="585d8-129">Daha fazla bilgi için bkz. [Al.exe (bütünleştirilmiş kod bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md) ve [derlemeler ve genel derleme önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="585d8-129">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="585d8-130">**-linkres** , **-linkresource**öğesinin kısa biçimidir.</span><span class="sxs-lookup"><span data-stu-id="585d8-130">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="585d8-131">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="585d8-131">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="585d8-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="585d8-132">Example</span></span>  
 <span data-ttu-id="585d8-133">Derle `in.cs` ve kaynak dosyasına bağla `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="585d8-133">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="585d8-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="585d8-134">Example</span></span>  
 <span data-ttu-id="585d8-135">`A.cs`DLL 'de derleyin, yerel BIR dll N.dll bağlayın ve çıktıyı genel derleme önbelleği 'ne (GAC) yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="585d8-135">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="585d8-136">Bu örnekte, A.dll ve N.dll her ikisi de GAC 'de yer alır.</span><span class="sxs-lookup"><span data-stu-id="585d8-136">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="585d8-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="585d8-137">Example</span></span>  
 <span data-ttu-id="585d8-138">Bu örnek, bir önceki ile aynı şeyi, ancak derleme bağlayıcı seçeneklerini kullanarak yapar.</span><span class="sxs-lookup"><span data-stu-id="585d8-138">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="585d8-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="585d8-139">See also</span></span>

- [<span data-ttu-id="585d8-140">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="585d8-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="585d8-141">Al.exe (bütünleştirilmiş kod bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="585d8-141">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="585d8-142">Derlemeler ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="585d8-142">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="585d8-143">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="585d8-143">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

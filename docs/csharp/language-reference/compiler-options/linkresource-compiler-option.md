---
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
ms.openlocfilehash: 454915454f3faf15933257f3e3e221afec51d0ee
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606760"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="2f0d3-102">-linkresource (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2f0d3-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="2f0d3-103">Çıkış dosyasındaki bir .NET Framework kaynağına bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="2f0d3-104">Kaynak dosyası çıkış dosyasına eklenmez.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="2f0d3-105">Bu, çıkış dosyasına bir kaynak dosyası katıştırabilen [-Resource](./resource-compiler-option.md) seçeneğinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-105">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f0d3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f0d3-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f0d3-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="2f0d3-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="2f0d3-108">Derlemeden bağlamak istediğiniz .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="2f0d3-109">`identifier`seçim</span><span class="sxs-lookup"><span data-stu-id="2f0d3-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="2f0d3-110">Kaynağın mantıksal adı; kaynağı yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="2f0d3-111">Varsayılan değer, dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="2f0d3-112">`accessibility-modifier`seçim</span><span class="sxs-lookup"><span data-stu-id="2f0d3-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="2f0d3-113">Kaynağın erişilebilirliği: public veya Private.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="2f0d3-114">Varsayılan değer geneldir.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f0d3-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f0d3-115">Remarks</span></span>  
 <span data-ttu-id="2f0d3-116">Varsayılan olarak, bağlantılı kaynaklar C# derleyici ile oluşturulduklarında derlemede ortaktır.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="2f0d3-117">Kaynakları özel hale getirmek için erişilebilirlik değiştiricisi `private` olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="2f0d3-118">`public` Veya`private` dışında başka bir değiştirici kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="2f0d3-119">**-linkresource** ,- **target: Module**dışındaki [-target](./target-compiler-option.md) seçeneklerinden birini gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-119">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="2f0d3-120">, Örneğin [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. `filename`</span><span class="sxs-lookup"><span data-stu-id="2f0d3-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="2f0d3-121">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2f0d3-122">Diğer tüm kaynaklar için, çalışma zamanında `GetManifestResource` kaynağa erişmek üzere <xref:System.Reflection.Assembly> sınıfındaki yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="2f0d3-123">İçinde `filename` belirtilen dosya herhangi bir biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="2f0d3-124">Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="2f0d3-125">Aşağıdaki örneklerden İkincisi bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="2f0d3-126">Derleme bağlayıcıda aynı şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="2f0d3-127">Aşağıdaki örneklerden üçüncüsü bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="2f0d3-128">Daha fazla bilgi için bkz. [al. exe (bütünleştirilmiş kod bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md) ve [derlemeler ve genel derleme önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="2f0d3-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="2f0d3-129">**-linkres** , **-linkresource**öğesinin kısa biçimidir.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="2f0d3-130">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f0d3-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f0d3-131">Example</span></span>  
 <span data-ttu-id="2f0d3-132">Derle `in.cs` ve kaynak dosyasına `rf.resource`bağla:</span><span class="sxs-lookup"><span data-stu-id="2f0d3-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="2f0d3-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f0d3-133">Example</span></span>  
 <span data-ttu-id="2f0d3-134">Bir `A.cs` dll 'de derleyin, yerel dll N. dll ' ye bağlanın ve çıktıyı genel derleme önbelleği 'ne (GAC) yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="2f0d3-135">Bu örnekte, hem. dll hem de N. dll GAC 'de yer alır.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="2f0d3-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f0d3-136">Example</span></span>  
 <span data-ttu-id="2f0d3-137">Bu örnek, bir önceki ile aynı şeyi, ancak derleme bağlayıcı seçeneklerini kullanarak yapar.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f0d3-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f0d3-138">See also</span></span>

- [<span data-ttu-id="2f0d3-139">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2f0d3-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2f0d3-140">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="2f0d3-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="2f0d3-141">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="2f0d3-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="2f0d3-142">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="2f0d3-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

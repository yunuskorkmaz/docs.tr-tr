---
description: -Resource (C# derleyici seçenekleri)
title: -Resource (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: 1e2de095b460b684fb06faf46731283a1304906e
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465695"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="595b9-103">-Resource (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="595b9-103">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="595b9-104">Belirtilen kaynağı çıkış dosyasına katıştırır.</span><span class="sxs-lookup"><span data-stu-id="595b9-104">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="595b9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="595b9-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="595b9-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="595b9-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="595b9-107">Çıktı dosyasına eklemek istediğiniz .NET kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="595b9-107">The .NET resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="595b9-108">`identifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="595b9-108">`identifier` (optional)</span></span>  
 <span data-ttu-id="595b9-109">Kaynağın mantıksal adı; kaynağı yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="595b9-109">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="595b9-110">Varsayılan değer, dosya adının adıdır.</span><span class="sxs-lookup"><span data-stu-id="595b9-110">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="595b9-111">`accessibility-modifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="595b9-111">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="595b9-112">Kaynağın erişilebilirliği: public veya Private.</span><span class="sxs-lookup"><span data-stu-id="595b9-112">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="595b9-113">Varsayılan değer geneldir.</span><span class="sxs-lookup"><span data-stu-id="595b9-113">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="595b9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="595b9-114">Remarks</span></span>  
 <span data-ttu-id="595b9-115">Kaynağı bir derlemeye bağlamak ve kaynak dosyasını çıkış dosyasına eklemek için [-linkresource](./linkresource-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="595b9-115">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="595b9-116">Varsayılan olarak, kaynaklar C# derleyicisi kullanılarak oluşturulduğunda derlemede ortaktır.</span><span class="sxs-lookup"><span data-stu-id="595b9-116">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="595b9-117">Kaynakları özel hale getirmek için `private` erişilebilirlik değiştiricisi olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="595b9-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="595b9-118">Veya dışında başka bir erişilebilirliği `public` olamaz `private` .</span><span class="sxs-lookup"><span data-stu-id="595b9-118">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="595b9-119">`filename`Örneğin, [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .net kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="595b9-119">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="595b9-120">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="595b9-120">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="595b9-121">Diğer tüm kaynaklar için, `GetManifestResource` <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek üzere sınıfındaki yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="595b9-121">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="595b9-122">**-res** , **-Resource**' in kısa biçimidir.</span><span class="sxs-lookup"><span data-stu-id="595b9-122">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="595b9-123">Çıkış dosyasındaki kaynakların sırası, komut satırında belirtilen sırada belirlenir.</span><span class="sxs-lookup"><span data-stu-id="595b9-123">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="595b9-124">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="595b9-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="595b9-125">Projenize bir kaynak dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="595b9-125">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="595b9-126">**Çözüm Gezgini**eklemek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="595b9-126">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="595b9-127">**Özellikler** penceresinde dosya Için **derleme eylemi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="595b9-127">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="595b9-128">**Derleme eylemini** **gömülü kaynağa**ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="595b9-128">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="595b9-129">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.FileProperties2.BuildAction%2A> ..</span><span class="sxs-lookup"><span data-stu-id="595b9-129">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="595b9-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="595b9-130">Example</span></span>  
 <span data-ttu-id="595b9-131">Derleme `in.cs` ve kaynak dosyası iliştirme `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="595b9-131">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="595b9-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="595b9-132">See also</span></span>

- [<span data-ttu-id="595b9-133">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="595b9-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="595b9-134">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="595b9-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

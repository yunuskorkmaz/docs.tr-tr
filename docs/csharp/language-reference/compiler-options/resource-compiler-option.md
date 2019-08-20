---
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
ms.openlocfilehash: e14bf59f5922a918b627af22c052c8efd9081e84
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602531"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="c8f92-102">-Resource (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c8f92-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="c8f92-103">Belirtilen kaynağı çıkış dosyasına katıştırır.</span><span class="sxs-lookup"><span data-stu-id="c8f92-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8f92-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c8f92-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c8f92-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="c8f92-106">Çıkış dosyasına eklemek istediğiniz .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="c8f92-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="c8f92-107">`identifier`seçim</span><span class="sxs-lookup"><span data-stu-id="c8f92-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="c8f92-108">Kaynağın mantıksal adı; kaynağı yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="c8f92-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="c8f92-109">Varsayılan değer, dosya adının adıdır.</span><span class="sxs-lookup"><span data-stu-id="c8f92-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="c8f92-110">`accessibility-modifier`seçim</span><span class="sxs-lookup"><span data-stu-id="c8f92-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="c8f92-111">Kaynağın erişilebilirliği: public veya Private.</span><span class="sxs-lookup"><span data-stu-id="c8f92-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="c8f92-112">Varsayılan değer geneldir.</span><span class="sxs-lookup"><span data-stu-id="c8f92-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8f92-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8f92-113">Remarks</span></span>  
 <span data-ttu-id="c8f92-114">Kaynağı bir derlemeye bağlamak ve kaynak dosyasını çıkış dosyasına eklemek için [-linkresource](./linkresource-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8f92-114">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="c8f92-115">Varsayılan olarak, kaynaklar C# derleyici kullanılarak oluşturulduğunda derlemede ortaktır.</span><span class="sxs-lookup"><span data-stu-id="c8f92-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="c8f92-116">Kaynakları özel hale getirmek için erişilebilirlik değiştiricisi `private` olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="c8f92-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="c8f92-117">`public` Veya`private` dışında başka bir erişilebilirliği olamaz.</span><span class="sxs-lookup"><span data-stu-id="c8f92-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="c8f92-118">, Örneğin [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. `filename`</span><span class="sxs-lookup"><span data-stu-id="c8f92-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="c8f92-119">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8f92-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c8f92-120">Diğer tüm kaynaklar için, çalışma zamanında `GetManifestResource` kaynağa erişmek üzere <xref:System.Reflection.Assembly> sınıfındaki yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8f92-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="c8f92-121">**-res** , **-Resource**' in kısa biçimidir.</span><span class="sxs-lookup"><span data-stu-id="c8f92-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="c8f92-122">Çıkış dosyasındaki kaynakların sırası, komut satırında belirtilen sırada belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c8f92-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c8f92-123">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c8f92-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c8f92-124">Projenize bir kaynak dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c8f92-124">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="c8f92-125">**Çözüm Gezgini**eklemek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="c8f92-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="c8f92-126">**Özellikler** penceresinde dosya Için **derleme eylemi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="c8f92-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="c8f92-127">**Derleme eylemini** **gömülü kaynağa**ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c8f92-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="c8f92-128">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8f92-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8f92-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8f92-129">Example</span></span>  
 <span data-ttu-id="c8f92-130">Derleme `in.cs` ve kaynak dosyası `rf.resource`iliştirme:</span><span class="sxs-lookup"><span data-stu-id="c8f92-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8f92-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8f92-131">See also</span></span>

- [<span data-ttu-id="c8f92-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c8f92-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c8f92-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="c8f92-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

---
title: -Kaynak (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 056207185f89aa219faf1b721598d372394e1061
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725707"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="6e1af-102">-Kaynak (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6e1af-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="6e1af-103">Belirtilen kaynak çıkış dosyasına katıştırır.</span><span class="sxs-lookup"><span data-stu-id="6e1af-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e1af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e1af-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6e1af-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6e1af-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="6e1af-106">Çıkış dosyasına eklemek istediğiniz .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="6e1af-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="6e1af-107">`identifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="6e1af-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="6e1af-108">Kaynağın mantıksal adı; Kaynak yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="6e1af-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="6e1af-109">Dosya adı varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6e1af-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="6e1af-110">`accessibility-modifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="6e1af-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="6e1af-111">Kaynak erişilebilirliğini: genel veya özel.</span><span class="sxs-lookup"><span data-stu-id="6e1af-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="6e1af-112">Genel varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6e1af-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e1af-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e1af-113">Remarks</span></span>  
 <span data-ttu-id="6e1af-114">Kullanım [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) kaynağı için bir derleme bağlama ve kaynak dosyası çıkış dosyasına ekleme.</span><span class="sxs-lookup"><span data-stu-id="6e1af-114">Use [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="6e1af-115">Varsayılan olarak, C# derleyicisi kullanılarak oluşturulduğunda kaynaklar derleme içinde geneldir.</span><span class="sxs-lookup"><span data-stu-id="6e1af-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="6e1af-116">Kaynakları özel hale getirmek için belirtin `private` erişilebilirlik değiştiricisi olarak.</span><span class="sxs-lookup"><span data-stu-id="6e1af-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="6e1af-117">Dışındaki bir erişilebilirliğe `public` veya `private` izin verilir.</span><span class="sxs-lookup"><span data-stu-id="6e1af-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="6e1af-118">Varsa `filename` , örneğin, tarafından oluşturulmuş bir .NET Framework kaynak dosyası [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6e1af-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="6e1af-119">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e1af-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6e1af-120">Diğer tüm kaynaklar için kullanmak `GetManifestResource` yöntemleri <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="6e1af-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="6e1af-121">**-res** öğesinin kısa biçimidir **-kaynak**.</span><span class="sxs-lookup"><span data-stu-id="6e1af-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="6e1af-122">Çıkış dosyası kaynakları sırası, komut satırında belirtilen siparişi belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6e1af-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6e1af-123">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6e1af-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="6e1af-124">Bir kaynak dosyası projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e1af-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="6e1af-125">Eklemek istediğiniz dosyayı seçin **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="6e1af-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="6e1af-126">Seçin **derleme eylemi** dosya **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="6e1af-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="6e1af-127">Ayarlama **derleme eylemi** için **katıştırılmış kaynak**.</span><span class="sxs-lookup"><span data-stu-id="6e1af-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="6e1af-128">Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e1af-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e1af-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e1af-129">Example</span></span>  
 <span data-ttu-id="6e1af-130">Derleme `in.cs` ve kaynak dosya ekleme `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="6e1af-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e1af-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e1af-131">See also</span></span>

- [<span data-ttu-id="6e1af-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6e1af-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="6e1af-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6e1af-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

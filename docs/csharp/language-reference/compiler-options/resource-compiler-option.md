---
title: "-resource (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c20de499ae0fd5f8869c9b6e78a308fde9787ef9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="24dcd-102">-resource (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="24dcd-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="24dcd-103">Belirtilen kaynak çıkış dosyası içine katıştırır.</span><span class="sxs-lookup"><span data-stu-id="24dcd-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24dcd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24dcd-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="24dcd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="24dcd-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="24dcd-106">Çıktı dosyasına eklemek istediğiniz .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="24dcd-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="24dcd-107">`identifier`(isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="24dcd-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="24dcd-108">Kaynak için mantıksal ad; Kaynak yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="24dcd-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="24dcd-109">Varsayılan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="24dcd-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="24dcd-110">`accessibility-modifier`(isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="24dcd-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="24dcd-111">Kaynak erişilebilirliğini: genel veya özel.</span><span class="sxs-lookup"><span data-stu-id="24dcd-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="24dcd-112">Ortak varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="24dcd-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24dcd-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24dcd-113">Remarks</span></span>  
 <span data-ttu-id="24dcd-114">Kullanım [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) bir derlemeye bir kaynak bağlayın ve kaynak dosyası çıktı dosyasına ekleme.</span><span class="sxs-lookup"><span data-stu-id="24dcd-114">Use [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="24dcd-115">C# Derleyici kullanılarak oluşturulduğunda varsayılan olarak, derlemede ortak kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="24dcd-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="24dcd-116">Kaynakları özel hale getirmek için belirtmeniz `private` olarak erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="24dcd-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="24dcd-117">Dışındaki bir erişilebilirliğe `public` veya `private` izin verilir.</span><span class="sxs-lookup"><span data-stu-id="24dcd-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="24dcd-118">Varsa `filename` , örneğin, tarafından oluşturulan bir .NET Framework kaynak dosyası [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="24dcd-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="24dcd-119">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="24dcd-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="24dcd-120">Diğer tüm kaynaklar için kullanmak `GetManifestResource` yöntemleri <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="24dcd-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="24dcd-121">**-res** kısa biçimi olan **-kaynak**.</span><span class="sxs-lookup"><span data-stu-id="24dcd-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="24dcd-122">Çıktı dosyası kaynaklarında sırasını, komut satırında belirtilen sipariş belirlenir.</span><span class="sxs-lookup"><span data-stu-id="24dcd-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="24dcd-123">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="24dcd-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="24dcd-124">Kaynak dosyayı projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24dcd-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="24dcd-125">İçinde eklemek istediğiniz dosyayı seçin **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="24dcd-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="24dcd-126">Seçin **yapı eylemi** dosyasını **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="24dcd-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="24dcd-127">Ayarlama **yapı eylemi** için **katıştırılmış kaynak**.</span><span class="sxs-lookup"><span data-stu-id="24dcd-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="24dcd-128">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="24dcd-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24dcd-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="24dcd-129">Example</span></span>  
 <span data-ttu-id="24dcd-130">Derleme `in.cs` ve kaynak dosyası ekleme `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="24dcd-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="24dcd-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24dcd-131">See Also</span></span>  
 [<span data-ttu-id="24dcd-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="24dcd-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="24dcd-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="24dcd-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

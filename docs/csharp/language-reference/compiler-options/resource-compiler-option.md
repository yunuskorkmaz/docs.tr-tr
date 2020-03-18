---
title: -kaynak (C# Derleyici Seçenekleri)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602531"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="5b4e6-102">-kaynak (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5b4e6-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="5b4e6-103">Belirtilen kaynağı çıktı dosyasına gömer.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b4e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b4e6-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5b4e6-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="5b4e6-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="5b4e6-106">Çıktı dosyasına katıştırmak istediğiniz .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="5b4e6-107">`identifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="5b4e6-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="5b4e6-108">Kaynak için mantıksal ad; kaynağı yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="5b4e6-109">Varsayılan, dosya adının adıdır.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="5b4e6-110">`accessibility-modifier` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="5b4e6-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="5b4e6-111">Kaynağın erişilebilirliği: ortak veya özel.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="5b4e6-112">Varsayılan değer herkese açıktır.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b4e6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b4e6-113">Remarks</span></span>  
 <span data-ttu-id="5b4e6-114">Kaynağı derlemeye bağlamak ve kaynak dosyasını çıktı dosyasına eklememek için [-linkresource'ı](./linkresource-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-114">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="5b4e6-115">Varsayılan olarak, c# derleyicisi kullanılarak oluşturulan kaynaklar derlemede geneldir.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="5b4e6-116">Kaynakları özel yapmak için `private` erişilebilirlik değiştirici olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="5b4e6-117">İzin verilen `public` veya `private` izin verilen başka bir erişilebilirlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="5b4e6-118">Örneğin `filename` [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulan bir .NET Framework kaynak dosyasıysa, <xref:System.Resources> ad alanındaki üyelerle erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="5b4e6-119">Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5b4e6-120">Diğer tüm kaynaklar için, çalışma <xref:System.Reflection.Assembly> zamanında kaynağa erişmek için sınıftaki `GetManifestResource` yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="5b4e6-121">**-res** **-kaynak**kısa şeklidir.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="5b4e6-122">Çıktı dosyasındaki kaynakların sırası komut satırında belirtilen sırada belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5b4e6-123">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5b4e6-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5b4e6-124">Projenize bir kaynak dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-124">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="5b4e6-125">**Çözüm Gezgini'ne**katıştırmak istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="5b4e6-126">**Özellikler** penceresindedosya için **Eylem Oluştur'u** seçin.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="5b4e6-127">**Yapı Eylemini** **Katıştırılmış Kaynağa**ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="5b4e6-128">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.FileProperties2.BuildAction%2A></span><span class="sxs-lookup"><span data-stu-id="5b4e6-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b4e6-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b4e6-129">Example</span></span>  
 <span data-ttu-id="5b4e6-130">Kaynak `in.cs` dosyayı `rf.resource`derleme ve ekleme:</span><span class="sxs-lookup"><span data-stu-id="5b4e6-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b4e6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b4e6-131">See also</span></span>

- [<span data-ttu-id="5b4e6-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5b4e6-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5b4e6-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="5b4e6-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

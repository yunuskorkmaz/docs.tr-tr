---
title: -Kaynak (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77c80332e663596244b35fe002218e7bcbaeb46a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523330"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="80dd9-102">-Kaynak (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80dd9-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="80dd9-103">Yönetilen kaynak bir derlemeye gömer.</span><span class="sxs-lookup"><span data-stu-id="80dd9-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80dd9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80dd9-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="80dd9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="80dd9-105">Arguments</span></span>  
  
|<span data-ttu-id="80dd9-106">Terim</span><span class="sxs-lookup"><span data-stu-id="80dd9-106">Term</span></span>|<span data-ttu-id="80dd9-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="80dd9-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="80dd9-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="80dd9-108">Required.</span></span> <span data-ttu-id="80dd9-109">Çıkış dosyasına eklemek için kaynak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="80dd9-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="80dd9-110">Varsayılan olarak, `filename` derleme içinde geneldir.</span><span class="sxs-lookup"><span data-stu-id="80dd9-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="80dd9-111">Dosya adı tırnak içine alın ("") bir boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="80dd9-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="80dd9-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="80dd9-112">Optional.</span></span> <span data-ttu-id="80dd9-113">Kaynağın mantıksal adı; yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="80dd9-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="80dd9-114">Varsayılan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="80dd9-114">The default is the name of the file.</span></span> <span data-ttu-id="80dd9-115">İsteğe bağlı olarak, kaynak olarak aşağıdaki genel veya özel derleme bildiriminde olup olmadığını belirtebilirsiniz: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="80dd9-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80dd9-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80dd9-116">Remarks</span></span>  
 <span data-ttu-id="80dd9-117">Kullanım `-linkresource` kaynak dosyası çıkış dosyasına koymadan bir kaynak bir derlemeye bağlanır.</span><span class="sxs-lookup"><span data-stu-id="80dd9-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="80dd9-118">Varsa `filename` olduğu bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , örneğin, göre oluşturulmuş kaynak dosyası [Resgen.exe (kaynak dosya oluşturucu)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> (bkz: adalanı<xref:System.Resources.ResourceManager> daha fazla bilgi için).</span><span class="sxs-lookup"><span data-stu-id="80dd9-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="80dd9-119">Çalışma zamanında diğer kaynaklara erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="80dd9-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="80dd9-120">Kısa formunu da `-resource` olduğu `-res`.</span><span class="sxs-lookup"><span data-stu-id="80dd9-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="80dd9-121">Nasıl ayarlanacağı hakkında daha fazla bilgi için `-resource` Visual Studio IDE'de bkz [uygulama kaynaklarını yönetme (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="80dd9-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80dd9-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="80dd9-122">Example</span></span>  
 <span data-ttu-id="80dd9-123">Aşağıdaki kod derlenir `In.vb` ve kaynak dosyası ekler `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="80dd9-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="80dd9-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80dd9-124">See Also</span></span>  
 [<span data-ttu-id="80dd9-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="80dd9-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="80dd9-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="80dd9-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [<span data-ttu-id="80dd9-127">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80dd9-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [<span data-ttu-id="80dd9-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80dd9-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="80dd9-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="80dd9-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

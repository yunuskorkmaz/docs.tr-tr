---
title: -resource (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
ms.openlocfilehash: 0de09ec0c778ac55ac7d93aa6d344e2067c46116
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="7253e-102">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7253e-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="7253e-103">Yönetilen bir kaynağın bir derlemede katıştırır.</span><span class="sxs-lookup"><span data-stu-id="7253e-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7253e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7253e-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7253e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7253e-105">Arguments</span></span>  
  
|<span data-ttu-id="7253e-106">Terim</span><span class="sxs-lookup"><span data-stu-id="7253e-106">Term</span></span>|<span data-ttu-id="7253e-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="7253e-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="7253e-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7253e-108">Required.</span></span> <span data-ttu-id="7253e-109">Çıktı dosyasına katıştırmak için kaynak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="7253e-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="7253e-110">Varsayılan olarak, `filename` bütünleştirilmiş kodunda geneldir.</span><span class="sxs-lookup"><span data-stu-id="7253e-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="7253e-111">Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="7253e-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="7253e-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7253e-112">Optional.</span></span> <span data-ttu-id="7253e-113">Kaynak için mantıksal ad; yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="7253e-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="7253e-114">Varsayılan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="7253e-114">The default is the name of the file.</span></span> <span data-ttu-id="7253e-115">İsteğe bağlı olarak, kaynağın aşağıdaki gibi ortak veya özel derleme bildiriminde olup olmadığını belirtebilirsiniz: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="7253e-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7253e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7253e-116">Remarks</span></span>  
 <span data-ttu-id="7253e-117">Kullanım `-linkresource` kaynak dosyasını çıktı dosyasına yerleştirerek olmadan bir kaynağı bir derlemeye bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="7253e-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="7253e-118">Varsa `filename` olan bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , örneğin, tarafından oluşturulan kaynak dosyasını [Resgen.exe (kaynak dosya oluşturucu)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı (bkz: <xref:System.Resources.ResourceManager> daha fazla bilgi için).</span><span class="sxs-lookup"><span data-stu-id="7253e-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="7253e-119">Çalışma zamanında tüm diğer kaynaklarına erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="7253e-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="7253e-120">Kısa formunu `-resource` olan `-res`.</span><span class="sxs-lookup"><span data-stu-id="7253e-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="7253e-121">Nasıl ayarlanacağı hakkında bilgi için `-resource` Visual Studio IDE'de bkz [yönetme uygulama kaynakları (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7253e-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7253e-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="7253e-122">Example</span></span>  
 <span data-ttu-id="7253e-123">Aşağıdaki kod derlerken `In.vb` ve ekler kaynak dosyası `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="7253e-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7253e-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7253e-124">See Also</span></span>  
 [<span data-ttu-id="7253e-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7253e-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7253e-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="7253e-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [<span data-ttu-id="7253e-127">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7253e-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [<span data-ttu-id="7253e-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7253e-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="7253e-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="7253e-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

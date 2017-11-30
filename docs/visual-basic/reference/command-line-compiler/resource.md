---
title: /resource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 858a216873ad9999722388e45d5de28398b27fbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="resource-visual-basic"></a><span data-ttu-id="a9fae-102">/resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9fae-102">/resource (Visual Basic)</span></span>
<span data-ttu-id="a9fae-103">Yönetilen bir kaynağın bir derlemede katıştırır.</span><span class="sxs-lookup"><span data-stu-id="a9fae-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9fae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9fae-104">Syntax</span></span>  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a9fae-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a9fae-105">Arguments</span></span>  
  
|<span data-ttu-id="a9fae-106">Terim</span><span class="sxs-lookup"><span data-stu-id="a9fae-106">Term</span></span>|<span data-ttu-id="a9fae-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="a9fae-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="a9fae-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a9fae-108">Required.</span></span> <span data-ttu-id="a9fae-109">Çıktı dosyasına katıştırmak için kaynak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a9fae-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="a9fae-110">Varsayılan olarak, `filename` bütünleştirilmiş kodunda geneldir.</span><span class="sxs-lookup"><span data-stu-id="a9fae-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="a9fae-111">Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="a9fae-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="a9fae-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a9fae-112">Optional.</span></span> <span data-ttu-id="a9fae-113">Kaynak için mantıksal ad; yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="a9fae-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="a9fae-114">Varsayılan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="a9fae-114">The default is the name of the file.</span></span> <span data-ttu-id="a9fae-115">İsteğe bağlı olarak, kaynağın aşağıdaki gibi ortak veya özel derleme bildiriminde olup olmadığını belirtebilirsiniz: `/res:``filename.res`,`myname.res`,`public`</span><span class="sxs-lookup"><span data-stu-id="a9fae-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `/res:``filename.res`,`myname.res`,`public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9fae-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9fae-116">Remarks</span></span>  
 <span data-ttu-id="a9fae-117">Kullanım `/linkresource` kaynak dosyasını çıktı dosyasına yerleştirerek olmadan bir kaynağı bir derlemeye bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="a9fae-117">Use `/linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="a9fae-118">Varsa `filename` olan bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , örneğin, tarafından oluşturulan kaynak dosyasını [Resgen.exe (kaynak dosya oluşturucu)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı (bkz: <xref:System.Resources.ResourceManager> daha fazla bilgi için).</span><span class="sxs-lookup"><span data-stu-id="a9fae-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="a9fae-119">Çalışma zamanında tüm diğer kaynaklarına erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="a9fae-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="a9fae-120">Kısa formunu `/resource` olan `/res`.</span><span class="sxs-lookup"><span data-stu-id="a9fae-120">The short form of `/resource` is `/res`.</span></span>  
  
 <span data-ttu-id="a9fae-121">Nasıl ayarlanacağı hakkında bilgi için `/resource` Visual Studio IDE'de bkz [yönetme uygulama kaynakları (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a9fae-121">For information about how to set `/resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9fae-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9fae-122">Example</span></span>  
 <span data-ttu-id="a9fae-123">Aşağıdaki kod derlerken `In.vb` ve ekler kaynak dosyası `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="a9fae-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9fae-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9fae-124">See Also</span></span>  
 [<span data-ttu-id="a9fae-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a9fae-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a9fae-126">/ win32resource</span><span class="sxs-lookup"><span data-stu-id="a9fae-126">/win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [<span data-ttu-id="a9fae-127">/ linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9fae-127">/linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [<span data-ttu-id="a9fae-128">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9fae-128">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="a9fae-129">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="a9fae-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

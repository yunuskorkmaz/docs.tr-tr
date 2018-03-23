---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b84631e0c09521a6f4ff9e06b2a80e0885862e
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="9f06a-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f06a-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="9f06a-103">Yönetilen kaynak bağlantısını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f06a-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f06a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f06a-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9f06a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f06a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="9f06a-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9f06a-106">Required.</span></span> <span data-ttu-id="9f06a-107">Derlemeye bağlamak için kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="9f06a-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="9f06a-108">Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="9f06a-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="9f06a-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9f06a-109">Optional.</span></span> <span data-ttu-id="9f06a-110">Kaynak için mantıksal adı.</span><span class="sxs-lookup"><span data-stu-id="9f06a-110">The logical name for the resource.</span></span> <span data-ttu-id="9f06a-111">Kaynak yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="9f06a-111">The name that is used to load the resource.</span></span> <span data-ttu-id="9f06a-112">Varsayılan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="9f06a-112">The default is the name of the file.</span></span> <span data-ttu-id="9f06a-113">İsteğe bağlı olarak, dosya gibi ortak veya özel derleme bildiriminde olup olmadığını belirtebilirsiniz: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="9f06a-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="9f06a-114">Varsayılan olarak, `filename` bütünleştirilmiş kodunda geneldir.</span><span class="sxs-lookup"><span data-stu-id="9f06a-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f06a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f06a-115">Remarks</span></span>  
 <span data-ttu-id="9f06a-116">`-linkresource` Seçeneği değil katıştırmak kaynak dosyasını çıktı dosyasına; kullanın `-resource` Bunu yapmak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9f06a-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="9f06a-117">`-linkresource` Seçeneği birini gerektirir `-target` dışında seçenekleri `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="9f06a-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="9f06a-118">Varsa `filename` olan bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , örneğin, tarafından oluşturulan kaynak dosyasını [Resgen.exe (kaynak dosya oluşturucu)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9f06a-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="9f06a-119">(Daha fazla bilgi için bkz: <xref:System.Resources.ResourceManager>.) Çalışma zamanında tüm diğer kaynaklarına erişmek için ile başlayan yöntemleri kullanan `GetManifestResource` içinde <xref:System.Reflection.Assembly> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9f06a-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="9f06a-120">Dosya adı herhangi bir dosya biçiminde olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f06a-120">The file name can be any file format.</span></span> <span data-ttu-id="9f06a-121">Örneğin, böylece genel derleme önbelleğine yüklü ve yönetilen kod derlemesindeki erişilen derleme yerel bir DLL parçası haline getirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f06a-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="9f06a-122">Kısa formunu `-linkresource` olan `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="9f06a-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f06a-123">`-linkresource` Seçeneği Visual Studio geliştirme ortamından kullanılabilir değil; komut satırından derleme zaman yalnızca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f06a-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f06a-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f06a-124">Example</span></span>  
 <span data-ttu-id="9f06a-125">Aşağıdaki kod derlerken `in.vb` ve kaynak dosyası bağlantılar `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="9f06a-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f06a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f06a-126">See Also</span></span>  
 [<span data-ttu-id="9f06a-127">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="9f06a-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9f06a-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f06a-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="9f06a-129">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f06a-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [<span data-ttu-id="9f06a-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="9f06a-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

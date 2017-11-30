---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="ec701-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec701-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="ec701-103">Yönetilen kaynak bağlantısını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec701-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec701-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec701-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ec701-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ec701-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="ec701-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ec701-106">Required.</span></span> <span data-ttu-id="ec701-107">Derlemeye bağlamak için kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="ec701-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="ec701-108">Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="ec701-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="ec701-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ec701-109">Optional.</span></span> <span data-ttu-id="ec701-110">Kaynak için mantıksal adı.</span><span class="sxs-lookup"><span data-stu-id="ec701-110">The logical name for the resource.</span></span> <span data-ttu-id="ec701-111">Kaynak yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="ec701-111">The name that is used to load the resource.</span></span> <span data-ttu-id="ec701-112">Varsayılan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="ec701-112">The default is the name of the file.</span></span> <span data-ttu-id="ec701-113">İsteğe bağlı olarak, dosya gibi ortak veya özel derleme bildiriminde olup olmadığını belirtebilirsiniz: `/linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="ec701-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="ec701-114">Varsayılan olarak, `filename` bütünleştirilmiş kodunda geneldir.</span><span class="sxs-lookup"><span data-stu-id="ec701-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec701-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec701-115">Remarks</span></span>  
 <span data-ttu-id="ec701-116">`/linkresource` Seçeneği değil katıştırmak kaynak dosyasını çıktı dosyasına; kullanın `/resource` Bunu yapmak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ec701-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="ec701-117">`/linkresource` Seçeneği birini gerektirir `/target` dışında seçenekleri `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="ec701-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="ec701-118">Varsa `filename` olan bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , örneğin, tarafından oluşturulan kaynak dosyasını [Resgen.exe (kaynak dosya oluşturucu)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ec701-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="ec701-119">(Daha fazla bilgi için bkz: <xref:System.Resources.ResourceManager>.) Çalışma zamanında tüm diğer kaynaklarına erişmek için ile başlayan yöntemleri kullanan `GetManifestResource` içinde <xref:System.Reflection.Assembly> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ec701-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="ec701-120">Dosya adı herhangi bir dosya biçiminde olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec701-120">The file name can be any file format.</span></span> <span data-ttu-id="ec701-121">Örneğin, böylece genel derleme önbelleğine yüklü ve yönetilen kod derlemesindeki erişilen derleme yerel bir DLL parçası haline getirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec701-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="ec701-122">Kısa formunu `/linkresource` olan `/linkres`.</span><span class="sxs-lookup"><span data-stu-id="ec701-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec701-123">`/linkresource` Seçeneği Visual Studio geliştirme ortamından kullanılabilir değil; komut satırından derleme zaman yalnızca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec701-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec701-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec701-124">Example</span></span>  
 <span data-ttu-id="ec701-125">Aşağıdaki kod derlerken `In.vb` ve kaynak dosyası bağlantılar `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="ec701-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec701-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec701-126">See Also</span></span>  
 [<span data-ttu-id="ec701-127">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ec701-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ec701-128">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec701-128">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="ec701-129">/ Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec701-129">/resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [<span data-ttu-id="ec701-130">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="ec701-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

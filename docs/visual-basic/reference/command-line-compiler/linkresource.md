---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 97e0ccd46f413cc05b659731436bb141ee178419
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45596634"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="4656f-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4656f-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="4656f-103">Yönetilen kaynağa bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4656f-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4656f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4656f-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4656f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4656f-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="4656f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4656f-106">Required.</span></span> <span data-ttu-id="4656f-107">Derlemeye bağlamak için kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="4656f-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="4656f-108">Dosya adı boşluk içeriyorsa adı tırnak içine alın. ("").</span><span class="sxs-lookup"><span data-stu-id="4656f-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="4656f-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4656f-109">Optional.</span></span> <span data-ttu-id="4656f-110">Kaynağın mantıksal adı.</span><span class="sxs-lookup"><span data-stu-id="4656f-110">The logical name for the resource.</span></span> <span data-ttu-id="4656f-111">Kaynak yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="4656f-111">The name that is used to load the resource.</span></span> <span data-ttu-id="4656f-112">Varsayılan dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="4656f-112">The default is the name of the file.</span></span> <span data-ttu-id="4656f-113">İsteğe bağlı olarak, dosyayı örneğin genel veya özel derleme bildiriminde olup olmadığını belirtebilirsiniz: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="4656f-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="4656f-114">Varsayılan olarak, `filename` derleme içinde geneldir.</span><span class="sxs-lookup"><span data-stu-id="4656f-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4656f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4656f-115">Remarks</span></span>  
 <span data-ttu-id="4656f-116">`-linkresource` Kullanın; seçeneği değil ekleme kaynak dosyası çıkış dosyasına `-resource` Bunu yapmak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4656f-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="4656f-117">`-linkresource` Seçeneği birini gerektirir `-target` dışında seçenekleri `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="4656f-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="4656f-118">Varsa `filename` olduğu bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , örneğin, göre oluşturulmuş kaynak dosyası [Resgen.exe (kaynak dosya oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4656f-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="4656f-119">(Daha fazla bilgi için <xref:System.Resources.ResourceManager>.) Çalışma zamanında diğer kaynaklara erişmek için Şununla yöntemleri kullanan `GetManifestResource` içinde <xref:System.Reflection.Assembly> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4656f-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="4656f-120">Dosya adı, herhangi bir dosya biçiminde olabilir.</span><span class="sxs-lookup"><span data-stu-id="4656f-120">The file name can be any file format.</span></span> <span data-ttu-id="4656f-121">Örneğin, böylece genel derleme önbelleğine yüklenebilir ve derlemedeki yönetilen koddan erişilebilir bütünleştirilmiş kodun yerel bir DLL parçası haline getirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4656f-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="4656f-122">Kısa formunu da `-linkresource` olduğu `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="4656f-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4656f-123">`-linkresource` Seçeneği Visual Studio geliştirme ortamından kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4656f-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4656f-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="4656f-124">Example</span></span>  
 <span data-ttu-id="4656f-125">Aşağıdaki kod derlenir `in.vb` ve kaynak dosyası bağlantılar `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="4656f-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4656f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4656f-126">See also</span></span>

- [<span data-ttu-id="4656f-127">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="4656f-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
- [<span data-ttu-id="4656f-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4656f-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
- [<span data-ttu-id="4656f-129">-Kaynak (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4656f-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
- [<span data-ttu-id="4656f-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4656f-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

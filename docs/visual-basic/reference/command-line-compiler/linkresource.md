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
ms.openlocfilehash: d92b0d08daf660880b648875c67c3b78069143d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924853"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="a8475-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8475-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="a8475-103">Yönetilen bir kaynağa bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8475-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8475-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8475-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a8475-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a8475-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="a8475-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a8475-106">Required.</span></span> <span data-ttu-id="a8475-107">Derlemeye bağlanacak kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="a8475-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="a8475-108">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="a8475-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="a8475-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a8475-109">Optional.</span></span> <span data-ttu-id="a8475-110">Kaynağın mantıksal adı.</span><span class="sxs-lookup"><span data-stu-id="a8475-110">The logical name for the resource.</span></span> <span data-ttu-id="a8475-111">Kaynağı yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="a8475-111">The name that is used to load the resource.</span></span> <span data-ttu-id="a8475-112">Varsayılan değer, dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="a8475-112">The default is the name of the file.</span></span> <span data-ttu-id="a8475-113">İsteğe bağlı olarak, dosyanın derleme bildiriminde genel mi yoksa özel mi olduğunu belirtebilirsiniz, örneğin: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="a8475-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="a8475-114">Varsayılan olarak, `filename` derlemede ortaktır.</span><span class="sxs-lookup"><span data-stu-id="a8475-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8475-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8475-115">Remarks</span></span>  
 <span data-ttu-id="a8475-116">Bu seçenek, kaynak dosyasını çıkış dosyasına eklemez; bunu yapmak için `-resource` seçeneğini kullanın. `-linkresource`</span><span class="sxs-lookup"><span data-stu-id="a8475-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="a8475-117">Seçeneği `-linkresource` , dışındaki `-target` seçeneklerden `-target:module`birini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a8475-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="a8475-118">, Örneğin, [Resgen. exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. `filename`</span><span class="sxs-lookup"><span data-stu-id="a8475-118">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="a8475-119">(Daha fazla bilgi için bkz <xref:System.Resources.ResourceManager>..) Çalışma zamanında diğer tüm kaynaklara erişmek için `GetManifestResource` <xref:System.Reflection.Assembly> sınıfında başlayan yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8475-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="a8475-120">Dosya adı herhangi bir dosya biçimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8475-120">The file name can be any file format.</span></span> <span data-ttu-id="a8475-121">Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8475-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="a8475-122">`-linkresource` Öğesinin`-linkres`kısa biçimi.</span><span class="sxs-lookup"><span data-stu-id="a8475-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8475-123">Bu `-linkresource` seçenek, Visual Studio geliştirme ortamından kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8475-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8475-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8475-124">Example</span></span>  
 <span data-ttu-id="a8475-125">Aşağıdaki kod derlenir `in.vb` ve kaynak dosyasına `rf.resource`bağlanır.</span><span class="sxs-lookup"><span data-stu-id="a8475-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8475-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8475-126">See also</span></span>

- [<span data-ttu-id="a8475-127">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a8475-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a8475-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8475-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="a8475-129">-Kaynak (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8475-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="a8475-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a8475-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

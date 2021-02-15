---
description: :-Linkresource (Visual Basic) hakkında daha fazla bilgi edinin
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 21fc47ecff44230bda0f445bc695706b5ae91eff
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463708"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="4b0a7-103">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b0a7-103">-linkresource (Visual Basic)</span></span>

<span data-ttu-id="4b0a7-104">Yönetilen bir kaynağa bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-104">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b0a7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b0a7-105">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="4b0a7-106">veya</span><span class="sxs-lookup"><span data-stu-id="4b0a7-106">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b0a7-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="4b0a7-107">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="4b0a7-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-108">Required.</span></span> <span data-ttu-id="4b0a7-109">Derlemeye bağlanacak kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-109">The resource file to link to the assembly.</span></span> <span data-ttu-id="4b0a7-110">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="4b0a7-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-111">Optional.</span></span> <span data-ttu-id="4b0a7-112">Kaynağın mantıksal adı.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-112">The logical name for the resource.</span></span> <span data-ttu-id="4b0a7-113">Kaynağı yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-113">The name that is used to load the resource.</span></span> <span data-ttu-id="4b0a7-114">Varsayılan değer, dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-114">The default is the name of the file.</span></span> <span data-ttu-id="4b0a7-115">İsteğe bağlı olarak, dosyanın derleme bildiriminde genel mi yoksa özel mi olduğunu belirtebilirsiniz, örneğin: `-linkres:filename.res,myname.res,public` .</span><span class="sxs-lookup"><span data-stu-id="4b0a7-115">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="4b0a7-116">Varsayılan olarak, `filename` derlemede ortaktır.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-116">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b0a7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b0a7-117">Remarks</span></span>  

 <span data-ttu-id="4b0a7-118">`-linkresource`Bu seçenek, kaynak dosyasını çıkış dosyasına eklemez; `-resource` bunu yapmak için seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-118">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="4b0a7-119">Seçeneği, dışındaki `-linkresource` seçeneklerden birini gerektirir `-target` `-target:module` .</span><span class="sxs-lookup"><span data-stu-id="4b0a7-119">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="4b0a7-120">, `filename` Örneğin, [Resgen.exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-120">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="4b0a7-121">(Daha fazla bilgi için bkz <xref:System.Resources.ResourceManager> ..) Çalışma zamanında diğer tüm kaynaklara erişmek için sınıfında başlayan yöntemleri kullanın `GetManifestResource` <xref:System.Reflection.Assembly> .</span><span class="sxs-lookup"><span data-stu-id="4b0a7-121">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="4b0a7-122">Dosya adı herhangi bir dosya biçimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-122">The file name can be any file format.</span></span> <span data-ttu-id="4b0a7-123">Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-123">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="4b0a7-124">Öğesinin kısa biçimi `-linkresource` `-linkres` .</span><span class="sxs-lookup"><span data-stu-id="4b0a7-124">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b0a7-125">`-linkresource`Bu seçenek, Visual Studio geliştirme ortamından kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-125">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b0a7-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b0a7-126">Example</span></span>  

 <span data-ttu-id="4b0a7-127">Aşağıdaki kod derlenir `in.vb` ve kaynak dosyasına bağlanır `rf.resource` .</span><span class="sxs-lookup"><span data-stu-id="4b0a7-127">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b0a7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b0a7-128">See also</span></span>

- [<span data-ttu-id="4b0a7-129">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="4b0a7-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4b0a7-130">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b0a7-130">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="4b0a7-131">-Kaynak (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b0a7-131">-resource (Visual Basic)</span></span>](resource.md)
- [<span data-ttu-id="4b0a7-132">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4b0a7-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

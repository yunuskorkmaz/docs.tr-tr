---
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
ms.openlocfilehash: 0315645eccdc899ac9cf4d0be105297e1fa2a4c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335489"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="2f86a-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f86a-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="2f86a-103">Yönetilen bir kaynağa bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f86a-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f86a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f86a-104">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="2f86a-105">or</span><span class="sxs-lookup"><span data-stu-id="2f86a-105">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f86a-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2f86a-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="2f86a-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2f86a-107">Required.</span></span> <span data-ttu-id="2f86a-108">Derlemeye bağlanacak kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="2f86a-108">The resource file to link to the assembly.</span></span> <span data-ttu-id="2f86a-109">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="2f86a-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="2f86a-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2f86a-110">Optional.</span></span> <span data-ttu-id="2f86a-111">Kaynağın mantıksal adı.</span><span class="sxs-lookup"><span data-stu-id="2f86a-111">The logical name for the resource.</span></span> <span data-ttu-id="2f86a-112">Kaynağı yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="2f86a-112">The name that is used to load the resource.</span></span> <span data-ttu-id="2f86a-113">Varsayılan değer, dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="2f86a-113">The default is the name of the file.</span></span> <span data-ttu-id="2f86a-114">İsteğe bağlı olarak, dosyanın derleme bildiriminde genel mi yoksa özel mi olduğunu belirtebilirsiniz, örneğin: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="2f86a-114">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="2f86a-115">Varsayılan olarak, `filename` derlemede ortaktır.</span><span class="sxs-lookup"><span data-stu-id="2f86a-115">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f86a-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f86a-116">Remarks</span></span>  
 <span data-ttu-id="2f86a-117">Bu `-linkresource` seçenek, kaynak dosyasını çıkış dosyasına eklemez; Bunu yapmak `-resource` için seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f86a-117">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="2f86a-118">Seçeneği `-linkresource` , dışındaki `-target` seçeneklerden birini gerektirir `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="2f86a-118">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="2f86a-119">, Örneğin, [Resgen. exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. `filename`</span><span class="sxs-lookup"><span data-stu-id="2f86a-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="2f86a-120">(Daha fazla bilgi için bkz <xref:System.Resources.ResourceManager>..) Çalışma zamanında diğer tüm kaynaklara erişmek için `GetManifestResource` <xref:System.Reflection.Assembly> sınıfında başlayan yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f86a-120">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="2f86a-121">Dosya adı herhangi bir dosya biçimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f86a-121">The file name can be any file format.</span></span> <span data-ttu-id="2f86a-122">Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f86a-122">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="2f86a-123">Öğesinin `-linkresource` kısa biçimi `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="2f86a-123">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f86a-124">Bu `-linkresource` seçenek, Visual Studio geliştirme ortamında kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f86a-124">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f86a-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f86a-125">Example</span></span>  
 <span data-ttu-id="2f86a-126">Aşağıdaki kod derlenir `in.vb` ve kaynak dosyasına `rf.resource`bağlanır.</span><span class="sxs-lookup"><span data-stu-id="2f86a-126">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f86a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f86a-127">See also</span></span>

- [<span data-ttu-id="2f86a-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2f86a-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2f86a-129">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f86a-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="2f86a-130">-Kaynak (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f86a-130">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="2f86a-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2f86a-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

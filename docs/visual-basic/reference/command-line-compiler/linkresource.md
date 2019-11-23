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
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="4973f-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4973f-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="4973f-103">Creates a link to a managed resource.</span><span class="sxs-lookup"><span data-stu-id="4973f-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4973f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4973f-104">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="4973f-105">veya</span><span class="sxs-lookup"><span data-stu-id="4973f-105">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4973f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4973f-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="4973f-107">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4973f-107">Required.</span></span> <span data-ttu-id="4973f-108">The resource file to link to the assembly.</span><span class="sxs-lookup"><span data-stu-id="4973f-108">The resource file to link to the assembly.</span></span> <span data-ttu-id="4973f-109">If the file name contains a space, enclose the name in quotation marks (" ").</span><span class="sxs-lookup"><span data-stu-id="4973f-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="4973f-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4973f-110">Optional.</span></span> <span data-ttu-id="4973f-111">The logical name for the resource.</span><span class="sxs-lookup"><span data-stu-id="4973f-111">The logical name for the resource.</span></span> <span data-ttu-id="4973f-112">The name that is used to load the resource.</span><span class="sxs-lookup"><span data-stu-id="4973f-112">The name that is used to load the resource.</span></span> <span data-ttu-id="4973f-113">The default is the name of the file.</span><span class="sxs-lookup"><span data-stu-id="4973f-113">The default is the name of the file.</span></span> <span data-ttu-id="4973f-114">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="4973f-114">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="4973f-115">By default, `filename` is public in the assembly.</span><span class="sxs-lookup"><span data-stu-id="4973f-115">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4973f-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4973f-116">Remarks</span></span>  
 <span data-ttu-id="4973f-117">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span><span class="sxs-lookup"><span data-stu-id="4973f-117">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="4973f-118">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="4973f-118">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="4973f-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span><span class="sxs-lookup"><span data-stu-id="4973f-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="4973f-120">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span><span class="sxs-lookup"><span data-stu-id="4973f-120">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="4973f-121">The file name can be any file format.</span><span class="sxs-lookup"><span data-stu-id="4973f-121">The file name can be any file format.</span></span> <span data-ttu-id="4973f-122">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span><span class="sxs-lookup"><span data-stu-id="4973f-122">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="4973f-123">The short form of `-linkresource` is `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="4973f-123">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4973f-124">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span><span class="sxs-lookup"><span data-stu-id="4973f-124">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4973f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="4973f-125">Example</span></span>  
 <span data-ttu-id="4973f-126">The following code compiles `in.vb` and links to resource file `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="4973f-126">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4973f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4973f-127">See also</span></span>

- [<span data-ttu-id="4973f-128">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="4973f-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4973f-129">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4973f-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="4973f-130">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4973f-130">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="4973f-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4973f-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

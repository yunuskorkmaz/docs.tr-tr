---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 726f3dd179aedb39b578c8580c9632182af2d5e0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085132"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="941ba-102">-Kaynak (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="941ba-102">-resource (Visual Basic)</span></span>

<span data-ttu-id="941ba-103">Bir derlemede yönetilen bir kaynak gömer.</span><span class="sxs-lookup"><span data-stu-id="941ba-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941ba-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="941ba-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="941ba-105">veya</span><span class="sxs-lookup"><span data-stu-id="941ba-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="941ba-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="941ba-106">Arguments</span></span>  
  
|<span data-ttu-id="941ba-107">Terim</span><span class="sxs-lookup"><span data-stu-id="941ba-107">Term</span></span>|<span data-ttu-id="941ba-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="941ba-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="941ba-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="941ba-109">Required.</span></span> <span data-ttu-id="941ba-110">Çıkış dosyasına eklemek için kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="941ba-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="941ba-111">Varsayılan olarak, `filename` derlemede ortaktır.</span><span class="sxs-lookup"><span data-stu-id="941ba-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="941ba-112">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="941ba-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="941ba-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="941ba-113">Optional.</span></span> <span data-ttu-id="941ba-114">Kaynağın mantıksal adı; yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="941ba-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="941ba-115">Varsayılan değer, dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="941ba-115">The default is the name of the file.</span></span> <span data-ttu-id="941ba-116">İsteğe bağlı olarak, aşağıdaki gibi, derleme bildiriminde kaynağın genel mi yoksa özel mi olduğunu belirtebilirsiniz: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="941ba-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="941ba-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="941ba-117">Remarks</span></span>  

 <span data-ttu-id="941ba-118">Kaynak `-linkresource` dosyasını çıkış dosyasına yerleştirmeksizin bir kaynağı derlemeye bağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="941ba-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="941ba-119">`filename`Örneğin, [Resgen.exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası varsa, <xref:System.Resources> ad alanındaki üyelerle erişilebilir ( <xref:System.Resources.ResourceManager> daha fazla bilgi için bkz.).</span><span class="sxs-lookup"><span data-stu-id="941ba-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="941ba-120">Çalışma zamanında diğer tüm kaynaklara erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A> , <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> .</span><span class="sxs-lookup"><span data-stu-id="941ba-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="941ba-121">Öğesinin kısa biçimi `-resource` `-res` .</span><span class="sxs-lookup"><span data-stu-id="941ba-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="941ba-122">Visual Studio IDE 'de nasıl ayarlanacağı hakkında bilgi için `-resource` bkz. [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="941ba-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="941ba-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="941ba-123">Example</span></span>  

 <span data-ttu-id="941ba-124">Aşağıdaki kod, `In.vb` kaynak dosyasını derler ve iliştirir `Rf.resource` .</span><span class="sxs-lookup"><span data-stu-id="941ba-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="941ba-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="941ba-125">See also</span></span>

- [<span data-ttu-id="941ba-126">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="941ba-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="941ba-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="941ba-127">-win32resource</span></span>](win32resource.md)
- [<span data-ttu-id="941ba-128">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="941ba-128">-linkresource (Visual Basic)</span></span>](linkresource.md)
- [<span data-ttu-id="941ba-129">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="941ba-129">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="941ba-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="941ba-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

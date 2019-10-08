---
title: -Kaynak (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 5bedc346381f6de293933dce14a8c5c3044b246f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005196"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="7020f-102">-Kaynak (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7020f-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="7020f-103">Bir derlemede yönetilen bir kaynak gömer.</span><span class="sxs-lookup"><span data-stu-id="7020f-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7020f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7020f-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="7020f-105">veya</span><span class="sxs-lookup"><span data-stu-id="7020f-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7020f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="7020f-106">Arguments</span></span>  
  
|<span data-ttu-id="7020f-107">Terim</span><span class="sxs-lookup"><span data-stu-id="7020f-107">Term</span></span>|<span data-ttu-id="7020f-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="7020f-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="7020f-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7020f-109">Required.</span></span> <span data-ttu-id="7020f-110">Çıkış dosyasına eklemek için kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="7020f-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="7020f-111">Varsayılan olarak, `filename`, derlemede ortaktır.</span><span class="sxs-lookup"><span data-stu-id="7020f-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="7020f-112">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="7020f-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="7020f-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7020f-113">Optional.</span></span> <span data-ttu-id="7020f-114">Kaynağın mantıksal adı; yüklemek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="7020f-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="7020f-115">Varsayılan değer, dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="7020f-115">The default is the name of the file.</span></span> <span data-ttu-id="7020f-116">İsteğe bağlı olarak, aşağıdaki gibi, derleme bildiriminde kaynağın genel mi yoksa özel mi olduğunu belirtebilirsiniz: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="7020f-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7020f-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7020f-117">Remarks</span></span>  
 <span data-ttu-id="7020f-118">Kaynak dosyasını çıkış dosyasına yerleştirmeksizin bir kaynağı derlemeye bağlamak için `-linkresource` kullanın.</span><span class="sxs-lookup"><span data-stu-id="7020f-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="7020f-119">@No__t-0 oluşturulmuş bir .NET Framework kaynak dosyası ise (örneğin, [Resgen. exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında, <xref:System.Resources> ad alanındaki üyelerle erişilebilir (daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager>).</span><span class="sxs-lookup"><span data-stu-id="7020f-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="7020f-120">Çalışma zamanında diğer tüm kaynaklara erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="7020f-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="7020f-121">@No__t-0 ' ın kısa biçimi `-res` ' dir.</span><span class="sxs-lookup"><span data-stu-id="7020f-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="7020f-122">Visual Studio IDE 'de `-resource` ' ı ayarlama hakkında daha fazla bilgi için bkz. [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7020f-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7020f-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="7020f-123">Example</span></span>  
 <span data-ttu-id="7020f-124">Aşağıdaki kod `In.vb` derler ve kaynak dosyası `Rf.resource` ' i iliştirir.</span><span class="sxs-lookup"><span data-stu-id="7020f-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7020f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7020f-125">See also</span></span>

- [<span data-ttu-id="7020f-126">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7020f-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7020f-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="7020f-127">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [<span data-ttu-id="7020f-128">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7020f-128">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [<span data-ttu-id="7020f-129">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7020f-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="7020f-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="7020f-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

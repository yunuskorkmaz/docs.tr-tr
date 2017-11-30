---
title: /reference (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f8c6851802afa818cc80b3f6d7eafc2ef47ac689
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reference-visual-basic"></a><span data-ttu-id="1e4c2-102">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e4c2-102">/reference (Visual Basic)</span></span>
<span data-ttu-id="1e4c2-103">Belirtilen derlemelerde türü bilgileri şu anda derlediğiniz proje kullanılabilir hale getirmek derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e4c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e4c2-104">Syntax</span></span>  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e4c2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1e4c2-105">Arguments</span></span>  
  
|<span data-ttu-id="1e4c2-106">Terim</span><span class="sxs-lookup"><span data-stu-id="1e4c2-106">Term</span></span>|<span data-ttu-id="1e4c2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="1e4c2-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="1e4c2-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-108">Required.</span></span> <span data-ttu-id="1e4c2-109">Derleme dosya adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="1e4c2-110">Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e4c2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e4c2-111">Remarks</span></span>  
 <span data-ttu-id="1e4c2-112">Derleme meta verilerini içe aktardığınız dosyaları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="1e4c2-113">Yalnızca genel türleri dışında derleme görünür.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="1e4c2-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçenek, bir modülden meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="1e4c2-115">Bir derlemeye (a derlemesi) başvurursanız kendisi başka bir derlemeye (B derlemesi) başvuran, varsa B derlemesine başvuru gerekir:</span><span class="sxs-lookup"><span data-stu-id="1e4c2-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="1e4c2-116">Derlemesi türünden bir türden devralır veya derleme B'deki bir arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="1e4c2-117">Alan, özellik, olay veya b derlemesinden dönüş türü veya parametresi türü olan yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="1e4c2-118">Kullanım [/Libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) bir veya daha fazla derleme başvurularını bulunduğu dizini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-118">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="1e4c2-119">Derleyicinin türü derlemedeki (modülü değil) tanımak bu türü çözümlemeye zorlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="1e4c2-120">Türünün bir örneği tanımlamak için nasıl Bunu yapmak için bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="1e4c2-121">Diğer yolları derleyici için derlemeyi türü adları çözümlemek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="1e4c2-122">Örneğin, bir derlemede türünden devralan, tür adı sonra derleyiciye bilinir.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="1e4c2-123">Başvuruları yaygın olarak kullanılan Vbc.rsp yanıt dosyası [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="1e4c2-124">Kullanmak `/noconfig` derleyicinin Vbc.rsp kullanmasını istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-124">Use `/noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="1e4c2-125">Kısa formunu `/reference` olan `/r`.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-125">The short form of `/reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e4c2-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e4c2-126">Example</span></span>  
 <span data-ttu-id="1e4c2-127">Aşağıdaki kod kaynak dosyasını derler `Input.vb` ve başvuru derlemelerden `Metad1.dll` ve `Metad2.dll` üretmek için `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-127">The following code compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e4c2-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e4c2-128">See Also</span></span>  
 [<span data-ttu-id="1e4c2-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="1e4c2-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1e4c2-130">/ noconfig</span><span class="sxs-lookup"><span data-stu-id="1e4c2-130">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="1e4c2-131">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e4c2-131">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="1e4c2-132">Ortak</span><span class="sxs-lookup"><span data-stu-id="1e4c2-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="1e4c2-133">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="1e4c2-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

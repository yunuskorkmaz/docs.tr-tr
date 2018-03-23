---
title: -başvuru (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba879dd7079b35bea50c4a6c1d67da7aa57110f6
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="01ec1-102">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01ec1-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="01ec1-103">Belirtilen derlemelerde türü bilgileri şu anda derlediğiniz proje kullanılabilir hale getirmek derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="01ec1-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ec1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01ec1-104">Syntax</span></span>  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="01ec1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="01ec1-105">Arguments</span></span>  
  
|<span data-ttu-id="01ec1-106">Terim</span><span class="sxs-lookup"><span data-stu-id="01ec1-106">Term</span></span>|<span data-ttu-id="01ec1-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="01ec1-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="01ec1-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="01ec1-108">Required.</span></span> <span data-ttu-id="01ec1-109">Derleme dosya adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="01ec1-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="01ec1-110">Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="01ec1-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01ec1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01ec1-111">Remarks</span></span>  
 <span data-ttu-id="01ec1-112">Derleme meta verilerini içe aktardığınız dosyaları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="01ec1-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="01ec1-113">Yalnızca genel türleri dışında derleme görünür.</span><span class="sxs-lookup"><span data-stu-id="01ec1-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="01ec1-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçenek, bir modülden meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="01ec1-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="01ec1-115">Bir derlemeye (a derlemesi) başvurursanız kendisi başka bir derlemeye (B derlemesi) başvuran, varsa B derlemesine başvuru gerekir:</span><span class="sxs-lookup"><span data-stu-id="01ec1-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="01ec1-116">Derlemesi türünden bir türden devralır veya derleme B'deki bir arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="01ec1-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="01ec1-117">Alan, özellik, olay veya b derlemesinden dönüş türü veya parametresi türü olan yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="01ec1-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="01ec1-118">Kullanım [- LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) bir veya daha fazla derleme başvurularını bulunduğu dizini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="01ec1-118">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="01ec1-119">Derleyicinin türü derlemedeki (modülü değil) tanımak bu türü çözümlemeye zorlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01ec1-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="01ec1-120">Türünün bir örneği tanımlamak için nasıl Bunu yapmak için bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01ec1-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="01ec1-121">Diğer yolları derleyici için derlemeyi türü adları çözümlemek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01ec1-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="01ec1-122">Örneğin, bir derlemede türünden devralan, tür adı sonra derleyiciye bilinir.</span><span class="sxs-lookup"><span data-stu-id="01ec1-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="01ec1-123">Başvuruları yaygın olarak kullanılan Vbc.rsp yanıt dosyası [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01ec1-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="01ec1-124">Kullanmak `-noconfig` derleyicinin Vbc.rsp kullanmasını istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="01ec1-124">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="01ec1-125">Kısa formunu `-reference` olan `/r`.</span><span class="sxs-lookup"><span data-stu-id="01ec1-125">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01ec1-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="01ec1-126">Example</span></span>  
 <span data-ttu-id="01ec1-127">Aşağıdaki komutu kaynak dosyasını derler `Input.vb` ve başvuru derlemelerden `Metad1.dll` ve `Metad2.dll` üretmek için `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="01ec1-127">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="01ec1-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01ec1-128">See Also</span></span>  
 [<span data-ttu-id="01ec1-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="01ec1-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="01ec1-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="01ec1-130">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="01ec1-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01ec1-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="01ec1-132">Public</span><span class="sxs-lookup"><span data-stu-id="01ec1-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="01ec1-133">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="01ec1-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

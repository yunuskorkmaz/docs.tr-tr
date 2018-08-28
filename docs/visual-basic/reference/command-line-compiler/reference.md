---
title: -başvuru (Visual Basic)
ms.date: 03/13/2018
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
ms.openlocfilehash: cb5d3b4c50a9c22880bdcc8406835cf51481e3cd
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003131"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="25d25-102">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25d25-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="25d25-103">Derleyicinin tür bilgilerini belirli derlemelerde şu anda derleme proje kullanılabilir hale getirmek neden olur.</span><span class="sxs-lookup"><span data-stu-id="25d25-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25d25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25d25-104">Syntax</span></span>  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="25d25-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="25d25-105">Arguments</span></span>  
  
|<span data-ttu-id="25d25-106">Terim</span><span class="sxs-lookup"><span data-stu-id="25d25-106">Term</span></span>|<span data-ttu-id="25d25-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="25d25-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="25d25-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="25d25-108">Required.</span></span> <span data-ttu-id="25d25-109">Derleme dosya adlarının virgülle ayrılmış liste.</span><span class="sxs-lookup"><span data-stu-id="25d25-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="25d25-110">Dosya adı boşluk içeriyorsa adı tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="25d25-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25d25-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25d25-111">Remarks</span></span>  
 <span data-ttu-id="25d25-112">İçeri aktardığınız dosya, derleme meta verileri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="25d25-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="25d25-113">Yalnızca genel türleri derlemenin dışında görünür.</span><span class="sxs-lookup"><span data-stu-id="25d25-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="25d25-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçenek, bir modülden meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="25d25-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="25d25-115">Bir bütünleştirilmiş kodu (bütünleştirilmiş kod: A) başvuruda bulunursanız kendisi başvuran bir derlemeyle (derlemeyi B), başvuru derlemesi B, gerekir:</span><span class="sxs-lookup"><span data-stu-id="25d25-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="25d25-116">Bir derlemeden bir tür bir tür tarafından devralındığında veya derleme B'deki bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="25d25-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="25d25-117">Bir alan, özelliği, olay veya dönüş türü veya parametresi türü derleme b olan yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="25d25-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="25d25-118">Kullanım [- LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) için bir veya daha fazla, derleme başvuruları bulunduğu dizini belirtin.</span><span class="sxs-lookup"><span data-stu-id="25d25-118">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="25d25-119">Derleyicinin derlemede (modül değil) bir türü tanıması, türü çözümlemeye zorlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d25-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="25d25-120">Bunu yapmak nasıl ilişkin bir örnek, bir türün örneğini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="25d25-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="25d25-121">Yollar, derleyici bir derlemede bulunan tür adlarını çözmek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25d25-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="25d25-122">Örneğin, bir derleme içinde bulunan bir türden devralıyorsanız, tür adı ardından derleyiciye bildiği.</span><span class="sxs-lookup"><span data-stu-id="25d25-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="25d25-123">Başvuru sık kullanılan nezahrnovat yanıt dosyası [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeleri, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25d25-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="25d25-124">Kullanma `-noconfig` derleyici nezahrnovat kullanmak istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="25d25-124">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="25d25-125">Kısa formunu da `-reference` olduğu `/r`.</span><span class="sxs-lookup"><span data-stu-id="25d25-125">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25d25-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="25d25-126">Example</span></span>  
 <span data-ttu-id="25d25-127">Aşağıdaki komut, kaynak dosyası derler `Input.vb` ve başvuru derlemeleri `Metad1.dll` ve `Metad2.dll` üretmek için `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="25d25-127">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="25d25-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25d25-128">See Also</span></span>  
 [<span data-ttu-id="25d25-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="25d25-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="25d25-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="25d25-130">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="25d25-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25d25-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="25d25-132">Public</span><span class="sxs-lookup"><span data-stu-id="25d25-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="25d25-133">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="25d25-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

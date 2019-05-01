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
ms.openlocfilehash: 21efca701eb16898dd291d73bf0431641ba75d12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788888"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="7b0e6-102">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b0e6-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="7b0e6-103">Derleyicinin tür bilgilerini belirli derlemelerde şu anda derleme proje kullanılabilir hale getirmek neden olur.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b0e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b0e6-104">Syntax</span></span>  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b0e6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7b0e6-105">Arguments</span></span>  
  
|<span data-ttu-id="7b0e6-106">Terim</span><span class="sxs-lookup"><span data-stu-id="7b0e6-106">Term</span></span>|<span data-ttu-id="7b0e6-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="7b0e6-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="7b0e6-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-108">Required.</span></span> <span data-ttu-id="7b0e6-109">Derleme dosya adlarının virgülle ayrılmış liste.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="7b0e6-110">Dosya adı boşluk içeriyorsa adı tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b0e6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b0e6-111">Remarks</span></span>  
 <span data-ttu-id="7b0e6-112">İçeri aktardığınız dosya, derleme meta verileri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="7b0e6-113">Yalnızca genel türleri derlemenin dışında görünür.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="7b0e6-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçenek, bir modülden meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="7b0e6-115">Bir bütünleştirilmiş kodu (bütünleştirilmiş kod: A) başvuruda bulunursanız kendisi başvuran bir derlemeyle (derlemeyi B), başvuru derlemesi B, gerekir:</span><span class="sxs-lookup"><span data-stu-id="7b0e6-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="7b0e6-116">Bir derlemeden bir tür bir tür tarafından devralındığında veya derleme B'deki bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="7b0e6-117">Bir alan, özelliği, olay veya dönüş türü veya parametresi türü derleme b olan yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="7b0e6-118">Kullanım [- LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) için bir veya daha fazla, derleme başvuruları bulunduğu dizini belirtin.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-118">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="7b0e6-119">Derleyicinin derlemede (modül değil) bir türü tanıması, türü çözümlemeye zorlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="7b0e6-120">Bunu yapmak nasıl ilişkin bir örnek, bir türün örneğini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="7b0e6-121">Yollar, derleyici bir derlemede bulunan tür adlarını çözmek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="7b0e6-122">Örneğin, bir derleme içinde bulunan bir türden devralıyorsanız, tür adı ardından derleyiciye bildiği.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="7b0e6-123">Başvuru sık kullanılan nezahrnovat yanıt dosyası [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeleri, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="7b0e6-124">Kullanma `-noconfig` derleyici nezahrnovat kullanmak istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-124">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="7b0e6-125">Kısa formunu da `-reference` olduğu `/r`.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-125">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b0e6-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b0e6-126">Example</span></span>  
 <span data-ttu-id="7b0e6-127">Aşağıdaki komut, kaynak dosyası derler `Input.vb` ve başvuru derlemeleri `Metad1.dll` ve `Metad2.dll` üretmek için `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-127">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b0e6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b0e6-128">See also</span></span>

- [<span data-ttu-id="7b0e6-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7b0e6-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7b0e6-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="7b0e6-130">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="7b0e6-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b0e6-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="7b0e6-132">Public</span><span class="sxs-lookup"><span data-stu-id="7b0e6-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="7b0e6-133">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="7b0e6-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

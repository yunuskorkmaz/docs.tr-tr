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
ms.openlocfilehash: 8f144dbd9376f15ac92e283472dac786a6972045
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775599"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="90ad2-102">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90ad2-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="90ad2-103">Derleyicinin, belirtilen derlemelerde bulunan tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="90ad2-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ad2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90ad2-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="90ad2-105">veya</span><span class="sxs-lookup"><span data-stu-id="90ad2-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="90ad2-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="90ad2-106">Arguments</span></span>  
  
|<span data-ttu-id="90ad2-107">Terim</span><span class="sxs-lookup"><span data-stu-id="90ad2-107">Term</span></span>|<span data-ttu-id="90ad2-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="90ad2-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="90ad2-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="90ad2-109">Required.</span></span> <span data-ttu-id="90ad2-110">Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="90ad2-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="90ad2-111">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="90ad2-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90ad2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90ad2-112">Remarks</span></span>  
 <span data-ttu-id="90ad2-113">İçeri aktardığınız dosya (ler) bütünleştirilmiş kod meta verisi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="90ad2-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="90ad2-114">Yalnızca ortak türler derleme dışında görünür.</span><span class="sxs-lookup"><span data-stu-id="90ad2-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="90ad2-115">[-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçeneği bir modülden meta verileri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="90ad2-115">The [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="90ad2-116">Kendisi başka bir derlemeye (derleme B) başvuran bir derlemeye (derleme A) başvuruyorsa, şu durumlarda derleme B 'ye başvurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="90ad2-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="90ad2-117">Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="90ad2-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="90ad2-118">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="90ad2-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="90ad2-119">Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="90ad2-119">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="90ad2-120">Derleyicinin bir derlemede (modül değil) bir türü tanıması için, türün çözümlenmesinin zorunlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="90ad2-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="90ad2-121">Bunu nasıl yapabileceğiniz bir örnek, türün bir örneğini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="90ad2-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="90ad2-122">Derleyici için bir derlemede tür adlarını çözümlemek için diğer yollar mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="90ad2-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="90ad2-123">Örneğin, derlemedeki bir türden devralma yaparsanız, tür adı derleyici tarafından bilinmiş olur.</span><span class="sxs-lookup"><span data-stu-id="90ad2-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="90ad2-124">Yaygın olarak kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyası varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="90ad2-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="90ad2-125">Derleyicinin Vbc. rsp kullanmasını istemiyorsanız, `-noconfig` kullanın.</span><span class="sxs-lookup"><span data-stu-id="90ad2-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="90ad2-126">@No__t_0 kısa biçimi `/r`.</span><span class="sxs-lookup"><span data-stu-id="90ad2-126">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90ad2-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="90ad2-127">Example</span></span>  
 <span data-ttu-id="90ad2-128">Aşağıdaki komut, `Metad1.dll` ve `Metad2.dll` ' den `Out.exe` üretmek için kaynak dosyayı `Input.vb` ve başvuru derlemelerini derler.</span><span class="sxs-lookup"><span data-stu-id="90ad2-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="90ad2-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90ad2-129">See also</span></span>

- [<span data-ttu-id="90ad2-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="90ad2-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="90ad2-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="90ad2-131">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="90ad2-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90ad2-132">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="90ad2-133">Public</span><span class="sxs-lookup"><span data-stu-id="90ad2-133">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="90ad2-134">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="90ad2-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
description: Hakkında daha fazla bilgi edinin:-Reference (Visual Basic)
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: e84cdf447294a299c26a775327528a94ebba03da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474154"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="3946a-103">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3946a-103">-reference (Visual Basic)</span></span>

<span data-ttu-id="3946a-104">Derleyicinin, belirtilen derlemelerde bulunan tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="3946a-104">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3946a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3946a-105">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="3946a-106">veya</span><span class="sxs-lookup"><span data-stu-id="3946a-106">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="3946a-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="3946a-107">Arguments</span></span>  
  
|<span data-ttu-id="3946a-108">Terim</span><span class="sxs-lookup"><span data-stu-id="3946a-108">Term</span></span>|<span data-ttu-id="3946a-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="3946a-109">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="3946a-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3946a-110">Required.</span></span> <span data-ttu-id="3946a-111">Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="3946a-111">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="3946a-112">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="3946a-112">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3946a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3946a-113">Remarks</span></span>  

 <span data-ttu-id="3946a-114">İçeri aktardığınız dosya (ler) bütünleştirilmiş kod meta verisi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3946a-114">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="3946a-115">Yalnızca ortak türler derleme dışında görünür.</span><span class="sxs-lookup"><span data-stu-id="3946a-115">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="3946a-116">[-Addmodule](addmodule.md) seçeneği bir modülden meta verileri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="3946a-116">The [-addmodule](addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="3946a-117">Kendisi başka bir derlemeye (derleme B) başvuran bir derlemeye (derleme A) başvuruyorsa, şu durumlarda derleme B 'ye başvurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="3946a-117">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="3946a-118">Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="3946a-118">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="3946a-119">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3946a-119">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="3946a-120">Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](libpath.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3946a-120">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="3946a-121">Derleyicinin bir derlemede (modül değil) bir türü tanıması için, türün çözümlenmesinin zorunlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3946a-121">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="3946a-122">Bunu nasıl yapabileceğiniz bir örnek, türün bir örneğini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="3946a-122">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="3946a-123">Derleyici için bir derlemede tür adlarını çözümlemek için diğer yollar mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3946a-123">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="3946a-124">Örneğin, derlemedeki bir türden devralma yaparsanız, tür adı derleyici tarafından bilinmiş olur.</span><span class="sxs-lookup"><span data-stu-id="3946a-124">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="3946a-125">Yaygın olarak kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyası varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3946a-125">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="3946a-126">`-noconfig`Derleyicinin Vbc. rsp kullanmasını istemiyorsanız kullanın.</span><span class="sxs-lookup"><span data-stu-id="3946a-126">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="3946a-127">Öğesinin kısa biçimi `-reference` `-r` .</span><span class="sxs-lookup"><span data-stu-id="3946a-127">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3946a-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3946a-128">Example</span></span>  

 <span data-ttu-id="3946a-129">Aşağıdaki komut, kaynak dosya `Input.vb` ve başvuru derlemelerini ' den `Metad1.dll` ve `Metad2.dll` üretilecek şekilde derler `Out.exe` .</span><span class="sxs-lookup"><span data-stu-id="3946a-129">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3946a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3946a-130">See also</span></span>

- [<span data-ttu-id="3946a-131">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3946a-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3946a-132">-noconfig</span><span class="sxs-lookup"><span data-stu-id="3946a-132">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="3946a-133">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3946a-133">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="3946a-134">Genel</span><span class="sxs-lookup"><span data-stu-id="3946a-134">Public</span></span>](../../language-reference/modifiers/public.md)
- [<span data-ttu-id="3946a-135">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3946a-135">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

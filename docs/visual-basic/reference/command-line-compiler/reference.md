---
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
ms.openlocfilehash: b489a164e56a5e3bdbf7e3cdf24ec330fadedf38
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097559"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="5b458-102">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b458-102">-reference (Visual Basic)</span></span>

<span data-ttu-id="5b458-103">Derleyicinin, belirtilen derlemelerde bulunan tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5b458-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b458-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b458-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="5b458-105">veya</span><span class="sxs-lookup"><span data-stu-id="5b458-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="5b458-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="5b458-106">Arguments</span></span>  
  
|<span data-ttu-id="5b458-107">Terim</span><span class="sxs-lookup"><span data-stu-id="5b458-107">Term</span></span>|<span data-ttu-id="5b458-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="5b458-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="5b458-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5b458-109">Required.</span></span> <span data-ttu-id="5b458-110">Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="5b458-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="5b458-111">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="5b458-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b458-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b458-112">Remarks</span></span>  

 <span data-ttu-id="5b458-113">İçeri aktardığınız dosya (ler) bütünleştirilmiş kod meta verisi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5b458-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="5b458-114">Yalnızca ortak türler derleme dışında görünür.</span><span class="sxs-lookup"><span data-stu-id="5b458-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="5b458-115">[-Addmodule](addmodule.md) seçeneği bir modülden meta verileri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="5b458-115">The [-addmodule](addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="5b458-116">Kendisi başka bir derlemeye (derleme B) başvuran bir derlemeye (derleme A) başvuruyorsa, şu durumlarda derleme B 'ye başvurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="5b458-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="5b458-117">Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="5b458-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="5b458-118">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5b458-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="5b458-119">Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](libpath.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b458-119">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="5b458-120">Derleyicinin bir derlemede (modül değil) bir türü tanıması için, türün çözümlenmesinin zorunlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b458-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="5b458-121">Bunu nasıl yapabileceğiniz bir örnek, türün bir örneğini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5b458-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="5b458-122">Derleyici için bir derlemede tür adlarını çözümlemek için diğer yollar mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5b458-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="5b458-123">Örneğin, derlemedeki bir türden devralma yaparsanız, tür adı derleyici tarafından bilinmiş olur.</span><span class="sxs-lookup"><span data-stu-id="5b458-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="5b458-124">Yaygın olarak kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyası varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b458-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="5b458-125">`-noconfig`Derleyicinin Vbc. rsp kullanmasını istemiyorsanız kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b458-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="5b458-126">Öğesinin kısa biçimi `-reference` `-r` .</span><span class="sxs-lookup"><span data-stu-id="5b458-126">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b458-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b458-127">Example</span></span>  

 <span data-ttu-id="5b458-128">Aşağıdaki komut, kaynak dosya `Input.vb` ve başvuru derlemelerini ' den `Metad1.dll` ve `Metad2.dll` üretilecek şekilde derler `Out.exe` .</span><span class="sxs-lookup"><span data-stu-id="5b458-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b458-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b458-129">See also</span></span>

- [<span data-ttu-id="5b458-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="5b458-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5b458-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="5b458-131">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="5b458-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b458-132">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="5b458-133">Geneldir</span><span class="sxs-lookup"><span data-stu-id="5b458-133">Public</span></span>](../../language-reference/modifiers/public.md)
- [<span data-ttu-id="5b458-134">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="5b458-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

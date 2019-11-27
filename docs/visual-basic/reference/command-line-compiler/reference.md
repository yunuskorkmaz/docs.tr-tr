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
ms.openlocfilehash: 8b57affa05c77d8ed20bfead7de767a8dd994241
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348593"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="af949-102">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af949-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="af949-103">Derleyicinin, belirtilen derlemelerde bulunan tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="af949-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af949-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af949-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="af949-105">veya</span><span class="sxs-lookup"><span data-stu-id="af949-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="af949-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="af949-106">Arguments</span></span>  
  
|<span data-ttu-id="af949-107">Terim</span><span class="sxs-lookup"><span data-stu-id="af949-107">Term</span></span>|<span data-ttu-id="af949-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="af949-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="af949-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="af949-109">Required.</span></span> <span data-ttu-id="af949-110">Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="af949-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="af949-111">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="af949-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af949-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af949-112">Remarks</span></span>  
 <span data-ttu-id="af949-113">İçeri aktardığınız dosya (ler) bütünleştirilmiş kod meta verisi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="af949-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="af949-114">Yalnızca ortak türler derleme dışında görünür.</span><span class="sxs-lookup"><span data-stu-id="af949-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="af949-115">[-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçeneği bir modülden meta verileri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="af949-115">The [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="af949-116">Kendisi başka bir derlemeye (derleme B) başvuran bir derlemeye (derleme A) başvuruyorsa, şu durumlarda derleme B 'ye başvurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="af949-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="af949-117">Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="af949-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="af949-118">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="af949-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="af949-119">Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="af949-119">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="af949-120">Derleyicinin bir derlemede (modül değil) bir türü tanıması için, türün çözümlenmesinin zorunlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="af949-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="af949-121">Bunu nasıl yapabileceğiniz bir örnek, türün bir örneğini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="af949-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="af949-122">Derleyici için bir derlemede tür adlarını çözümlemek için diğer yollar mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="af949-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="af949-123">Örneğin, derlemedeki bir türden devralma yaparsanız, tür adı derleyici tarafından bilinmiş olur.</span><span class="sxs-lookup"><span data-stu-id="af949-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="af949-124">Yaygın olarak kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyası varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af949-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="af949-125">Derleyicinin Vbc. rsp kullanmasını istemiyorsanız `-noconfig` kullanın.</span><span class="sxs-lookup"><span data-stu-id="af949-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="af949-126">`-reference` kısa biçimi `/r`.</span><span class="sxs-lookup"><span data-stu-id="af949-126">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af949-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="af949-127">Example</span></span>  
 <span data-ttu-id="af949-128">Aşağıdaki komut, `Metad1.dll` ve `Metad2.dll` `Out.exe`oluşturmak için kaynak dosya `Input.vb` ve başvuru derlemelerini derler.</span><span class="sxs-lookup"><span data-stu-id="af949-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="af949-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af949-129">See also</span></span>

- [<span data-ttu-id="af949-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="af949-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="af949-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="af949-131">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="af949-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af949-132">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="af949-133">Public</span><span class="sxs-lookup"><span data-stu-id="af949-133">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="af949-134">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="af949-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

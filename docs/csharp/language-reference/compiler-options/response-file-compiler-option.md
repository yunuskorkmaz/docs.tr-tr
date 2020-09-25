---
description: '@ (C# Derleyici Seçenekleri)'
title: '@ (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 8f7e222e194fc4ba96159ecd792765f64b4d1c57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193769"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="76924-103">@ (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="76924-103">@ (C# Compiler Options)</span></span>

<span data-ttu-id="76924-104">@ Seçeneği, derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosya belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="76924-104">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76924-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="76924-105">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="76924-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="76924-106">Arguments</span></span>  

 `response_file`  
 <span data-ttu-id="76924-107">Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="76924-107">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76924-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76924-108">Remarks</span></span>  

 <span data-ttu-id="76924-109">Derleyici seçenekleri ve kaynak kodu dosyaları, derleyici tarafından, tıpkı komut satırında belirtildikleri gibi işlenecek şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="76924-109">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="76924-110">Bir derlemede birden fazla yanıt dosyası belirtmek için, birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="76924-110">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="76924-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="76924-111">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="76924-112">Bir yanıt dosyasında, bir satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir.</span><span class="sxs-lookup"><span data-stu-id="76924-112">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="76924-113">Tek bir derleyici seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz).</span><span class="sxs-lookup"><span data-stu-id="76924-113">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="76924-114">Yanıt dosyaları # simgesiyle başlayan açıklamalara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="76924-114">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="76924-115">Bir yanıt dosyası içinden derleyici seçeneklerinin belirtilmesi, komut satırında bu komutları verme gibidir.</span><span class="sxs-lookup"><span data-stu-id="76924-115">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="76924-116">Daha fazla bilgi için bkz. [komut satırından oluşturma](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) .</span><span class="sxs-lookup"><span data-stu-id="76924-116">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="76924-117">Derleyici komut seçeneklerini karşılaştığı şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="76924-117">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="76924-118">Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarındaki daha önce listelenen seçenekleri geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="76924-118">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="76924-119">Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="76924-119">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="76924-120">C#, csc.exe dosyası ile aynı dizinde bulunan CSC. rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="76924-120">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="76924-121">Csc. rsp hakkında daha fazla bilgi için bkz. [-noconfig](./noconfig-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="76924-121">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="76924-122">Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="76924-122">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76924-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="76924-123">Example</span></span>  

 <span data-ttu-id="76924-124">Örnek yanıt dosyasından birkaç satır aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="76924-124">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="76924-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76924-125">See also</span></span>

- [<span data-ttu-id="76924-126">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="76924-126">C# Compiler Options</span></span>](./index.md)

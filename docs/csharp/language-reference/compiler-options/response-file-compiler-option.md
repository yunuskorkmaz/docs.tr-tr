---
title: "@ (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d4dc8c81a9afd60add4c2a62be6804a0f6446124
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="-c-compiler-options"></a><span data-ttu-id="c4c5c-102">@ (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c4c5c-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="c4c5c-103">@ Derleyici seçenekleri içeren bir dosya ve derlemek için kaynak kodu dosyaları belirttiğiniz seçeneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4c5c-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c4c5c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c4c5c-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="c4c5c-106">Derleyici seçeneklerini veya kaynak kodu dosyaları derlemek için listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4c5c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4c5c-107">Remarks</span></span>  
 <span data-ttu-id="c4c5c-108">Komut satırında bunlar yalnızca belirtilmiş sanki derleyici seçenekleri ve kaynak kodu dosyaları derleyici tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="c4c5c-109">Bir derlemede birden fazla yanıt dosyası belirtmek için birden çok yanıt dosyası seçeneklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="c4c5c-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c4c5c-110">For example:</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="c4c5c-111">Bir yanıt dosyası, birden çok derleyici seçenekleri ve kaynak kodu dosyaları tek bir satırda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="c4c5c-112">Bir tek derleyici seçeneği belirtimi (birden çok satıra yayılamaz) tek bir satırda görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="c4c5c-113">Yanıt dosyaları # sembolü ile başlayan açıklamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="c4c5c-114">Derleyici seçeneklerini içinde bir yanıt dosyası belirtme komutlarda komut satırında verilmesine benzer olur.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="c4c5c-115">Bkz: [komut satırından derleme](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-115">See [Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="c4c5c-116">Karşılaşılan derleyici komut seçeneklerini işler.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="c4c5c-117">Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında önceden listelenen seçenekleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="c4c5c-118">Buna karşılık, bir yanıt dosyası seçeneklerinde komut satırında veya diğer yanıt dosyaları daha önce listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="c4c5c-119">C# csc.exe dosya ile aynı dizinde bulunan csc.rsp dosyası sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="c4c5c-120">Bkz: [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) csc.rsp hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-120">See [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="c4c5c-121">Visual Studio geliştirme ortamında bu derleyici seçeneği ayarlanamaz ya da programlı olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4c5c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4c5c-122">Example</span></span>  
 <span data-ttu-id="c4c5c-123">Örnek bir yanıt dosyası birkaç satırlarından şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c4c5c-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
/target:exe /out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4c5c-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4c5c-124">See Also</span></span>  
 [<span data-ttu-id="c4c5c-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c4c5c-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

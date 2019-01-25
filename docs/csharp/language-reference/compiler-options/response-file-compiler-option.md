---
title: '@ (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 32a06c596c44cdf28e5c1bb3422b9cf8262f2c08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738098"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="9b97d-102">@ (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="9b97d-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="9b97d-103">@ Derleyici seçenekleri içeren bir dosyayı ve kaynak kodu dosyalarını derlemek için belirttiğiniz seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b97d-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b97d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b97d-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b97d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9b97d-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="9b97d-106">Derleyici Seçenekleri veya kaynak kodu dosyalarını derlemek için listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="9b97d-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b97d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b97d-107">Remarks</span></span>  
 <span data-ttu-id="9b97d-108">Kaynak kodu dosyaları ve derleyici seçenekleri derleyici tarafından yalnızca komut satırında, belirtilmiş gibi işlenir.</span><span class="sxs-lookup"><span data-stu-id="9b97d-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="9b97d-109">Bir derlemede birden fazla yanıt dosyası belirtmek için birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="9b97d-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="9b97d-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9b97d-110">For example:</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="9b97d-111">Bir yanıt dosyası, birden çok derleme seçenekleri ve kaynak kodu dosyaları tek bir satırda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="9b97d-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="9b97d-112">Bir tek derleyici seçeneği belirtimi (çok satırlı yayılamaz) tek bir satırda yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b97d-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="9b97d-113">Yanıt dosyaları # sembolü ile başlayan açıklamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b97d-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="9b97d-114">Bir yanıt dosyası derleyici seçeneklerini belirterek bu komutlar komut satırında verilmesine benzer olur.</span><span class="sxs-lookup"><span data-stu-id="9b97d-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="9b97d-115">Bkz: [komut satırından derleme](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="9b97d-115">See [Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="9b97d-116">Karşılaşılan derleyici komut seçenekleri işler.</span><span class="sxs-lookup"><span data-stu-id="9b97d-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="9b97d-117">Bu nedenle, komut satırı bağımsız değişkenleri, yanıt dosyaları daha önce listelenen seçeneklerini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b97d-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="9b97d-118">Buna karşılık, bir yanıt dosyasında seçenekleri komut satırında veya diğer yanıt dosyaları daha önce listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9b97d-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="9b97d-119">C# csc.exe dosyasıyla aynı dizinde bulunan csc.rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b97d-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="9b97d-120">Bkz: [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) csc.rsp hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="9b97d-120">See [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="9b97d-121">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlanamaz ya da programlı olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9b97d-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b97d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b97d-122">Example</span></span>  
 <span data-ttu-id="9b97d-123">Birkaç örnek yanıt dosyasından şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9b97d-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b97d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b97d-124">See also</span></span>

- [<span data-ttu-id="9b97d-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9b97d-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

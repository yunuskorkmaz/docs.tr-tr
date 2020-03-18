---
title: '@ (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: d8e5c0ec148754c3e4cebfa32ad9f44a0bb0119e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70202915"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="c64ca-102">@ (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c64ca-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="c64ca-103">@ seçeneği derleyici seçenekleri ve derlemek için kaynak kodu dosyaları içeren bir dosya belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c64ca-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c64ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c64ca-104">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c64ca-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c64ca-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="c64ca-106">Derleyici seçeneklerini veya derlemide kaynak kod dosyalarını listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="c64ca-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c64ca-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c64ca-107">Remarks</span></span>  
 <span data-ttu-id="c64ca-108">Derleyici seçenekleri ve kaynak kod dosyaları, komut satırında belirtilmiş gibi derleyici tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="c64ca-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="c64ca-109">Derlemede birden fazla yanıt dosyası belirtmek için birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="c64ca-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="c64ca-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c64ca-110">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="c64ca-111">Yanıt dosyasında, birden çok derleyici seçeneği ve kaynak kodu dosyası tek bir satırda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c64ca-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="c64ca-112">Tek bir derleyici seçeneği belirtimi tek bir satırda görünmelidir (birden çok satıra yayılamaz).</span><span class="sxs-lookup"><span data-stu-id="c64ca-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="c64ca-113">Yanıt dosyaları # sembolü ile başlayan yorumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="c64ca-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="c64ca-114">Yanıt dosyasının içinden derleyici seçeneklerini belirtmek, komut satırında bu komutları vermek gibidir.</span><span class="sxs-lookup"><span data-stu-id="c64ca-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="c64ca-115">Daha fazla bilgi için [Komut Satırı'ndan Bina'ya](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="c64ca-115">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="c64ca-116">Derleyici, komut seçeneklerini karşılaşılan şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="c64ca-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="c64ca-117">Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="c64ca-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="c64ca-118">Tersine, yanıt dosyasındaki seçenekler komut satırında veya diğer yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c64ca-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="c64ca-119">C# csc.exe dosyası ile aynı dizinde bulunan csc.rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c64ca-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="c64ca-120">CSc.rsp hakkında daha fazla bilgi için [-noconfig](./noconfig-compiler-option.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="c64ca-120">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="c64ca-121">Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c64ca-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c64ca-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c64ca-122">Example</span></span>  
 <span data-ttu-id="c64ca-123">Örnek yanıt dosyasından birkaç satır şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c64ca-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c64ca-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c64ca-124">See also</span></span>

- [<span data-ttu-id="c64ca-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c64ca-125">C# Compiler Options</span></span>](./index.md)

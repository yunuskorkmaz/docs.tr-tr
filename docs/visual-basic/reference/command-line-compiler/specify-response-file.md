---
title: '@ (Yanıt Dosyası Belirtme) (Visual Basic)'
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af66000208dee0896792892a52dc6acdf5cb1e37
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="2a768-102">@ (Yanıt Dosyası Belirtme) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a768-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="2a768-103">Derleyici seçenekleri içeren bir dosya ve derlemek için kaynak kodu dosyaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a768-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a768-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a768-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="2a768-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2a768-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="2a768-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2a768-106">Required.</span></span> <span data-ttu-id="2a768-107">Derleyici seçeneklerini veya kaynak kodu dosyaları derlemek için listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="2a768-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="2a768-108">Dosya adını tırnak işaretleri içine alın ("") boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="2a768-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a768-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a768-109">Remarks</span></span>  
 <span data-ttu-id="2a768-110">Derleyici derleyici seçenekleri ve komut satırında belirtilmiş gibi bir yanıt dosyası içinde belirtilen kaynak kodu dosyaları işler.</span><span class="sxs-lookup"><span data-stu-id="2a768-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="2a768-111">Bir derlemede birden fazla yanıt dosyası belirtmek için aşağıdaki gibi birden çok yanıt dosyası seçeneklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="2a768-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="2a768-112">Bir yanıt dosyası, birden çok derleyici seçenekleri ve kaynak kodu dosyaları tek bir satırda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="2a768-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="2a768-113">Tek bir derleyici seçeneği belirtimi (birden çok satıra yayılamaz) tek bir satırda görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a768-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="2a768-114">Yanıt dosyaları ile başlayan açıklamaları olabilir `#` simgesi.</span><span class="sxs-lookup"><span data-stu-id="2a768-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="2a768-115">Bir veya daha fazla yanıt dosyalarında belirtilen seçeneklerle komut satırında belirtilen Seçenekleri birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a768-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="2a768-116">Bunları bulduğu gibi derleyici komut seçeneklerini işler.</span><span class="sxs-lookup"><span data-stu-id="2a768-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="2a768-117">Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında önceden listelenen seçenekleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a768-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="2a768-118">Buna karşılık, bir yanıt dosyası seçeneklerinde, komut satırında veya diğer yanıt dosyaları daha önce listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2a768-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="2a768-119">Visual Basic Vbc.exe dosya ile aynı dizinde bulunan Vbc.rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a768-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="2a768-120">Vbc.rsp dosya varsayılan olarak sürece dahil `-noconfig` seçenek kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a768-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="2a768-121">Daha fazla bilgi için bkz: [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="2a768-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a768-122">`@` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a768-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a768-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a768-123">Example</span></span>  
 <span data-ttu-id="2a768-124">Aşağıdaki satırları örnek yanıt dosyasından ' dir.</span><span class="sxs-lookup"><span data-stu-id="2a768-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="2a768-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a768-125">Example</span></span>  
 <span data-ttu-id="2a768-126">Aşağıdaki örnekte nasıl kullanılacağı ortaya `@` adlı yanıt dosyası seçeneğiyle `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="2a768-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a768-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a768-127">See Also</span></span>  
 [<span data-ttu-id="2a768-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2a768-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2a768-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="2a768-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="2a768-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2a768-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

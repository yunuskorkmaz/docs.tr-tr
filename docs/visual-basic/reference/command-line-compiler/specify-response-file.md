---
title: '@ (Yanıt Dosyası Belirtme) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: d790e66e04cc62011550e894eec4000a43783765
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494789"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="c28c4-102">@ (Yanıt Dosyası Belirtme) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c28c4-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="c28c4-103">Derleyici seçenekleri içeren bir dosyayı ve derlemek için kaynak kodu dosyaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c28c4-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c28c4-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c28c4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c28c4-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="c28c4-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c28c4-106">Required.</span></span> <span data-ttu-id="c28c4-107">Derleyici Seçenekleri veya kaynak kodu dosyalarına derlemek listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="c28c4-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="c28c4-108">Dosya adı tırnak içine alın ("") bir boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="c28c4-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c28c4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c28c4-109">Remarks</span></span>  
 <span data-ttu-id="c28c4-110">Derleyici derleyici seçenekleri ve komut satırı üzerinde belirtilmiş gibi bir yanıt dosyası içinde belirtilen kaynak kodu dosyaları işler.</span><span class="sxs-lookup"><span data-stu-id="c28c4-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="c28c4-111">Bir derlemede birden fazla yanıt dosyası belirtmek için aşağıdaki gibi birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="c28c4-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="c28c4-112">Bir yanıt dosyası, birden çok derleme seçenekleri ve kaynak kodu dosyaları tek bir satırda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c28c4-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="c28c4-113">Tek bir derleyici seçeneği belirtimi (çok satırlı yayılamaz) tek bir satırda yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c28c4-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="c28c4-114">Yanıt dosyaları ile başlayan açıklamaları olabilir `#` simgesi.</span><span class="sxs-lookup"><span data-stu-id="c28c4-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="c28c4-115">Bir veya daha fazla yanıt dosyalarında belirtilen seçeneklerle komut satırında belirtilen seçenekler birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c28c4-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="c28c4-116">Derleyici bunları komut seçenekleri işler.</span><span class="sxs-lookup"><span data-stu-id="c28c4-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="c28c4-117">Bu nedenle, komut satırı bağımsız değişkenleri, yanıt dosyaları daha önce listelenen seçeneklerini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c28c4-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="c28c4-118">Buna karşılık, bir yanıt dosyasında seçenekleri komut satırında veya diğer yanıt dosyaları daha önce listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c28c4-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="c28c4-119">Visual Basic Vbc.exe dosyasıyla aynı dizinde bulunan nezahrnovat dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c28c4-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="c28c4-120">Nezahrnovat dosya, sürece varsayılan olarak dahil edilir `-noconfig` seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c28c4-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="c28c4-121">Daha fazla bilgi için [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="c28c4-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c28c4-122">`@` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c28c4-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c28c4-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="c28c4-123">Example</span></span>  
 <span data-ttu-id="c28c4-124">Aşağıdaki satırları bir örnek yanıt dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="c28c4-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="c28c4-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="c28c4-125">Example</span></span>  
 <span data-ttu-id="c28c4-126">Aşağıdaki örnek nasıl kullanılacağını gösterir `@` adlı yanıt dosyası seçeneği `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="c28c4-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="c28c4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c28c4-127">See also</span></span>
- [<span data-ttu-id="c28c4-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="c28c4-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c28c4-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="c28c4-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="c28c4-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="c28c4-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

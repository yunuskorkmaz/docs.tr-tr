---
title: '@ (Yanıt Dosyası Belirtme) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: b84d50334e56305c27c5c0bc54578ba871a28365
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937293"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="becb9-102">@ (Yanıt Dosyası Belirtme) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="becb9-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="becb9-103">Derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="becb9-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="becb9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="becb9-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="becb9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="becb9-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="becb9-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="becb9-106">Required.</span></span> <span data-ttu-id="becb9-107">Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="becb9-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="becb9-108">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="becb9-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="becb9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="becb9-109">Remarks</span></span>  
 <span data-ttu-id="becb9-110">Derleyici, bir yanıt dosyasında belirtilen derleyici seçeneklerini ve kaynak kodu dosyalarını komut satırında belirtildikleri gibi işler.</span><span class="sxs-lookup"><span data-stu-id="becb9-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="becb9-111">Bir derlemede birden fazla yanıt dosyası belirtmek için, aşağıdaki gibi birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="becb9-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="becb9-112">Bir yanıt dosyasında, tek satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir.</span><span class="sxs-lookup"><span data-stu-id="becb9-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="becb9-113">Tek bir derleyici-seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz).</span><span class="sxs-lookup"><span data-stu-id="becb9-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="becb9-114">Yanıt dosyaları `#` sembolle başlayan açıklamalara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="becb9-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="becb9-115">Komut satırında belirtilen seçenekleri, bir veya daha fazla yanıt dosyasında belirtilen seçeneklerle birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="becb9-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="becb9-116">Derleyici, komut seçeneklerini kendileriyle karşılaştığı şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="becb9-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="becb9-117">Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="becb9-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="becb9-118">Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="becb9-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="becb9-119">Visual Basic, vbc. exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="becb9-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="becb9-120">`-noconfig` Seçenek kullanılmamışsa, vbc. rsp dosyası varsayılan olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="becb9-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="becb9-121">Daha fazla bilgi için bkz. [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="becb9-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="becb9-122">Bu `@` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="becb9-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="becb9-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="becb9-123">Example</span></span>  
 <span data-ttu-id="becb9-124">Aşağıdaki satırlar örnek bir yanıt dosyasından alınır.</span><span class="sxs-lookup"><span data-stu-id="becb9-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="becb9-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="becb9-125">Example</span></span>  
 <span data-ttu-id="becb9-126">Aşağıdaki örnek, `@` seçeneğinin adlı `File1.rsp`yanıt dosyası ile nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="becb9-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="becb9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="becb9-127">See also</span></span>

- [<span data-ttu-id="becb9-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="becb9-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="becb9-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="becb9-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="becb9-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="becb9-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

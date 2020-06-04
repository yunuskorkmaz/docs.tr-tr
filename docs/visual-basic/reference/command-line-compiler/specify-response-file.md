---
title: '@ (Yanıt Dosyasını Belirtin)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 91cf1b5a55d16ab47a83fbd259dd1d83d8e9c31a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403102"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="7d62d-102">@ (Yanıt Dosyası Belirtme) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d62d-102">@ (Specify Response File) (Visual Basic)</span></span>

<span data-ttu-id="7d62d-103">Derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d62d-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d62d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7d62d-104">Syntax</span></span>

```console
@response_file
```

## <a name="arguments"></a><span data-ttu-id="7d62d-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="7d62d-105">Arguments</span></span>

`response_file`  
<span data-ttu-id="7d62d-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7d62d-106">Required.</span></span> <span data-ttu-id="7d62d-107">Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="7d62d-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="7d62d-108">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="7d62d-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>

## <a name="remarks"></a><span data-ttu-id="7d62d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d62d-109">Remarks</span></span>

<span data-ttu-id="7d62d-110">Derleyici, bir yanıt dosyasında belirtilen derleyici seçeneklerini ve kaynak kodu dosyalarını komut satırında belirtildikleri gibi işler.</span><span class="sxs-lookup"><span data-stu-id="7d62d-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>

<span data-ttu-id="7d62d-111">Bir derlemede birden fazla yanıt dosyası belirtmek için, aşağıdaki gibi birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="7d62d-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>

```console
@file1.rsp @file2.rsp
```

<span data-ttu-id="7d62d-112">Bir yanıt dosyasında, tek satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir.</span><span class="sxs-lookup"><span data-stu-id="7d62d-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="7d62d-113">Tek bir derleyici-seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz).</span><span class="sxs-lookup"><span data-stu-id="7d62d-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="7d62d-114">Yanıt dosyaları sembolle başlayan açıklamalara sahip olabilir `#` .</span><span class="sxs-lookup"><span data-stu-id="7d62d-114">Response files can have comments that begin with the `#` symbol.</span></span>

<span data-ttu-id="7d62d-115">Komut satırında belirtilen seçenekleri, bir veya daha fazla yanıt dosyasında belirtilen seçeneklerle birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d62d-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="7d62d-116">Derleyici, komut seçeneklerini kendileriyle karşılaştığı şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="7d62d-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="7d62d-117">Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d62d-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="7d62d-118">Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7d62d-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>

<span data-ttu-id="7d62d-119">Visual Basic, vbc. exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d62d-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="7d62d-120">Seçenek kullanılmamışsa, vbc. rsp dosyası varsayılan olarak dahil edilir `-noconfig` .</span><span class="sxs-lookup"><span data-stu-id="7d62d-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="7d62d-121">Daha fazla bilgi için bkz. [-noconfig](noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="7d62d-121">For more information, see [-noconfig](noconfig.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7d62d-122">`@`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d62d-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="7d62d-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d62d-123">Example</span></span>

<span data-ttu-id="7d62d-124">Aşağıdaki satırlar örnek bir yanıt dosyasından alınır.</span><span class="sxs-lookup"><span data-stu-id="7d62d-124">The following lines are from a sample response file.</span></span>

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a><span data-ttu-id="7d62d-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d62d-125">Example</span></span>

<span data-ttu-id="7d62d-126">Aşağıdaki örnek, `@` seçeneğinin adlı yanıt dosyası ile nasıl kullanılacağını gösterir `File1.rsp` .</span><span class="sxs-lookup"><span data-stu-id="7d62d-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>

```console
vbc @file1.rsp
```

## <a name="see-also"></a><span data-ttu-id="7d62d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d62d-127">See also</span></span>

- [<span data-ttu-id="7d62d-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7d62d-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7d62d-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="7d62d-129">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="7d62d-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="7d62d-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

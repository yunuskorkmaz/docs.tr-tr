---
description: 'Hakkında daha fazla bilgi edinin: @ (yanıt dosyası belirtme) (Visual Basic)'
title: '@ (Yanıt Dosyasını Belirtin)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 7a28be0d0bf6da177d9cfe85ecdb40eccf8a339f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473920"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="e45d7-103">@ (Yanıt Dosyası Belirtme) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e45d7-103">@ (Specify Response File) (Visual Basic)</span></span>

<span data-ttu-id="e45d7-104">Derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e45d7-104">Specifies a file that contains compiler options and source-code files to compile.</span></span>

## <a name="syntax"></a><span data-ttu-id="e45d7-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e45d7-105">Syntax</span></span>

```console
@response_file
```

## <a name="arguments"></a><span data-ttu-id="e45d7-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="e45d7-106">Arguments</span></span>

`response_file`  
<span data-ttu-id="e45d7-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e45d7-107">Required.</span></span> <span data-ttu-id="e45d7-108">Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="e45d7-108">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="e45d7-109">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="e45d7-109">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>

## <a name="remarks"></a><span data-ttu-id="e45d7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e45d7-110">Remarks</span></span>

<span data-ttu-id="e45d7-111">Derleyici, bir yanıt dosyasında belirtilen derleyici seçeneklerini ve kaynak kodu dosyalarını komut satırında belirtildikleri gibi işler.</span><span class="sxs-lookup"><span data-stu-id="e45d7-111">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>

<span data-ttu-id="e45d7-112">Bir derlemede birden fazla yanıt dosyası belirtmek için, aşağıdaki gibi birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="e45d7-112">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>

```console
@file1.rsp @file2.rsp
```

<span data-ttu-id="e45d7-113">Bir yanıt dosyasında, tek satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e45d7-113">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="e45d7-114">Tek bir derleyici-seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz).</span><span class="sxs-lookup"><span data-stu-id="e45d7-114">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="e45d7-115">Yanıt dosyaları sembolle başlayan açıklamalara sahip olabilir `#` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-115">Response files can have comments that begin with the `#` symbol.</span></span>

<span data-ttu-id="e45d7-116">Komut satırında belirtilen seçenekleri, bir veya daha fazla yanıt dosyasında belirtilen seçeneklerle birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e45d7-116">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="e45d7-117">Derleyici, komut seçeneklerini kendileriyle karşılaştığı şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="e45d7-117">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="e45d7-118">Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="e45d7-118">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="e45d7-119">Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e45d7-119">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>

<span data-ttu-id="e45d7-120">Visual Basic, Vbc.exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e45d7-120">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="e45d7-121">Seçenek kullanılmamışsa, vbc. rsp dosyası varsayılan olarak dahil edilir `-noconfig` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-121">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="e45d7-122">Daha fazla bilgi için bkz. [-noconfig](noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="e45d7-122">For more information, see [-noconfig](noconfig.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e45d7-123">`@`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e45d7-123">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="e45d7-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e45d7-124">Example</span></span>

<span data-ttu-id="e45d7-125">Aşağıdaki satırlar örnek bir yanıt dosyasından alınır.</span><span class="sxs-lookup"><span data-stu-id="e45d7-125">The following lines are from a sample response file.</span></span>

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a><span data-ttu-id="e45d7-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="e45d7-126">Example</span></span>

<span data-ttu-id="e45d7-127">Aşağıdaki örnek, `@` seçeneğinin adlı yanıt dosyası ile nasıl kullanılacağını gösterir `File1.rsp` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-127">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>

```console
vbc @file1.rsp
```

## <a name="see-also"></a><span data-ttu-id="e45d7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e45d7-128">See also</span></span>

- [<span data-ttu-id="e45d7-129">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e45d7-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="e45d7-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="e45d7-130">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="e45d7-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="e45d7-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

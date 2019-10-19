---
title: '@ (Yanıt Dosyası Belirtme) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 60206b6e42d329776948e8a0ef3c2e8e7e7d58bc
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583308"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="78560-102">@ (Yanıt Dosyası Belirtme) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78560-102">@ (Specify Response File) (Visual Basic)</span></span>

<span data-ttu-id="78560-103">Derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="78560-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>

## <a name="syntax"></a><span data-ttu-id="78560-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78560-104">Syntax</span></span>

```console
@response_file
```

## <a name="arguments"></a><span data-ttu-id="78560-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="78560-105">Arguments</span></span>

`response_file`  
<span data-ttu-id="78560-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="78560-106">Required.</span></span> <span data-ttu-id="78560-107">Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="78560-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="78560-108">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="78560-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>

## <a name="remarks"></a><span data-ttu-id="78560-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78560-109">Remarks</span></span>

<span data-ttu-id="78560-110">Derleyici, bir yanıt dosyasında belirtilen derleyici seçeneklerini ve kaynak kodu dosyalarını komut satırında belirtildikleri gibi işler.</span><span class="sxs-lookup"><span data-stu-id="78560-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>

<span data-ttu-id="78560-111">Bir derlemede birden fazla yanıt dosyası belirtmek için, aşağıdaki gibi birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="78560-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>

```console
@file1.rsp @file2.rsp
```

<span data-ttu-id="78560-112">Bir yanıt dosyasında, tek satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir.</span><span class="sxs-lookup"><span data-stu-id="78560-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="78560-113">Tek bir derleyici-seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz).</span><span class="sxs-lookup"><span data-stu-id="78560-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="78560-114">Yanıt dosyaları `#` simgesiyle başlayan açıklamalara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="78560-114">Response files can have comments that begin with the `#` symbol.</span></span>

<span data-ttu-id="78560-115">Komut satırında belirtilen seçenekleri, bir veya daha fazla yanıt dosyasında belirtilen seçeneklerle birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78560-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="78560-116">Derleyici, komut seçeneklerini kendileriyle karşılaştığı şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="78560-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="78560-117">Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="78560-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="78560-118">Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="78560-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>

<span data-ttu-id="78560-119">Visual Basic, vbc. exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="78560-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="78560-120">@No__t_0 seçeneği kullanılmadığı takdirde Vbc. rsp dosyası varsayılan olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="78560-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="78560-121">Daha fazla bilgi için bkz. [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="78560-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>

> [!NOTE]
> <span data-ttu-id="78560-122">@No__t_0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78560-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="78560-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="78560-123">Example</span></span>

<span data-ttu-id="78560-124">Aşağıdaki satırlar örnek bir yanıt dosyasından alınır.</span><span class="sxs-lookup"><span data-stu-id="78560-124">The following lines are from a sample response file.</span></span>

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a><span data-ttu-id="78560-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="78560-125">Example</span></span>

<span data-ttu-id="78560-126">Aşağıdaki örnek, `@` seçeneğinin `File1.rsp` adlı yanıt dosyası ile nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78560-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>

```console
vbc @file1.rsp
```

## <a name="see-also"></a><span data-ttu-id="78560-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78560-127">See also</span></span>

- [<span data-ttu-id="78560-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="78560-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="78560-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="78560-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="78560-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="78560-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

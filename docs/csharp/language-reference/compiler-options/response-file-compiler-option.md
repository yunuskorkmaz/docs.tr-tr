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
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202915"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="43b5c-102">@ (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="43b5c-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="43b5c-103">@ Seçeneği, derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosya belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="43b5c-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43b5c-104">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="43b5c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="43b5c-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="43b5c-106">Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen bir dosya.</span><span class="sxs-lookup"><span data-stu-id="43b5c-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43b5c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43b5c-107">Remarks</span></span>  
 <span data-ttu-id="43b5c-108">Derleyici seçenekleri ve kaynak kodu dosyaları, derleyici tarafından, tıpkı komut satırında belirtildikleri gibi işlenecek şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="43b5c-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="43b5c-109">Bir derlemede birden fazla yanıt dosyası belirtmek için, birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="43b5c-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="43b5c-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="43b5c-110">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="43b5c-111">Bir yanıt dosyasında, bir satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir.</span><span class="sxs-lookup"><span data-stu-id="43b5c-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="43b5c-112">Tek bir derleyici seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz).</span><span class="sxs-lookup"><span data-stu-id="43b5c-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="43b5c-113">Yanıt dosyaları # simgesiyle başlayan açıklamalara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="43b5c-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="43b5c-114">Bir yanıt dosyası içinden derleyici seçeneklerinin belirtilmesi, komut satırında bu komutları verme gibidir.</span><span class="sxs-lookup"><span data-stu-id="43b5c-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="43b5c-115">Daha fazla bilgi için bkz. [komut satırından oluşturma](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) .</span><span class="sxs-lookup"><span data-stu-id="43b5c-115">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="43b5c-116">Derleyici komut seçeneklerini karşılaştığı şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="43b5c-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="43b5c-117">Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarındaki daha önce listelenen seçenekleri geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="43b5c-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="43b5c-118">Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="43b5c-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="43b5c-119">C#csc. exe dosyası ile aynı dizinde bulunan CSC. rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="43b5c-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="43b5c-120">Csc. rsp hakkında daha fazla bilgi için bkz. [-noconfig](./noconfig-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="43b5c-120">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="43b5c-121">Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="43b5c-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b5c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="43b5c-122">Example</span></span>  
 <span data-ttu-id="43b5c-123">Örnek yanıt dosyasından birkaç satır aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="43b5c-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="43b5c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43b5c-124">See also</span></span>

- [<span data-ttu-id="43b5c-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="43b5c-125">C# Compiler Options</span></span>](./index.md)

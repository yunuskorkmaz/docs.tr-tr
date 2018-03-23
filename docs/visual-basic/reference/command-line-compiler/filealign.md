---
title: -filealign
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26ff29f00f00d3ea5dbbd0bbf01df4d7858771d0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-filealign"></a><span data-ttu-id="315c0-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="315c0-102">-filealign</span></span>
<span data-ttu-id="315c0-103">Çıkış dosyasının bölümlerinin hizalamak konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="315c0-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="315c0-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="315c0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="315c0-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="315c0-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="315c0-106">Required.</span></span> <span data-ttu-id="315c0-107">Çıktı dosyasında bölüm hizalamasını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="315c0-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="315c0-108">Geçerli değerler 512, 1024, 2048, 4096 ve 8192 ' dir.</span><span class="sxs-lookup"><span data-stu-id="315c0-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="315c0-109">Bu değerler bayt cinsinden.</span><span class="sxs-lookup"><span data-stu-id="315c0-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="315c0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="315c0-110">Remarks</span></span>  
 <span data-ttu-id="315c0-111">Kullanabileceğiniz `-filealign` seçeneği çıkış dosyanızın bölüm hizalamasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="315c0-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="315c0-112">Kod veya veri içeren bir taşınabilir yürütülebilir (PE) dosyasında bitişik bellek bloklarını bölümleridir.</span><span class="sxs-lookup"><span data-stu-id="315c0-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="315c0-113">`-filealign` Seçeneği standart olmayan bir hizalama uygulamanızla derleme olanak tanır; bu seçeneği kullanmak çoğu Geliştirici gerekmez.</span><span class="sxs-lookup"><span data-stu-id="315c0-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="315c0-114">Her bölümü olan bir sınır ile hizalanır `-filealign` değeri.</span><span class="sxs-lookup"><span data-stu-id="315c0-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="315c0-115">Sabit varsayılan yok.</span><span class="sxs-lookup"><span data-stu-id="315c0-115">There is no fixed default.</span></span> <span data-ttu-id="315c0-116">Varsa `-filealign` belirtilmezse, derleyici varsayılan derleme zamanında seçer.</span><span class="sxs-lookup"><span data-stu-id="315c0-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="315c0-117">Bölüm boyutunu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="315c0-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="315c0-118">Bölüm boyutunu değiştirme küçük cihazlarda çalışan programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="315c0-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="315c0-119">`-filealign` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="315c0-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315c0-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="315c0-120">See Also</span></span>  
 [<span data-ttu-id="315c0-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="315c0-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

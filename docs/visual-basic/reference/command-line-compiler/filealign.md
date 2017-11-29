---
title: /filealign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbabc19c85501b97ef5443a6f6e12524f8de7d91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="filealign"></a><span data-ttu-id="ffe80-102">/filealign</span><span class="sxs-lookup"><span data-stu-id="ffe80-102">/filealign</span></span>
<span data-ttu-id="ffe80-103">Çıkış dosyasının bölümlerinin hizalamak konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffe80-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe80-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffe80-104">Syntax</span></span>  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="ffe80-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ffe80-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="ffe80-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ffe80-106">Required.</span></span> <span data-ttu-id="ffe80-107">Çıktı dosyasında bölüm hizalamasını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ffe80-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="ffe80-108">Geçerli değerler 512, 1024, 2048, 4096 ve 8192 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ffe80-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="ffe80-109">Bu değerler bayt cinsinden.</span><span class="sxs-lookup"><span data-stu-id="ffe80-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffe80-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffe80-110">Remarks</span></span>  
 <span data-ttu-id="ffe80-111">Kullanabileceğiniz `/filealign` seçeneği çıkış dosyanızın bölüm hizalamasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ffe80-111">You can use the `/filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="ffe80-112">Kod veya veri içeren bir taşınabilir yürütülebilir (PE) dosyasında bitişik bellek bloklarını bölümleridir.</span><span class="sxs-lookup"><span data-stu-id="ffe80-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="ffe80-113">`/filealign` Seçeneği standart olmayan bir hizalama uygulamanızla derleme olanak tanır; bu seçeneği kullanmak çoğu Geliştirici gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ffe80-113">The `/filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="ffe80-114">Her bölümü olan bir sınır ile hizalanır `/filealign` değeri.</span><span class="sxs-lookup"><span data-stu-id="ffe80-114">Each section is aligned on a boundary that is a multiple of the `/filealign` value.</span></span> <span data-ttu-id="ffe80-115">Sabit varsayılan yok.</span><span class="sxs-lookup"><span data-stu-id="ffe80-115">There is no fixed default.</span></span> <span data-ttu-id="ffe80-116">Varsa `/filealign` belirtilmezse, derleyici varsayılan derleme zamanında seçer.</span><span class="sxs-lookup"><span data-stu-id="ffe80-116">If `/filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="ffe80-117">Bölüm boyutunu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffe80-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="ffe80-118">Bölüm boyutunu değiştirme küçük cihazlarda çalışan programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ffe80-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffe80-119">`/filealign` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ffe80-119">The `/filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe80-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffe80-120">See Also</span></span>  
 [<span data-ttu-id="ffe80-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ffe80-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

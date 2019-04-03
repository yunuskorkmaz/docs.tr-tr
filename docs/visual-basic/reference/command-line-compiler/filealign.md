---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 9a844515a4596064937762ac05b850463f1b5e14
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819183"
---
# <a name="-filealign"></a><span data-ttu-id="a83d8-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="a83d8-102">-filealign</span></span>
<span data-ttu-id="a83d8-103">Çıktı dosyasının bölümlerinin hizalanacağı yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a83d8-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a83d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a83d8-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="a83d8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a83d8-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="a83d8-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a83d8-106">Required.</span></span> <span data-ttu-id="a83d8-107">Çıkış dosyasında bölüm hizalamasını belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="a83d8-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="a83d8-108">Geçerli değerler, 512, 1024, 2048, 4096 ve 8192:.</span><span class="sxs-lookup"><span data-stu-id="a83d8-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="a83d8-109">Bu değerler bayt.</span><span class="sxs-lookup"><span data-stu-id="a83d8-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a83d8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a83d8-110">Remarks</span></span>  
 <span data-ttu-id="a83d8-111">Kullanabileceğiniz `-filealign` seçeneği, çıkış dosyasında bölüm hizalamasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a83d8-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="a83d8-112">Kod veya veri içeren taşınabilir yürütülebilir (PE) dosyası bitişik bellek blokları bölümleridir.</span><span class="sxs-lookup"><span data-stu-id="a83d8-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="a83d8-113">`-filealign` Seçeneği ile standart olmayan bir hizalama uygulamanızı derleyin olanak sağlar; geliştiricilerin çoğu, bu seçeneği kullanmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a83d8-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="a83d8-114">Her bölümde katları olan bir sınır üzerinde hizalanır `-filealign` değeri.</span><span class="sxs-lookup"><span data-stu-id="a83d8-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="a83d8-115">Sabit varsayılan yok.</span><span class="sxs-lookup"><span data-stu-id="a83d8-115">There is no fixed default.</span></span> <span data-ttu-id="a83d8-116">Varsa `-filealign` belirtilmezse, derleyici derleme zamanında bir varsayılan seçer.</span><span class="sxs-lookup"><span data-stu-id="a83d8-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="a83d8-117">Bölüm boyutu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a83d8-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="a83d8-118">Bölüm boyutu değiştirme daha küçük cihazlarda çalıştırılacak programları için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a83d8-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a83d8-119">`-filealign` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a83d8-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a83d8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a83d8-120">See also</span></span>

- [<span data-ttu-id="a83d8-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a83d8-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

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
ms.openlocfilehash: db70749f28592ae6711b6d9544f8704af9416490
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181728"
---
# <a name="-filealign"></a><span data-ttu-id="3b72c-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="3b72c-102">-filealign</span></span>
<span data-ttu-id="3b72c-103">Çıktı dosyasının bölümlerinin hizalanacağı yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b72c-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b72c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b72c-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="3b72c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3b72c-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="3b72c-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3b72c-106">Required.</span></span> <span data-ttu-id="3b72c-107">Çıkış dosyasında bölüm hizalamasını belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="3b72c-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="3b72c-108">Geçerli değerler, 512, 1024, 2048, 4096 ve 8192:.</span><span class="sxs-lookup"><span data-stu-id="3b72c-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="3b72c-109">Bu değerler bayt.</span><span class="sxs-lookup"><span data-stu-id="3b72c-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b72c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b72c-110">Remarks</span></span>  
 <span data-ttu-id="3b72c-111">Kullanabileceğiniz `-filealign` seçeneği, çıkış dosyasında bölüm hizalamasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="3b72c-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="3b72c-112">Kod veya veri içeren taşınabilir yürütülebilir (PE) dosyası bitişik bellek blokları bölümleridir.</span><span class="sxs-lookup"><span data-stu-id="3b72c-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="3b72c-113">`-filealign` Seçeneği ile standart olmayan bir hizalama uygulamanızı derleyin olanak sağlar; geliştiricilerin çoğu, bu seçeneği kullanmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3b72c-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="3b72c-114">Her bölümde katları olan bir sınır üzerinde hizalanır `-filealign` değeri.</span><span class="sxs-lookup"><span data-stu-id="3b72c-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="3b72c-115">Sabit varsayılan yok.</span><span class="sxs-lookup"><span data-stu-id="3b72c-115">There is no fixed default.</span></span> <span data-ttu-id="3b72c-116">Varsa `-filealign` belirtilmezse, derleyici derleme zamanında bir varsayılan seçer.</span><span class="sxs-lookup"><span data-stu-id="3b72c-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="3b72c-117">Bölüm boyutu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b72c-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="3b72c-118">Bölüm boyutu değiştirme daha küçük cihazlarda çalıştırılacak programları için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b72c-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b72c-119">`-filealign` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b72c-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b72c-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b72c-120">See Also</span></span>  
 [<span data-ttu-id="3b72c-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3b72c-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

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
ms.openlocfilehash: fef2652f591e713140c651a9cb0df1ea9e6236c8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005590"
---
# <a name="-filealign"></a><span data-ttu-id="fe4c0-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="fe4c0-102">-filealign</span></span>
<span data-ttu-id="fe4c0-103">Çıktı dosyasının bölümlerinin hangi noktada hizalanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe4c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe4c0-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="fe4c0-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="fe4c0-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="fe4c0-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-106">Required.</span></span> <span data-ttu-id="fe4c0-107">Çıkış dosyasındaki bölümlerin hizalamasını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="fe4c0-108">Geçerli değerler 512, 1024, 2048, 4096 ve 8192.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="fe4c0-109">Bu değerler baytlardır.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe4c0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe4c0-110">Remarks</span></span>  
 <span data-ttu-id="fe4c0-111">Çıkış dosyanızdaki bölümlerin hizalamasını `-filealign` belirtmek için seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="fe4c0-112">Bölümler, bir Taşınabilir çalıştırılabilir (PE) dosyasında kod veya veri içeren bitişik bellek bloklarıdır.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="fe4c0-113">`-filealign` Seçeneği uygulamanızı standart olmayan hizalamayla derlemenize olanak sağlar; çoğu geliştiricilerin bu seçeneği kullanması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="fe4c0-114">Her bölüm, `-filealign` değerin katı olan bir sınır üzerine hizalanır.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="fe4c0-115">Sabit bir varsayılan yoktur.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-115">There is no fixed default.</span></span> <span data-ttu-id="fe4c0-116">`-filealign` Belirtilmemişse, derleyici derleme zamanında bir varsayılan değer seçer.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="fe4c0-117">Bölüm boyutunu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="fe4c0-118">Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe4c0-119">Bu `-filealign` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4c0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe4c0-120">See also</span></span>

- [<span data-ttu-id="fe4c0-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="fe4c0-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

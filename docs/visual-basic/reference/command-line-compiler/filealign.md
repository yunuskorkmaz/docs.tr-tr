---
description: Daha fazla bilgi edinin:-filealign
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
ms.openlocfilehash: f32ae370c0ef832b501f085351eadb9b6156c730
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470297"
---
# <a name="-filealign"></a><span data-ttu-id="08b18-103">-filealign</span><span class="sxs-lookup"><span data-stu-id="08b18-103">-filealign</span></span>

<span data-ttu-id="08b18-104">Çıktı dosyasının bölümlerinin hangi noktada hizalanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="08b18-104">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b18-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="08b18-105">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="08b18-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="08b18-106">Arguments</span></span>  

 `number`  
 <span data-ttu-id="08b18-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="08b18-107">Required.</span></span> <span data-ttu-id="08b18-108">Çıkış dosyasındaki bölümlerin hizalamasını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="08b18-108">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="08b18-109">Geçerli değerler 512, 1024, 2048, 4096 ve 8192.</span><span class="sxs-lookup"><span data-stu-id="08b18-109">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="08b18-110">Bu değerler baytlardır.</span><span class="sxs-lookup"><span data-stu-id="08b18-110">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08b18-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08b18-111">Remarks</span></span>  

 <span data-ttu-id="08b18-112">`-filealign`Çıkış dosyanızdaki bölümlerin hizalamasını belirtmek için seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08b18-112">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="08b18-113">Bölümler, bir Taşınabilir çalıştırılabilir (PE) dosyasında kod veya veri içeren bitişik bellek bloklarıdır.</span><span class="sxs-lookup"><span data-stu-id="08b18-113">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="08b18-114">`-filealign`Seçeneği uygulamanızı standart olmayan hizalamayla derlemenize olanak tanır; çoğu geliştirici bu seçeneği kullanmak zorunda kalmaz.</span><span class="sxs-lookup"><span data-stu-id="08b18-114">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="08b18-115">Her bölüm, değerin katı olan bir sınır üzerine hizalanır `-filealign` .</span><span class="sxs-lookup"><span data-stu-id="08b18-115">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="08b18-116">Sabit bir varsayılan yoktur.</span><span class="sxs-lookup"><span data-stu-id="08b18-116">There is no fixed default.</span></span> <span data-ttu-id="08b18-117">`-filealign`Belirtilmemişse, derleyici derleme zamanında bir varsayılan değer seçer.</span><span class="sxs-lookup"><span data-stu-id="08b18-117">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="08b18-118">Bölüm boyutunu belirterek, çıkış dosyasının boyutunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08b18-118">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="08b18-119">Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="08b18-119">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08b18-120">`-filealign`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08b18-120">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b18-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08b18-121">See also</span></span>

- [<span data-ttu-id="08b18-122">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="08b18-122">Visual Basic Command-Line Compiler</span></span>](index.md)

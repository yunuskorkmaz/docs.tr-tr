---
title: Çok fazla sayıda dosya
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: cd168ce86569d2d7558e21a5b4cc5ef385b28313
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873549"
---
# <a name="too-many-files"></a><span data-ttu-id="7d481-102">Çok fazla sayıda dosya</span><span class="sxs-lookup"><span data-stu-id="7d481-102">Too many files</span></span>

<span data-ttu-id="7d481-103">Kök dizinde işletim sisteminin izin verdiğinden daha fazla dosya oluşturuldu veya CONFIG.SYS dosyanızda **Files =** Setting içinde belirtilen sayıdan daha fazla dosya açıldı.</span><span class="sxs-lookup"><span data-stu-id="7d481-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7d481-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7d481-104">To correct this error</span></span>  
  
1. <span data-ttu-id="7d481-105">Programınız kök dizindeki dosyaları açıyor, kapatıyor veya kaydediyor ise, programınızı bir alt dizin kullanacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7d481-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="7d481-106">CONFIG.SYS dosyanızda **Files =** Setting dosyasında belirtilen dosya sayısını artırın ve bilgisayarınızı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="7d481-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d481-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d481-107">See also</span></span>

- [<span data-ttu-id="7d481-108">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="7d481-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)

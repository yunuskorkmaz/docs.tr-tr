---
title: Çok fazla sayıda dosya
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 38d39ad20f350137d714ae5d09db5d2204b83621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362806"
---
# <a name="too-many-files"></a><span data-ttu-id="5b808-102">Çok fazla sayıda dosya</span><span class="sxs-lookup"><span data-stu-id="5b808-102">Too many files</span></span>
<span data-ttu-id="5b808-103">Kök dizinde, işletim sisteminin izin verdiğinden daha fazla dosya oluşturuldu veya CONFIG 'inizdeki **dosyalar =** ayarında belirtilen sayıdan daha fazla dosya açıldı. SYS dosyası.</span><span class="sxs-lookup"><span data-stu-id="5b808-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5b808-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5b808-104">To correct this error</span></span>  
  
1. <span data-ttu-id="5b808-105">Programınız kök dizindeki dosyaları açıyor, kapatıyor veya kaydediyor ise, programınızı bir alt dizin kullanacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5b808-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="5b808-106">CONFIG 'inizdeki **Files =** ayarında belirtilen dosya sayısını artırın. SYS dosyası ve bilgisayarınızı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="5b808-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b808-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b808-107">See also</span></span>

- [<span data-ttu-id="5b808-108">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="5b808-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)

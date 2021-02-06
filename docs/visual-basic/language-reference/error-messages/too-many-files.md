---
description: 'Daha fazla bilgi edinin: çok fazla dosya'
title: Çok fazla sayıda dosya
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 85d246c49f765cf618bf889d75dcc9c10b780280
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641232"
---
# <a name="too-many-files"></a><span data-ttu-id="c27f1-103">Çok fazla sayıda dosya</span><span class="sxs-lookup"><span data-stu-id="c27f1-103">Too many files</span></span>

<span data-ttu-id="c27f1-104">Kök dizinde işletim sisteminin izin verdiğinden daha fazla dosya oluşturuldu veya CONFIG.SYS dosyanızda **Files =** Setting içinde belirtilen sayıdan daha fazla dosya açıldı.</span><span class="sxs-lookup"><span data-stu-id="c27f1-104">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c27f1-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c27f1-105">To correct this error</span></span>  
  
1. <span data-ttu-id="c27f1-106">Programınız kök dizindeki dosyaları açıyor, kapatıyor veya kaydediyor ise, programınızı bir alt dizin kullanacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c27f1-106">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="c27f1-107">CONFIG.SYS dosyanızda **Files =** Setting dosyasında belirtilen dosya sayısını artırın ve bilgisayarınızı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="c27f1-107">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c27f1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c27f1-108">See also</span></span>

- [<span data-ttu-id="c27f1-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="c27f1-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)

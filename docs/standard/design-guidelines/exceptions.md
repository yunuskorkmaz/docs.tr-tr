---
title: Özel Durumlar için Tasarım Yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: b64b6052aeb99c6e878c1a9aac50e67bca7f8d2a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709380"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="4e6fe-102">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4e6fe-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="4e6fe-103">Özel durum işlemede, return-Value tabanlı hata raporlama üzerinde birçok avantaj bulunur.</span><span class="sxs-lookup"><span data-stu-id="4e6fe-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="4e6fe-104">İyi çerçeve tasarımı, uygulama geliştiricisinin özel durumların avantajlarını belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4e6fe-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="4e6fe-105">Bu bölümde özel durumların avantajları ele alınmaktadır ve bunları etkili bir şekilde kullanmaya yönelik yönergeler sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4e6fe-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e6fe-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4e6fe-106">In This Section</span></span>  
 [<span data-ttu-id="4e6fe-107">Özel Durum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e6fe-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="4e6fe-108">Standart Özel Durum Türlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="4e6fe-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="4e6fe-109">Özel Durumlar ve Performans</span><span class="sxs-lookup"><span data-stu-id="4e6fe-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="4e6fe-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="4e6fe-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4e6fe-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="4e6fe-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e6fe-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e6fe-112">See also</span></span>

- [<span data-ttu-id="4e6fe-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4e6fe-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

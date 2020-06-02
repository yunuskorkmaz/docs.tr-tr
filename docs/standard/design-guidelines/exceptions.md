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
ms.openlocfilehash: d7580d4d3953b279824bba76b44c4134a7293b7a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289778"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="aa811-102">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="aa811-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="aa811-103">Özel durum işlemede, return-Value tabanlı hata raporlama üzerinde birçok avantaj bulunur.</span><span class="sxs-lookup"><span data-stu-id="aa811-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="aa811-104">İyi çerçeve tasarımı, uygulama geliştiricisinin özel durumların avantajlarını belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="aa811-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="aa811-105">Bu bölümde özel durumların avantajları ele alınmaktadır ve bunları etkili bir şekilde kullanmaya yönelik yönergeler sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa811-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa811-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="aa811-106">In This Section</span></span>  
 [<span data-ttu-id="aa811-107">Özel durum atma</span><span class="sxs-lookup"><span data-stu-id="aa811-107">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="aa811-108">Standart Özel Durum Türlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="aa811-108">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="aa811-109">Özel durumlar ve performans</span><span class="sxs-lookup"><span data-stu-id="aa811-109">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="aa811-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="aa811-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="aa811-111">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="aa811-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa811-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa811-112">See also</span></span>

- [<span data-ttu-id="aa811-113">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="aa811-113">Framework Design Guidelines</span></span>](index.md)

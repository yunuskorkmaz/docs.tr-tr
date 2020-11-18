---
title: Özel Durumlar için Tasarım Yönergeleri
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: 776e559bb1629245c275cb4463531a8dd4b230ae
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821157"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="77304-102">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="77304-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="77304-103">Özel durum işlemede, return-Value tabanlı hata raporlama üzerinde birçok avantaj bulunur.</span><span class="sxs-lookup"><span data-stu-id="77304-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="77304-104">İyi çerçeve tasarımı, uygulama geliştiricisinin özel durumların avantajlarını belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="77304-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="77304-105">Bu bölümde özel durumların avantajları ele alınmaktadır ve bunları etkili bir şekilde kullanmaya yönelik yönergeler sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77304-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77304-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="77304-106">In This Section</span></span>  
 [<span data-ttu-id="77304-107">Özel durum atma</span><span class="sxs-lookup"><span data-stu-id="77304-107">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="77304-108">Standart Özel Durum Türlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="77304-108">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="77304-109">Özel durumlar ve performans</span><span class="sxs-lookup"><span data-stu-id="77304-109">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="77304-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="77304-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="77304-111">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="77304-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77304-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77304-112">See also</span></span>

- [<span data-ttu-id="77304-113">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="77304-113">Framework Design Guidelines</span></span>](index.md)

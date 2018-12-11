---
title: Özel durumlar için tasarım yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
author: KrzysztofCwalina
ms.openlocfilehash: 60c3d25138c224f5eabf44d06b6c9a8373eb5f96
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153207"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="fe92a-102">Özel durumlar için tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fe92a-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="fe92a-103">Özel durum işleme dönüş değerine göre hata bildirimi üzerinden birçok avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="fe92a-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="fe92a-104">İyi çerçevesi tasarımı, uygulama geliştiricisinin özel durumları avantajlarını daha iyi anlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="fe92a-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="fe92a-105">Bu bölümde, özel durumların avantajlar açıklanır ve verimli bir şekilde kullanmak için yönergeler sunar.</span><span class="sxs-lookup"><span data-stu-id="fe92a-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe92a-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fe92a-106">In This Section</span></span>  
 [<span data-ttu-id="fe92a-107">Özel Durum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe92a-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="fe92a-108">Standart Özel Durum Türlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="fe92a-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="fe92a-109">Özel Durumlar ve Performans</span><span class="sxs-lookup"><span data-stu-id="fe92a-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="fe92a-110">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="fe92a-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fe92a-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="fe92a-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe92a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe92a-112">See also</span></span>

- [<span data-ttu-id="fe92a-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fe92a-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

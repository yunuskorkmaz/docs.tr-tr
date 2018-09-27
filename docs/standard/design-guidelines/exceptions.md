---
title: Özel durumlar için tasarım yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51cc5296a7b3f6d75b5e56d6bbc74330fa147848
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232623"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="fd794-102">Özel durumlar için tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fd794-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="fd794-103">Özel durum işleme dönüş değerine göre hata bildirimi üzerinden birçok avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="fd794-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="fd794-104">İyi çerçevesi tasarımı, uygulama geliştiricisinin özel durumları avantajlarını daha iyi anlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="fd794-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="fd794-105">Bu bölümde, özel durumların avantajlar açıklanır ve verimli bir şekilde kullanmak için yönergeler sunar.</span><span class="sxs-lookup"><span data-stu-id="fd794-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd794-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fd794-106">In This Section</span></span>  
 [<span data-ttu-id="fd794-107">Özel Durum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd794-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="fd794-108">Standart Özel Durum Türlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="fd794-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="fd794-109">Özel Durumlar ve Performans</span><span class="sxs-lookup"><span data-stu-id="fd794-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="fd794-110">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="fd794-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fd794-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="fd794-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd794-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd794-112">See also</span></span>

- [<span data-ttu-id="fd794-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fd794-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

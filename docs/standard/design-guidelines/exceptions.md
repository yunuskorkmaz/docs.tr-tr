---
title: "Özel durumlar için tasarım yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ee456632070f778d51d7fb40475a795a0f620b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="27b4a-102">Özel durumlar için tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="27b4a-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="27b4a-103">Özel durum işleme dönüş değeri temel hata bildirimi üzerinden birçok avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="27b4a-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="27b4a-104">İyi framework tasarım özel durumlar faydaları hayata geçirmek uygulama geliştiricisi yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="27b4a-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="27b4a-105">Bu bölümde özel durumlara avantajlar açıklanır ve etkili bir şekilde kullanma için yönergeler sunar.</span><span class="sxs-lookup"><span data-stu-id="27b4a-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27b4a-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="27b4a-106">In This Section</span></span>  
 [<span data-ttu-id="27b4a-107">Özel durum atma</span><span class="sxs-lookup"><span data-stu-id="27b4a-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="27b4a-108">Standart özel durum türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="27b4a-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="27b4a-109">Özel durumları ve performans</span><span class="sxs-lookup"><span data-stu-id="27b4a-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="27b4a-110">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="27b4a-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="27b4a-111">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="27b4a-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b4a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27b4a-112">See Also</span></span>  
 [<span data-ttu-id="27b4a-113">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="27b4a-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

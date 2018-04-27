---
title: Özel durumlar için tasarım yönergeleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6dcd29f96ce32f1b2602af5d844339fe33c0ed7b
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="bca95-102">Özel durumlar için tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bca95-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="bca95-103">Özel durum işleme dönüş değeri temel hata bildirimi üzerinden birçok avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="bca95-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="bca95-104">İyi framework tasarım özel durumlar faydaları hayata geçirmek uygulama geliştiricisi yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="bca95-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="bca95-105">Bu bölümde özel durumlara avantajlar açıklanır ve etkili bir şekilde kullanma için yönergeler sunar.</span><span class="sxs-lookup"><span data-stu-id="bca95-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bca95-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bca95-106">In This Section</span></span>  
 [<span data-ttu-id="bca95-107">Özel Durum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bca95-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="bca95-108">Standart Özel Durum Türlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="bca95-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="bca95-109">Özel Durumlar ve Performans</span><span class="sxs-lookup"><span data-stu-id="bca95-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="bca95-110">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="bca95-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bca95-111">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="bca95-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca95-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bca95-112">See Also</span></span>  
 [<span data-ttu-id="bca95-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="bca95-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

---
title: Ortak Tasarım Desenleri
description: '.NET içinde birkaç yaygın tasarım desenini tanımlayan bağlantılara bakın: bağımlılık özellikleri ve Dispose deseni.'
ms.date: 10/22/2008
helpviewer_keywords:
- design patterns in class libraries
- class library design guidelines [.NET Framework], design patterns
ms.assetid: f7bd1361-4ab2-4132-972d-a044b8f197e1
ms.openlocfilehash: ed580365f7d7bb3c91f1aa4065413f64e0e965db
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821469"
---
# <a name="common-design-patterns"></a><span data-ttu-id="0b8d5-103">Ortak Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="0b8d5-103">Common Design Patterns</span></span>
<span data-ttu-id="0b8d5-104">Desenlerin çok geniş bir konusuyla ilgili olan yazılım desenleri, desen dilleri ve kenar desenleri hakkında çok sayıda kitap vardır.</span><span class="sxs-lookup"><span data-stu-id="0b8d5-104">There are numerous books on software patterns, pattern languages, and antipatterns that address the very broad subject of patterns.</span></span> <span data-ttu-id="0b8d5-105">Bu nedenle, bu bölümde .NET Framework API 'Leri tasarımında sık kullanılan çok sınırlı bir desen kümesiyle ilgili yönergeler ve tartışmalar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b8d5-105">Thus, this chapter provides guidelines and discussion related to a very limited set of patterns that are used frequently in the design of the .NET Framework APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b8d5-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0b8d5-106">In This Section</span></span>  
 [<span data-ttu-id="0b8d5-107">Bağımlılık özellikleri</span><span class="sxs-lookup"><span data-stu-id="0b8d5-107">Dependency Properties</span></span>](dependency-properties.md)  
 [<span data-ttu-id="0b8d5-108">Dispose Deseni</span><span class="sxs-lookup"><span data-stu-id="0b8d5-108">Dispose Pattern</span></span>](../garbage-collection/implementing-dispose.md)  
 <span data-ttu-id="0b8d5-109">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="0b8d5-109">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0b8d5-110">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="0b8d5-110">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8d5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b8d5-111">See also</span></span>

- [<span data-ttu-id="0b8d5-112">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0b8d5-112">Framework Design Guidelines</span></span>](index.md)

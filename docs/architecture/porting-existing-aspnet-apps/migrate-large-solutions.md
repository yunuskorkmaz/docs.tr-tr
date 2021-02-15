---
title: Büyük çözümleri ASP.NET Core geçirin
description: Büyük ASP.NET MVC uygulamalarının ASP.NET Core nasıl geçirileceğiyle bir bakış.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: e0fcf4b975678e81a71bac800cbe8bd01f1b8d17
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488955"
---
# <a name="migrate-large-solutions-to-aspnet-core"></a><span data-ttu-id="fda3c-103">Büyük çözümleri ASP.NET Core geçirin</span><span class="sxs-lookup"><span data-stu-id="fda3c-103">Migrate large solutions to ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="fda3c-104">.NET Framework büyük çözümlerin .NET Core 'a geçirilmesi için bazı planlama yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fda3c-104">Migrating large solutions from .NET Framework to .NET Core requires some planning.</span></span> <span data-ttu-id="fda3c-105">Bağımlılıklar, bunlara bağımlı olan projelerden önce geçirilmesi veya güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="fda3c-105">Dependencies must be migrated or updated before the projects that depend on them.</span></span> <span data-ttu-id="fda3c-106">Bağımlılıkları belirleyebilen ve .NET Core 'a geçiş ile ilgili yardım sunan araçlar vardır.</span><span class="sxs-lookup"><span data-stu-id="fda3c-106">There are tools that can identify dependencies and offer help with migrating to .NET Core.</span></span> <span data-ttu-id="fda3c-107">Uygulamaya, kapsamına ve geçerli kullanım düzenlerine bağlı olarak, geçiş sırasında farklı stratejiler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fda3c-107">Depending on the app, its scope, and current usage patterns, different strategies may be employed when migrating.</span></span> <span data-ttu-id="fda3c-108">Tek seferde veya zaman içinde, geçerli sistemle yan yana geçiş yapabilirsiniz mi?</span><span class="sxs-lookup"><span data-stu-id="fda3c-108">Do you migrate it all at once, or over time, side-by-side with the current system?</span></span> <span data-ttu-id="fda3c-109">Geçerli sistemi yeni bir kez sarın ve işlevselliğini artımlı olarak değiştirir mi?</span><span class="sxs-lookup"><span data-stu-id="fda3c-109">Do you wrap the current system in the new one, and incrementally replace its functionality?</span></span>

<span data-ttu-id="fda3c-110">Bu bölümde, büyük bir çözüm için geçiş planı oluşturma, geçişe yardımcı olmak için araçları kullanma ve geçiş için göz önünde bulundurulması gereken bazı stratejiler hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="fda3c-110">In this chapter, you'll learn how create a migration plan for a large solution, how to use tools to help with the migration, and some strategies to consider for the migration itself.</span></span>

## <a name="references"></a><span data-ttu-id="fda3c-111">Başvurular</span><span class="sxs-lookup"><span data-stu-id="fda3c-111">References</span></span>

- [<span data-ttu-id="fda3c-112">Büyük MVC ve Web API uygulamalarını .NET Core 'a geçirmek için hangi konular önemlidir?</span><span class="sxs-lookup"><span data-stu-id="fda3c-112">What topics are important to migrating large MVC and Web API apps to .NET Core?</span></span>](https://twitter.com/ardalis/status/1313669040859217921)
- [<span data-ttu-id="fda3c-113">.NET Framework 'den .NET Core 'a taşıma</span><span class="sxs-lookup"><span data-stu-id="fda3c-113">Porting from .NET Framework to .NET Core</span></span>](https://docs.microsoft.com/dotnet/core/porting/)

>[!div class="step-by-step"]
><span data-ttu-id="fda3c-114">[Önceki](testing-differences.md) 
> [Sonraki](identify-migration-sequence.md)</span><span class="sxs-lookup"><span data-stu-id="fda3c-114">[Previous](testing-differences.md)
[Next](identify-migration-sequence.md)</span></span>

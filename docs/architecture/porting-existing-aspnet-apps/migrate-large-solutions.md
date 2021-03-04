---
title: Büyük çözümleri ASP.NET Core geçirin
description: Büyük ASP.NET MVC uygulamalarının ASP.NET Core nasıl geçirileceğiyle bir bakış.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d3ebd71213e074ce80dc83fc3230c4e365275ad3
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105889"
---
# <a name="migrate-large-solutions-to-aspnet-core"></a>Büyük çözümleri ASP.NET Core geçirin

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Framework büyük çözümlerin .NET Core 'a geçirilmesi için bazı planlama yapılması gerekir. Bağımlılıklar, bunlara bağımlı olan projelerden önce geçirilmesi veya güncelleştirilmeleri gerekir. Bağımlılıkları belirleyebilen ve .NET Core 'a geçiş ile ilgili yardım sunan araçlar vardır. Uygulamaya, kapsamına ve geçerli kullanım düzenlerine bağlı olarak, geçiş sırasında farklı stratejiler kullanılabilir. Tek seferde veya zaman içinde, geçerli sistemle yan yana geçiş yapabilirsiniz mi? Geçerli sistemi yeni bir kez sarın ve işlevselliğini artımlı olarak değiştirir mi?

Bu bölümde, büyük bir çözüm için geçiş planı oluşturma, geçişe yardımcı olmak için araçları kullanma ve geçiş için göz önünde bulundurulması gereken bazı stratejiler hakkında bilgi edineceksiniz.

## <a name="references"></a>Başvurular

- [Büyük MVC ve Web API uygulamalarını .NET Core 'a geçirmek için hangi konular önemlidir?](https://twitter.com/ardalis/status/1313669040859217921)
- [.NET Framework 'den .NET Core 'a taşıma](../../core/porting/index.md)

>[!div class="step-by-step"]
>[Önceki](testing-differences.md) 
> [Sonraki](identify-migration-sequence.md)

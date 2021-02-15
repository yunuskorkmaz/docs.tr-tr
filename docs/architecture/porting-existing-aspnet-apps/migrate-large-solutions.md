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
# <a name="migrate-large-solutions-to-aspnet-core"></a>Büyük çözümleri ASP.NET Core geçirin

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Framework büyük çözümlerin .NET Core 'a geçirilmesi için bazı planlama yapılması gerekir. Bağımlılıklar, bunlara bağımlı olan projelerden önce geçirilmesi veya güncelleştirilmeleri gerekir. Bağımlılıkları belirleyebilen ve .NET Core 'a geçiş ile ilgili yardım sunan araçlar vardır. Uygulamaya, kapsamına ve geçerli kullanım düzenlerine bağlı olarak, geçiş sırasında farklı stratejiler kullanılabilir. Tek seferde veya zaman içinde, geçerli sistemle yan yana geçiş yapabilirsiniz mi? Geçerli sistemi yeni bir kez sarın ve işlevselliğini artımlı olarak değiştirir mi?

Bu bölümde, büyük bir çözüm için geçiş planı oluşturma, geçişe yardımcı olmak için araçları kullanma ve geçiş için göz önünde bulundurulması gereken bazı stratejiler hakkında bilgi edineceksiniz.

## <a name="references"></a>Başvurular

- [Büyük MVC ve Web API uygulamalarını .NET Core 'a geçirmek için hangi konular önemlidir?](https://twitter.com/ardalis/status/1313669040859217921)
- [.NET Framework 'den .NET Core 'a taşıma](https://docs.microsoft.com/dotnet/core/porting/)

>[!div class="step-by-step"]
>[Önceki](testing-differences.md) 
> [Sonraki](identify-migration-sequence.md)

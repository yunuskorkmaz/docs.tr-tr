---
title: 'NETSDK1079: .NET Core 3,0 veya üzeri hedeflenirken Microsoft. AspNetCore. All paketi desteklenmez.'
description: Microsoft. AspNetCore. app 'ten geçişi çözme
author: dsplaisted
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1079
ms.openlocfilehash: e0b7aba909dbd2931f755238a2de2418d294751d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445803"
---
# <a name="netsdk1079-the-microsoftaspnetcoreall-package-is-not-supported-when-targeting-net-core-30-or-higher"></a>NETSDK1079: .NET Core 3,0 veya üzeri hedeflenirken Microsoft. AspNetCore. All paketi desteklenmez.

**Bu makale için geçerlidir:** ✔️ .NET Core SDK 3.1.100 ve sonraki sürümler

Şu durumlarda şu hata iletisini alabilirsiniz:

- ASP.NET Core bir projeyi .NET Core 2,2 veya daha önceki bir sürümden .NET Core 3,0 veya sonraki bir sürümüne yeniden hedefleyebilirsiniz.
- Proje Microsoft. AspNetCore. All paketini kullanır.

`PackageReference`Microsoft. AspNetCore. All için ' i kaldırın.  Ayrıca, Microsoft. AspNetCore. All 'tan başvurulan ancak ASP.NET Core paylaşılan çerçevesine dahil olmayan paketler için paket başvuruları eklemeniz gerekebilir.  Bu paketler burada listelenmiştir: [Microsoft. AspNetCore. All 'Dan Microsoft. AspNetCore. app 'e geçiş](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).

Ayrıca bkz. [ASP.NET Core 2,2 ' den 3,0 ' e geçiş](/aspnet/core/migration/22-to-30)

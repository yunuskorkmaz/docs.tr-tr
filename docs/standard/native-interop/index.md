---
title: Yerel birlikte çalışabilirliği - .NET
description: . NET'te yerel bileşenleriyle arabirim öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 29aacc9210b4103f379b7776c36fc3c29b9e6dec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973569"
---
# <a name="native-interoperability"></a>Native ile birlikte çalışma

Aşağıdaki makaleler, "yerel birlikte çalışabilirlik".NET yapmanın çeşitli yollarını göstermektedir.

Neden yerel kod içine çağırmak istiyorsunuz birkaç nedeni vardır:

* İşletim sistemleri, büyük hacimli yönetilen sınıf kitaplıklarında bulunmayan API'leri ile gelir. Bu senaryo için birinci bir örnek, donanım veya işletim sistemi yönetim işlevlerine erişimi olacaktır.
* C stili Abı'ler (yerel Abı'ler) oluşturabilir veya diğer bileşenlerle aracılığıyla gösterilir, Java kodu gibi iletişim kurarak [Java yerel arabirimi (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) veya yerel bir bileşeni oluşturabilecek herhangi bir yönetilen dil.
* Windows üzerinde çoğu, Microsoft Office suite gibi yüklenen yazılım programlarını temsil eder ve bunları otomatik hale getirmek ya da kullandığınız geliştiricilerin izin veren COM bileşenlerini kaydeder. Bu ayrıca yerel birlikte çalışabilirliği gerektirir.

Önceki listede tüm olası durumlar ve hangi geliştirici istediğiniz/gibi/yerel bileşenleriyle arabirim oluşturmak için gerekecek senaryoları ele alınmamıştır. .NET sınıf kitaplığı, yerel birlikte çalışabilirliği destek adil birkaç Konsolu desteği ve işleme, dosya sistemi erişimini ve diğerleri gibi kendi API uygulamak için örneği için kullanır. Ancak, gerekirse bir seçenek olduğuna dikkat edin önemlidir.

> [!NOTE]
> Bu bölümdeki örnekler çoğu için üç tüm desteklenen platformlar için .NET Core (Windows, Linux ve macOS) sunulur. Ancak, bazı kısa ve yalnızca tanım örnekler için Windows dosya adları ve uzantıları (diğer bir deyişle, kitaplıkları için "dll") kullanan tek bir örnek gösterilir. Bu özelliklerden Linux veya Macos'ta kullanılabilir değil, yalnızca bu çok kolaylık sağlamak için yapılmıştır gelmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Platform Çağırma (P/Invoke)](pinvoke.md)
- [Tür hazırlama](type-marshalling.md)
- [Yerel birlikte çalışabilirliği en iyi uygulamalar](best-practices.md)

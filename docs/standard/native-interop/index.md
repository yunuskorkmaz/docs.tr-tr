---
title: Yerel birlikte çalışabilirlik - .NET
description: .NET'te yerel bileşenlerle nasıl arayüz arayla iletişim etobur sunmayı öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 330466d74cc268214f74c4f575e6a2961f678972
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706341"
---
# <a name="native-interoperability"></a>Native ile birlikte çalışma

Aşağıdaki makaleler .NET'te "yerel birlikte çalışabilirlik" yapmanın çeşitli yollarını göstermektedir.

Yerel kodu aramak istemenizin birkaç nedeni vardır:

- İşletim sistemleri, yönetilen sınıf kitaplıklarında bulunmayan büyük hacimli API'lerle birlikte gelir. Bu senaryo için en önemli örnek donanım veya işletim sistemi yönetim işlevlerine erişim olacaktır.
- [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) veya yerel bir bileşen oluşturabilecek başka bir yönetilen dil aracılığıyla ortaya çıkarılan Java kodu gibi C stili ABI'leri (yerel ABI' ler) olan veya üretebilen diğer bileşenlerle iletişim kurmak.
- Windows'da, Microsoft Office paketi gibi yüklenen yazılımların çoğu, programlarını temsil eden ve geliştiricilerin bunları otomatikleştirmesine veya kullanmasına izin veren COM bileşenlerini kaydeder. Bu da yerel birlikte çalışabilirlik gerektirir.

Önceki liste, geliştiricinin yerel bileşenlerle ara birim yapmak istediği/beğeneceği/ihtiyaç dalacağı tüm olası durumları ve senaryoları kapsamaz. .NET sınıf kitaplığı, örneğin, konsol desteği ve manipülasyon, dosya sistemi erişimi ve diğerleri gibi adil sayıda API'sini uygulamak için yerel birlikte çalışabilirlik desteğini kullanır. Ancak, gerekirse bir seçenek olduğunu unutmayın.

> [!NOTE]
> Bu bölümdeki örneklerin çoğu .NET Core (Windows, Linux ve macOS) için desteklenen üç platform için de sunulacaktır. Ancak, bazı kısa ve açıklayıcı örnekler için, Windows dosya adlarını ve uzantılarını kullanan tek bir örnek gösterilir (diğer bir şekilde kitaplıklar için "dll"). Bu bu özellikleri Linux veya macOS mevcut olmadığı anlamına gelmez, sadece kolaylık uğruna yapıldı.

## <a name="see-also"></a>Ayrıca bkz.

- [Platform Çağırma (P/Invoke)](pinvoke.md)
- [Tür hazırlama](type-marshaling.md)
- [Yerel birlikte çalışabilirlik en iyi uygulamalar](best-practices.md)

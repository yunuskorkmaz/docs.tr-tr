---
title: WCF geliştiricileri için gRPC-gRPC 'ye Genel Bakış
description: GRPC 'nin geliştirilmesine kılavuzluk eden ilkeler kümesi hakkında bilgi edinin.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b372cc9dcdb2efd605b3d9b688513e4ff8530b01
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184444"
---
# <a name="grpc-overview"></a>gRPC genel bakış

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Son bölümde hem WCF hem de gRPC 'nin genesare ' a bakdıktan sonra, bu bölümde gRPC 'nin bazı önemli özellikleri ve WCF ile nasıl karşılaştırılacağı ele alınacaktır.

ASP.NET Core 3,0, GRPC 'nin resmi .NET uygulamasına katkıda bulunan Microsoft ekipleriyle, gRPC 'yi bir birinci sınıf vatandaşlık olarak yerel olarak destekleyen ilk ASP.NET sürümüdür. .NET ile, diğer tüm büyük programlama dilleri ve çerçeveleri ile birlikte çalışabilmeye yönelik dağıtılmış uygulamalar oluşturmak için en iyi yaklaşım önerilir.

## <a name="key-principles"></a>Temel ilkeler

Bölüm 1 ' de anlatıldığı gibi, Google Stubby, onun iç, genel amaçlı RPC altyapısına yeniden çalışma için HTTP/2 girişini kullanmak istedi. GRPC yeniden adlandırılmış Stubby, artık standartdan yararlanabilir ve uygulanabilirliğini mobil bilgi işlem, bulut ve Nesnelerin İnterneti genişletebilirler.

Bunu başarmak için, [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) , GRPC 'yi yönetecek bir ilkeler kümesi kurdu. Aşağıdaki listede, en iyi şekilde erişilebilirlik ve kullanışlılığın en üst düzeye çıkarmasından ilgisi olan en ilgili olanlar gösterilmektedir:

- **Ücretsiz ve açık** – tüm yapıtlar, geliştiricilerin GRPC 'yi benimsemelerine kısıtlama gerektirmeyen lisanslama ile açık kaynak olmalıdır.
- **Kapsam ve basitlik** – GRPC, tüm popüler platformlarda kullanılabilir ve her platformda derlemek için yeterince kolay olmalıdır.
- **Birlikte çalışabilirlik ve erişim** – bant genişliği veya gecikme süresi ne olursa olsun, geniş kullanılabilir ağ standartları kullanılarak GRPC 'yi herhangi bir ağda kullanmak mümkün olmalıdır.
- **Genel amaçlı ve** performans: Framework, performansa ödün vermeden mümkün olduğunca geniş bir kullanım talebi yelpazaya kadar kullanılabilir olmalıdır.
- **Akış** : protokol, büyük veri kümeleri veya zaman uyumsuz mesajlaşma için akış semantiğini sağlamalıdır.
- **Meta veri değişimi** – protokol, kimlik doğrulama belirteçleri gibi iş dışı verilerin gerçek iş verilerinden ayrı olarak işlenmesine izin verir.
- **Standartlaştırılmış durum kodları** : hata işleme kararlarını daha net hale getirmek ve ek daha zengin hata işleme gerekliyse, bunu meta veri değişimi içinde yönetmek için bir mekanizma sağlanmalıdır.

>[!div class="step-by-step"]
>[Önceki](introduction.md)
>[İleri](approach.md)

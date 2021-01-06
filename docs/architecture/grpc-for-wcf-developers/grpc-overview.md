---
title: WCF geliştiricileri için gRPC-gRPC 'ye Genel Bakış
description: GRPC 'nin geliştirilmesine kılavuzluk eden ilkeler kümesi hakkında bilgi edinin.
ms.date: 12/15/2020
ms.openlocfilehash: 99e1bdb1f49469f444044027c3ac5d927f9cab13
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938409"
---
# <a name="grpc-overview"></a>gRPC genel bakış

Son bölümde hem Windows Communication Foundation (WCF) hem de gRPC 'nin genesto ' a bakdıktan sonra, bu bölümde gRPC 'nin bazı önemli özellikleri ve bunların WCF ile nasıl Karşılaştırıldığı ele alır.

ASP.NET Core 3,0, GRPC 'nin resmi .NET uygulamasına katkıda bulunan Microsoft ekipleriyle, gRPC 'yi bir birinci sınıf vatandaşlık olarak yerel olarak destekleyen ilk ASP.NET sürümüdür. Diğer tüm büyük programlama dilleri ve çerçeveleri ile birlikte çalışan, .NET ile dağıtılmış uygulamalar oluşturmak için önerilir.

## <a name="key-principles"></a>Temel ilkeler

Bölüm 1 ' de anlatıldığı gibi, Google Stubby, kendi iç, genel amaçlı RPC altyapısını değiştirmek için HTTP/2 girişini kullanmak istedi. gRPC, Stubby temel alınarak standartlarından yararlanabilir ve uygulanabilirliğini mobil bilgi işlem, bulut ve Nesnelerin İnterneti genişletebilirler.

Bu standartlığa ulaşmak için [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) , GRPC 'yi yönetecek bir ilke kümesi kurdu. Aşağıdaki listede, en iyi şekilde erişilebilirliği ve kullanılabilirliği en üst düzeye çıkarmak için önemli olan en ilgili olanlar gösterilmektedir:

- **Ücretsiz ve açık** – tüm yapıtlar, geliştiricilerin GRPC 'yi benimseme ile sınırlandırmasız lisanslama ile açık kaynak olmalıdır.
- **Kapsam ve basitlik** – GRPC her bir popüler platformda kullanılabilir ve her platformda derlemek için yeterince kolay olmalıdır.
- **Birlikte çalışabilirlik ve erişim** – bant genişliği veya gecikme süresi ne olursa olsun, geniş kullanılabilir ağ standartları kullanarak GRPC 'yi herhangi bir ağda kullanmak mümkün olmalıdır.
- **Genel amaçlı ve** performans: Framework, performansa ödün vermeden mümkün olduğunca geniş bir kullanım talebi yelpazaya kadar kullanılabilir olmalıdır.
- **Akış** : protokol, büyük veri kümeleri veya zaman uyumsuz mesajlaşma için akış semantiğini sağlamalıdır.
- **Meta veri değişimi** – protokol, kimlik doğrulama belirteçleri gibi iş dışı verilerin gerçek iş verilerinden ayrı olarak işlenmesine izin verir.
- **Standartlaştırılmış durum kodları** – hata işleme kararlarını daha net hale getirmek için hata kodlarının değişkenliği azaltılmalıdır. Ek, daha zengin hata işleme gerektiğinde, meta veri değişimi içindeki davranışı yönetmek için bir mekanizma sağlanmalıdır.

>[!div class="step-by-step"]
>[Önceki](introduction.md) 
> [Sonraki](approach.md)

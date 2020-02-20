---
title: Protokol arabellekleri-WCF geliştiricileri için gRPC
description: GRPC ağı için kullanılan protokol arabellekleri hat biçimine giriş.
ms.date: 09/09/2019
ms.openlocfilehash: cc4ff272a9912d6f2dd8f8ddb1972c7369f980fe
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503448"
---
# <a name="protocol-buffers"></a>Protokol arabellekleri

gRPC Hizmetleri, Windows Communication Foundation (WCF) içindeki veri sözleşmelerine benzer şekilde, verileri *protokol arabelleği (Protobuffer)* olarak gönderir ve alır. Prototip,, XML veya JSON gibi insan tarafından okunabilen biçimlerin yükü olmadan, okuma ve yazma amacıyla makineler için yapılandırılmış verileri serileştirmenin etkili bir yoludur.

Bu bölümde, prototipin nasıl çalıştığı ve kendi Prototipsiz iletilerinizin nasıl tanımlanacağı ele alınmaktadır.

## <a name="how-protobuf-works"></a>Prototiparabelleği çalışma

WCF veri sözleşmeleri de dahil olmak üzere çoğu .NET nesne serileştirme tekniği, çalışma zamanında nesne yapısını çözümlemek için yansıma kullanarak çalışır. Buna karşılık, çoğu prototip kitaplıkları bir `.proto` dosyasında adanmış bir dil (*protokol arabelleği dili*) kullanarak yapıyı tanımlamanızı gerektirir. Daha sonra bir derleyici, Desteklenen platformların herhangi biri için kod oluşturmak üzere bu dosyayı kullanır. Desteklenen platformlar .NET, Java, C/C++, JavaScript ve çok daha fazlasını içerir. 

Prototip derleyicisi, `protoc`, alternatif uygulamalar kullanılabilir olsa da Google tarafından korunur. Oluşturulan kod verimli ve verilerin hızlı serileştirilmesi ve seri durumundan çıkarılması için iyileştirilmiştir.

Protohat Tel biçimi ikili bir kodlamadır. İletileri temsil etmek için kullanılan bayt sayısını en aza indirmek için bazı zekice püf noktalarını kullanır. İkili kodlama biçimi bilgisi, Protoarabelleğe kullanımı için gerekli değildir. Ancak ilgileniyorsanız, [protokol arabellekleri Web sitesinde](https://developers.google.com/protocol-buffers/docs/encoding)hakkında daha fazla bilgi edinebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](why-grpc.md)
>[İleri](protobuf-messages.md)

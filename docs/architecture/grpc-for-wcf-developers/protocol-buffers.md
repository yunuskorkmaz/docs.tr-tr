---
title: Protokol arabellekleri-WCF geliştiricileri için gRPC
description: GRPC ağı için kullanılan protokol arabellekleri hat biçimine giriş.
ms.date: 09/09/2019
ms.openlocfilehash: dbe8cb43475cfeec19051daf68452ef86269372f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967290"
---
# <a name="protocol-buffers"></a>Protokol arabellekleri

gRPC Hizmetleri, WCF 'nin veri sözleşmelerine benzer şekilde, verileri *protokol arabelleği (Protobuffer)* olarak gönderir ve alır. Prototip,, XML veya JSON gibi insan tarafından okunabilen biçimlerin yükü olmadan, okuma ve yazma amacıyla makineler için yapılandırılmış verileri serileştirmenin etkili bir yoludur.

Bu bölümde, prototipin nasıl çalıştığı ve kendi Prototipsiz iletilerinizin nasıl tanımlanacağı ele alınmaktadır.

## <a name="how-protobuf-works"></a>Prototiparabelleği çalışma

WCF veri sözleşmeleri de dahil olmak üzere çoğu .NET nesne serileştirme tekniği, çalışma zamanında nesne yapısını çözümlemek için yansıma kullanarak çalışır. Buna karşılık, çoğu prototip kitaplığı, yapıyı bir `.proto` dosyasında adanmış bir dil (*protokol arabelleği dili*) kullanarak tanımlamanızı gerektirir. Bu dosya daha sonra .NET, Java, C/C++, JavaScript ve çok daha fazlasını içeren desteklenen platformlardan herhangi biri için kod oluşturmak üzere bir derleyici tarafından kullanılır. Prototip derleyicisi, `protoc`, alternatif uygulamalar kullanılabilir olsa da Google tarafından korunur. Oluşturulan kod verimli ve verilerin hızlı serileştirilmesi ve seri durumundan çıkarılması için iyileştirilmiştir.

Protohat Tel biçimi, iletileri temsil etmek için kullanılan bayt sayısını en aza indirmek için bazı zekice püf noktalarını kullanan ikili bir kodlamadır. İkili kodlama biçimi bilgisi Protobellek kullanımı için gerekli değildir, ancak ilgilendiğiniz hakkında daha fazla bilgi edinmek için [protokol arabellekleri Web sitesinde](https://developers.google.com/protocol-buffers/docs/encoding)bulabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](why-grpc.md)
>[İleri](protobuf-messages.md)

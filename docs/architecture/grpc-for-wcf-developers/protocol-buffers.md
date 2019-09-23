---
title: Protokol arabellekleri-WCF geliştiricileri için gRPC
description: GRPC ağı için kullanılan protokol arabellekleri hat biçimine giriş.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 4f9031c86731ea7ded4a812be9967237e52c4b39
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184171"
---
# <a name="protocol-buffers"></a>Protokol arabellekleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

gRPC Hizmetleri, WCF 'nin veri sözleşmelerine benzer şekilde, verileri *protokol arabelleği (Protobuffer)* olarak gönderir ve alır. Prototip,, XML veya JSON gibi insan tarafından okunabilen biçimlerin yükü olmadan, okuma ve yazma amacıyla makineler için yapılandırılmış verileri serileştirmenin etkili bir yoludur.

Bu bölümde, prototipin nasıl çalıştığı ve kendi Prototipsiz iletilerinizin nasıl tanımlanacağı ele alınmaktadır.

## <a name="how-protobuf-works"></a>Prototiparabelleği çalışma

WCF veri sözleşmeleri de dahil olmak üzere çoğu .NET nesne serileştirme tekniği, çalışma zamanında nesne yapısını çözümlemek için yansıma kullanarak çalışır. Buna karşılık, çoğu prototip kitaplığı, bir `.proto` dosyada özel bir dil (*protokol arabelleği dili*) kullanarak yapıyı önceden tanımlamanızı gerektirir. Bu dosya daha sonra .NET, Java, C/C++, JavaScript ve çok daha fazlasını içeren desteklenen platformlardan herhangi biri için kod oluşturmak üzere bir derleyici tarafından kullanılır. Prototip derleyicisi `protoc`, diğer uygulamalar kullanılabilir olsa da Google tarafından korunur. Oluşturulan kod verimli ve verilerin hızlı serileştirilmesi ve seri durumundan çıkarılması için iyileştirilmiştir.

Protohat Tel biçimi, iletileri temsil etmek için kullanılan bayt sayısını en aza indirmek için bazı zekice püf noktalarını kullanan ikili bir kodlamadır. İkili kodlama biçimi bilgisi Protobellek kullanımı için gerekli değildir, ancak ilgilendiğiniz hakkında daha fazla bilgi edinmek için [protokol arabellekleri Web sitesinde](https://developers.google.com/protocol-buffers/docs/encoding)bulabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](why-grpc.md)
>[İleri](protobuf-messages.md)

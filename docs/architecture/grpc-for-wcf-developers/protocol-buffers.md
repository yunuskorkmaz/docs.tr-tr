---
title: Protokol Arabellekleri - WCF geliştiricileri için gRPC
description: gRPC ağ için kullanılan Protokol Arabellekleri tel formatına giriş.
ms.date: 09/09/2019
ms.openlocfilehash: 35319d299a8bc2866a87954b3e54bfda9314ffe8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147938"
---
# <a name="protocol-buffers"></a>Protokol arabellekleri

gRPC hizmetleri, Windows Communication Foundation (WCF)'deki veri sözleşmelerine benzer şekilde *Protokol Arabelleği (Protobuf) iletileri*olarak veri gönderir ve alır. Protobuf, XML veya JSON gibi insan tarafından okunabilir biçimlerin maruz kalınması nasibini almadan, makinelerin okuma ve yazma için yapılandırılmış verileri serihale getirmenin etkili bir yoludur.

Bu bölümde Protobuf'un nasıl çalıştığı ve kendi Protobuf iletilerinizi nasıl tanımlayılabilmek yer alabilen.

## <a name="how-protobuf-works"></a>Protobuf nasıl çalışır?

WCF'nin veri sözleşmeleri de dahil olmak üzere çoğu .NET nesne serileştirme tekniği, çalışma zamanında nesne yapısını çözümlemek için yansımayı kullanarak çalışır. Bunun aksine, çoğu Protobuf kitaplığı, bir `.proto` dosyada özel bir dil *(Protokol Arabelleği*Dili) kullanarak yapıyı önceden tanımlamanızı gerektirir. Bir derleyici daha sonra desteklenen platformlardan herhangi biri için kod oluşturmak için bu dosyayı kullanır. Desteklenen platformlar .NET, Java, C/C++, JavaScript ve daha birçok içerir.

Alternatif uygulamalar mevcut olmasına `protoc`rağmen Protobuf derleyicisi, Google tarafından korunur. Oluşturulan kod verimlidir ve verilerin hızlı serileştirilmesi ve deserialization için optimize edin.

Protobuf tel biçimi ikili bir kodlamadır. İletileri temsil etmek için kullanılan bayt sayısını en aza indirmek için bazı zekice hileler kullanır. Protobuf'u kullanmak için ikili kodlama biçimi bilgisi ne kadar gerekli değildir. Ancak ilgileniyorsanız, [protokol arabellekleri web sitesinden](https://developers.google.com/protocol-buffers/docs/encoding)bu konuda daha fazla bilgi edinebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](why-grpc.md)
>[Sonraki](protobuf-messages.md)

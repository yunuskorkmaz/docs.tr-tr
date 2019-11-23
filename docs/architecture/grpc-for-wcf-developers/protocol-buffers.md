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
# <a name="protocol-buffers"></a><span data-ttu-id="3a042-103">Protokol arabellekleri</span><span class="sxs-lookup"><span data-stu-id="3a042-103">Protocol buffers</span></span>

<span data-ttu-id="3a042-104">gRPC Hizmetleri, WCF 'nin veri sözleşmelerine benzer şekilde, verileri *protokol arabelleği (Protobuffer)* olarak gönderir ve alır.</span><span class="sxs-lookup"><span data-stu-id="3a042-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to WCF's data contracts.</span></span> <span data-ttu-id="3a042-105">Prototip,, XML veya JSON gibi insan tarafından okunabilen biçimlerin yükü olmadan, okuma ve yazma amacıyla makineler için yapılandırılmış verileri serileştirmenin etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="3a042-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="3a042-106">Bu bölümde, prototipin nasıl çalıştığı ve kendi Prototipsiz iletilerinizin nasıl tanımlanacağı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a042-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="3a042-107">Prototiparabelleği çalışma</span><span class="sxs-lookup"><span data-stu-id="3a042-107">How Protobuf works</span></span>

<span data-ttu-id="3a042-108">WCF veri sözleşmeleri de dahil olmak üzere çoğu .NET nesne serileştirme tekniği, çalışma zamanında nesne yapısını çözümlemek için yansıma kullanarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="3a042-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at run time.</span></span> <span data-ttu-id="3a042-109">Buna karşılık, çoğu prototip kitaplığı, yapıyı bir `.proto` dosyasında adanmış bir dil (*protokol arabelleği dili*) kullanarak tanımlamanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3a042-109">By contrast, most Protobuf libraries require you to define the structure up front using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="3a042-110">Bu dosya daha sonra .NET, Java, C/C++, JavaScript ve çok daha fazlasını içeren desteklenen platformlardan herhangi biri için kod oluşturmak üzere bir derleyici tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a042-110">This file is then used by a compiler to generate code for any of the supported platforms, including .NET, Java, C/C++, JavaScript, and many more.</span></span> <span data-ttu-id="3a042-111">Prototip derleyicisi, `protoc`, alternatif uygulamalar kullanılabilir olsa da Google tarafından korunur.</span><span class="sxs-lookup"><span data-stu-id="3a042-111">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="3a042-112">Oluşturulan kod verimli ve verilerin hızlı serileştirilmesi ve seri durumundan çıkarılması için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3a042-112">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="3a042-113">Protohat Tel biçimi, iletileri temsil etmek için kullanılan bayt sayısını en aza indirmek için bazı zekice püf noktalarını kullanan ikili bir kodlamadır.</span><span class="sxs-lookup"><span data-stu-id="3a042-113">The Protobuf wire format itself is a binary encoding, which uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="3a042-114">İkili kodlama biçimi bilgisi Protobellek kullanımı için gerekli değildir, ancak ilgilendiğiniz hakkında daha fazla bilgi edinmek için [protokol arabellekleri Web sitesinde](https://developers.google.com/protocol-buffers/docs/encoding)bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a042-114">Knowledge of the binary encoding format isn't necessary to use Protobuf, but if you're interested you can learn more about it on [the Protocol Buffers web site](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3a042-115">[Önceki](why-grpc.md)
>[İleri](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="3a042-115">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>

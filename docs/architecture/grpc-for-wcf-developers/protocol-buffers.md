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
# <a name="protocol-buffers"></a><span data-ttu-id="1b3cd-103">Protokol arabellekleri</span><span class="sxs-lookup"><span data-stu-id="1b3cd-103">Protocol buffers</span></span>

<span data-ttu-id="1b3cd-104">gRPC Hizmetleri, Windows Communication Foundation (WCF) içindeki veri sözleşmelerine benzer şekilde, verileri *protokol arabelleği (Protobuffer)* olarak gönderir ve alır.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="1b3cd-105">Prototip,, XML veya JSON gibi insan tarafından okunabilen biçimlerin yükü olmadan, okuma ve yazma amacıyla makineler için yapılandırılmış verileri serileştirmenin etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="1b3cd-106">Bu bölümde, prototipin nasıl çalıştığı ve kendi Prototipsiz iletilerinizin nasıl tanımlanacağı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="1b3cd-107">Prototiparabelleği çalışma</span><span class="sxs-lookup"><span data-stu-id="1b3cd-107">How Protobuf works</span></span>

<span data-ttu-id="1b3cd-108">WCF veri sözleşmeleri de dahil olmak üzere çoğu .NET nesne serileştirme tekniği, çalışma zamanında nesne yapısını çözümlemek için yansıma kullanarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="1b3cd-109">Buna karşılık, çoğu prototip kitaplıkları bir `.proto` dosyasında adanmış bir dil (*protokol arabelleği dili*) kullanarak yapıyı tanımlamanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="1b3cd-110">Daha sonra bir derleyici, Desteklenen platformların herhangi biri için kod oluşturmak üzere bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="1b3cd-111">Desteklenen platformlar .NET, Java, C/C++, JavaScript ve çok daha fazlasını içerir.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span> 

<span data-ttu-id="1b3cd-112">Prototip derleyicisi, `protoc`, alternatif uygulamalar kullanılabilir olsa da Google tarafından korunur.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="1b3cd-113">Oluşturulan kod verimli ve verilerin hızlı serileştirilmesi ve seri durumundan çıkarılması için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="1b3cd-114">Protohat Tel biçimi ikili bir kodlamadır.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="1b3cd-115">İletileri temsil etmek için kullanılan bayt sayısını en aza indirmek için bazı zekice püf noktalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="1b3cd-116">İkili kodlama biçimi bilgisi, Protoarabelleğe kullanımı için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="1b3cd-117">Ancak ilgileniyorsanız, [protokol arabellekleri Web sitesinde](https://developers.google.com/protocol-buffers/docs/encoding)hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b3cd-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1b3cd-118">[Önceki](why-grpc.md)
>[İleri](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="1b3cd-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>

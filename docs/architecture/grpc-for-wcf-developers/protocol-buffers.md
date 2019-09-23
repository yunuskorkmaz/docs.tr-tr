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
# <a name="protocol-buffers"></a><span data-ttu-id="48b69-103">Protokol arabellekleri</span><span class="sxs-lookup"><span data-stu-id="48b69-103">Protocol buffers</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="48b69-104">gRPC Hizmetleri, WCF 'nin veri sözleşmelerine benzer şekilde, verileri *protokol arabelleği (Protobuffer)* olarak gönderir ve alır.</span><span class="sxs-lookup"><span data-stu-id="48b69-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to WCF's data contracts.</span></span> <span data-ttu-id="48b69-105">Prototip,, XML veya JSON gibi insan tarafından okunabilen biçimlerin yükü olmadan, okuma ve yazma amacıyla makineler için yapılandırılmış verileri serileştirmenin etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="48b69-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="48b69-106">Bu bölümde, prototipin nasıl çalıştığı ve kendi Prototipsiz iletilerinizin nasıl tanımlanacağı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48b69-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="48b69-107">Prototiparabelleği çalışma</span><span class="sxs-lookup"><span data-stu-id="48b69-107">How Protobuf works</span></span>

<span data-ttu-id="48b69-108">WCF veri sözleşmeleri de dahil olmak üzere çoğu .NET nesne serileştirme tekniği, çalışma zamanında nesne yapısını çözümlemek için yansıma kullanarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="48b69-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at run time.</span></span> <span data-ttu-id="48b69-109">Buna karşılık, çoğu prototip kitaplığı, bir `.proto` dosyada özel bir dil (*protokol arabelleği dili*) kullanarak yapıyı önceden tanımlamanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="48b69-109">By contrast, most Protobuf libraries require you to define the structure up front using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="48b69-110">Bu dosya daha sonra .NET, Java, C/C++, JavaScript ve çok daha fazlasını içeren desteklenen platformlardan herhangi biri için kod oluşturmak üzere bir derleyici tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48b69-110">This file is then used by a compiler to generate code for any of the supported platforms, including .NET, Java, C/C++, JavaScript, and many more.</span></span> <span data-ttu-id="48b69-111">Prototip derleyicisi `protoc`, diğer uygulamalar kullanılabilir olsa da Google tarafından korunur.</span><span class="sxs-lookup"><span data-stu-id="48b69-111">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="48b69-112">Oluşturulan kod verimli ve verilerin hızlı serileştirilmesi ve seri durumundan çıkarılması için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="48b69-112">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="48b69-113">Protohat Tel biçimi, iletileri temsil etmek için kullanılan bayt sayısını en aza indirmek için bazı zekice püf noktalarını kullanan ikili bir kodlamadır.</span><span class="sxs-lookup"><span data-stu-id="48b69-113">The Protobuf wire format itself is a binary encoding, which uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="48b69-114">İkili kodlama biçimi bilgisi Protobellek kullanımı için gerekli değildir, ancak ilgilendiğiniz hakkında daha fazla bilgi edinmek için [protokol arabellekleri Web sitesinde](https://developers.google.com/protocol-buffers/docs/encoding)bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48b69-114">Knowledge of the binary encoding format isn't necessary to use Protobuf, but if you're interested you can learn more about it on [the Protocol Buffers web site](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="48b69-115">[Önceki](why-grpc.md)
>[İleri](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="48b69-115">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>

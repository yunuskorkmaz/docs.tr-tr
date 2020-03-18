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
# <a name="protocol-buffers"></a><span data-ttu-id="f4cba-103">Protokol arabellekleri</span><span class="sxs-lookup"><span data-stu-id="f4cba-103">Protocol buffers</span></span>

<span data-ttu-id="f4cba-104">gRPC hizmetleri, Windows Communication Foundation (WCF)'deki veri sözleşmelerine benzer şekilde *Protokol Arabelleği (Protobuf) iletileri*olarak veri gönderir ve alır.</span><span class="sxs-lookup"><span data-stu-id="f4cba-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f4cba-105">Protobuf, XML veya JSON gibi insan tarafından okunabilir biçimlerin maruz kalınması nasibini almadan, makinelerin okuma ve yazma için yapılandırılmış verileri serihale getirmenin etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="f4cba-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="f4cba-106">Bu bölümde Protobuf'un nasıl çalıştığı ve kendi Protobuf iletilerinizi nasıl tanımlayılabilmek yer alabilen.</span><span class="sxs-lookup"><span data-stu-id="f4cba-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="f4cba-107">Protobuf nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="f4cba-107">How Protobuf works</span></span>

<span data-ttu-id="f4cba-108">WCF'nin veri sözleşmeleri de dahil olmak üzere çoğu .NET nesne serileştirme tekniği, çalışma zamanında nesne yapısını çözümlemek için yansımayı kullanarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="f4cba-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="f4cba-109">Bunun aksine, çoğu Protobuf kitaplığı, bir `.proto` dosyada özel bir dil *(Protokol Arabelleği*Dili) kullanarak yapıyı önceden tanımlamanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f4cba-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="f4cba-110">Bir derleyici daha sonra desteklenen platformlardan herhangi biri için kod oluşturmak için bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4cba-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="f4cba-111">Desteklenen platformlar .NET, Java, C/C++, JavaScript ve daha birçok içerir.</span><span class="sxs-lookup"><span data-stu-id="f4cba-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span>

<span data-ttu-id="f4cba-112">Alternatif uygulamalar mevcut olmasına `protoc`rağmen Protobuf derleyicisi, Google tarafından korunur.</span><span class="sxs-lookup"><span data-stu-id="f4cba-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="f4cba-113">Oluşturulan kod verimlidir ve verilerin hızlı serileştirilmesi ve deserialization için optimize edin.</span><span class="sxs-lookup"><span data-stu-id="f4cba-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="f4cba-114">Protobuf tel biçimi ikili bir kodlamadır.</span><span class="sxs-lookup"><span data-stu-id="f4cba-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="f4cba-115">İletileri temsil etmek için kullanılan bayt sayısını en aza indirmek için bazı zekice hileler kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4cba-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="f4cba-116">Protobuf'u kullanmak için ikili kodlama biçimi bilgisi ne kadar gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f4cba-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="f4cba-117">Ancak ilgileniyorsanız, [protokol arabellekleri web sitesinden](https://developers.google.com/protocol-buffers/docs/encoding)bu konuda daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4cba-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f4cba-118">[Önceki](why-grpc.md)
>[Sonraki](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="f4cba-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>

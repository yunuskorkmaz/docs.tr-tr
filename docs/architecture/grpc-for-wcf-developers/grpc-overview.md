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
# <a name="grpc-overview"></a><span data-ttu-id="07bb6-103">gRPC genel bakış</span><span class="sxs-lookup"><span data-stu-id="07bb6-103">gRPC overview</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="07bb6-104">Son bölümde hem WCF hem de gRPC 'nin genesare ' a bakdıktan sonra, bu bölümde gRPC 'nin bazı önemli özellikleri ve WCF ile nasıl karşılaştırılacağı ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="07bb6-104">After looking at the genesis of both WCF and gRPC in the last chapter, this chapter will consider some of the key features of gRPC and how they compare to WCF.</span></span>

<span data-ttu-id="07bb6-105">ASP.NET Core 3,0, GRPC 'nin resmi .NET uygulamasına katkıda bulunan Microsoft ekipleriyle, gRPC 'yi bir birinci sınıf vatandaşlık olarak yerel olarak destekleyen ilk ASP.NET sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="07bb6-105">ASP.NET Core 3.0 is the first release of ASP.NET that natively supports gRPC as a first-class citizen, with Microsoft teams contributing to the official .NET implementation of gRPC.</span></span> <span data-ttu-id="07bb6-106">.NET ile, diğer tüm büyük programlama dilleri ve çerçeveleri ile birlikte çalışabilmeye yönelik dağıtılmış uygulamalar oluşturmak için en iyi yaklaşım önerilir.</span><span class="sxs-lookup"><span data-stu-id="07bb6-106">It's recommended as the best approach for building distributed applications with .NET that can interoperate with all other major programming languages and frameworks.</span></span>

## <a name="key-principles"></a><span data-ttu-id="07bb6-107">Temel ilkeler</span><span class="sxs-lookup"><span data-stu-id="07bb6-107">Key principles</span></span>

<span data-ttu-id="07bb6-108">Bölüm 1 ' de anlatıldığı gibi, Google Stubby, onun iç, genel amaçlı RPC altyapısına yeniden çalışma için HTTP/2 girişini kullanmak istedi.</span><span class="sxs-lookup"><span data-stu-id="07bb6-108">As discussed in chapter 1, Google wanted to use the introduction of HTTP/2 to rework Stubby, its internal, general purpose RPC infrastructure.</span></span> <span data-ttu-id="07bb6-109">GRPC yeniden adlandırılmış Stubby, artık standartdan yararlanabilir ve uygulanabilirliğini mobil bilgi işlem, bulut ve Nesnelerin İnterneti genişletebilirler.</span><span class="sxs-lookup"><span data-stu-id="07bb6-109">Stubby, renamed gRPC, now could take advantage of standardization and would extend its applicability to mobile computing, the cloud, and the Internet of Things.</span></span>

<span data-ttu-id="07bb6-110">Bunu başarmak için, [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) , GRPC 'yi yönetecek bir ilkeler kümesi kurdu.</span><span class="sxs-lookup"><span data-stu-id="07bb6-110">To achieve this, the [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) established a set of principles that would govern gRPC.</span></span> <span data-ttu-id="07bb6-111">Aşağıdaki listede, en iyi şekilde erişilebilirlik ve kullanışlılığın en üst düzeye çıkarmasından ilgisi olan en ilgili olanlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="07bb6-111">The following list shows the most relevant ones, which are mainly concerned with maximizing accessibility and usability:</span></span>

- <span data-ttu-id="07bb6-112">**Ücretsiz ve açık** – tüm yapıtlar, geliştiricilerin GRPC 'yi benimsemelerine kısıtlama gerektirmeyen lisanslama ile açık kaynak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07bb6-112">**Free and open** – all artifacts should be open source with licensing that doesn't constrain developers from adopting gRPC.</span></span>
- <span data-ttu-id="07bb6-113">**Kapsam ve basitlik** – GRPC, tüm popüler platformlarda kullanılabilir ve her platformda derlemek için yeterince kolay olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07bb6-113">**Coverage and simplicity** – gRPC should be available across every popular platform and simple enough to build on any platform.</span></span>
- <span data-ttu-id="07bb6-114">**Birlikte çalışabilirlik ve erişim** – bant genişliği veya gecikme süresi ne olursa olsun, geniş kullanılabilir ağ standartları kullanılarak GRPC 'yi herhangi bir ağda kullanmak mümkün olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07bb6-114">**Interoperability and reach** – it should be possible to use gRPC on any network, regardless of bandwidth or latency, using widely available network standards.</span></span>
- <span data-ttu-id="07bb6-115">**Genel amaçlı ve** performans: Framework, performansa ödün vermeden mümkün olduğunca geniş bir kullanım talebi yelpazaya kadar kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07bb6-115">**General purpose and performant** – the framework should be usable by as broad a range of use-cases as possible without compromising performance.</span></span>
- <span data-ttu-id="07bb6-116">**Akış** : protokol, büyük veri kümeleri veya zaman uyumsuz mesajlaşma için akış semantiğini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="07bb6-116">**Streaming** – the protocol should provide streaming semantics for large data-sets or asynchronous messaging.</span></span>
- <span data-ttu-id="07bb6-117">**Meta veri değişimi** – protokol, kimlik doğrulama belirteçleri gibi iş dışı verilerin gerçek iş verilerinden ayrı olarak işlenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="07bb6-117">**Metadata exchange** – the protocol allow non-business data, such as authentication tokens, to be handled separately from actual business data.</span></span>
- <span data-ttu-id="07bb6-118">**Standartlaştırılmış durum kodları** : hata işleme kararlarını daha net hale getirmek ve ek daha zengin hata işleme gerekliyse, bunu meta veri değişimi içinde yönetmek için bir mekanizma sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07bb6-118">**Standardized status codes** – the variability of error codes should be reduced to make error handling decisions clearer and, where additional richer error handling is required, a mechanism should be provided for managing this within the metadata exchange.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="07bb6-119">[Önceki](introduction.md)
>[İleri](approach.md)</span><span class="sxs-lookup"><span data-stu-id="07bb6-119">[Previous](introduction.md)
[Next](approach.md)</span></span>

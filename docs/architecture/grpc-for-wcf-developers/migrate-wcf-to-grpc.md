---
title: WCF geliştiricileri için bir WCF çözümünü gRPC-gRPC 'ye geçirme
description: Farklı türlerde WCF Hizmetleri gRPC 'de eşdeğerine nasıl geçirilir.
ms.date: 12/15/2020
ms.openlocfilehash: 3bd35cb6119368ff3db3be9ab5fabf89f2652b29
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937967"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="9b945-103">WCF çözümünü gRPC'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="9b945-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="9b945-104">Bu bölümde, ASP.NET Core 5,0 gRPC projeleriyle nasıl çalışılacağı ve farklı türlerde Windows Communication Foundation (WCF) Hizmetleri gRPC eşdeğerine nasıl geçirilerek anlatılmaktadır:</span><span class="sxs-lookup"><span data-stu-id="9b945-104">This chapter will describe how to work with ASP.NET Core 5.0 gRPC projects and demonstrate migrating different types of Windows Communication Foundation (WCF) services to the gRPC equivalent:</span></span>

- <span data-ttu-id="9b945-105">ASP.NET Core 5,0 gRPC projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9b945-105">Create an ASP.NET Core 5.0 gRPC project.</span></span>
- <span data-ttu-id="9b945-106">Basit istek-gRPC birli RPC 'ye yönelik yanıt verme işlemleri.</span><span class="sxs-lookup"><span data-stu-id="9b945-106">Simple request-reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="9b945-107">GRPC istemci akışı RPC 'ye tek yönlü işlemler.</span><span class="sxs-lookup"><span data-stu-id="9b945-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="9b945-108">GRPC çift yönlü akış RPC 'ye tam çift yönlü hizmetler.</span><span class="sxs-lookup"><span data-stu-id="9b945-108">Full-duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="9b945-109">Ayrıca, veri kümelerini döndürmek için tekrarlanan alanlar ve akış Hizmetleri kullanmanın bir karşılaştırması vardır ve bu, bölümün sonunda istemci kitaplıklarının kullanımıyla ilgili bir tartışmadır.</span><span class="sxs-lookup"><span data-stu-id="9b945-109">There's also a comparison of using streaming services versus repeated fields for returning datasets, and there's a discussion of the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="9b945-110">Örnek WCF uygulaması, bir hisse senedi Hizmetleri kümesinin en az bir saplama örneğidir.</span><span class="sxs-lookup"><span data-stu-id="9b945-110">The sample WCF application is a minimal stub of a set of stock trading services.</span></span> <span data-ttu-id="9b945-111">Bağımlılık ekleme için Autofac adlı açık kaynaklı denetim (IOC) kapsayıcı kitaplığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b945-111">It uses the open-source Inversion of Control (IoC) container library called Autofac for dependency injection.</span></span> <span data-ttu-id="9b945-112">Her WCF hizmet türü için bir tane olmak üzere üç hizmet içerir.</span><span class="sxs-lookup"><span data-stu-id="9b945-112">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="9b945-113">Hizmetler aşağıdaki bölümlerde daha ayrıntılı bir şekilde ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="9b945-113">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="9b945-114">GitHub 'da, [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) çözümlerini yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b945-114">You can download the solutions from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="9b945-115">Hizmetler, dış bağımlılıkları en aza indirmek için sahte veriler kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b945-115">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="9b945-116">Örnekler, her bir hizmetin WCF ve gRPC uygulamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9b945-116">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9b945-117">[Önceki](ws-protocols.md) 
> [Sonraki](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="9b945-117">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>

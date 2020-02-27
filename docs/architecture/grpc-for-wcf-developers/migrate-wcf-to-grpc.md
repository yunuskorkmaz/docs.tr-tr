---
title: WCF geliştiricileri için bir WCF çözümünü gRPC-gRPC 'ye geçirme
description: Farklı türlerde WCF Hizmetleri gRPC 'de eşdeğerine nasıl geçirilir.
ms.date: 09/02/2019
ms.openlocfilehash: 12e724ab46a33547d352da7a604a5a994e617bc2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628520"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="b1c09-103">WCF çözümünü gRPC'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="b1c09-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="b1c09-104">Bu bölümde, ASP.NET Core 3,0 gRPC projeleriyle nasıl çalışılacağı ve farklı türlerde Windows Communication Foundation (WCF) Hizmetleri gRPC eşdeğerine nasıl geçirilerek anlatılmaktadır:</span><span class="sxs-lookup"><span data-stu-id="b1c09-104">This chapter will describe how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of Windows Communication Foundation (WCF) services to the gRPC equivalent:</span></span>

- <span data-ttu-id="b1c09-105">ASP.NET Core 3,0 gRPC projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1c09-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="b1c09-106">Basit istek-gRPC birli RPC 'ye yönelik yanıt verme işlemleri.</span><span class="sxs-lookup"><span data-stu-id="b1c09-106">Simple request-reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="b1c09-107">GRPC istemci akışı RPC 'ye tek yönlü işlemler.</span><span class="sxs-lookup"><span data-stu-id="b1c09-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="b1c09-108">GRPC çift yönlü akış RPC 'ye tam çift yönlü hizmetler.</span><span class="sxs-lookup"><span data-stu-id="b1c09-108">Full-duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="b1c09-109">Ayrıca, veri kümelerini döndürmek için tekrarlanan alanlar ve akış Hizmetleri kullanmanın bir karşılaştırması vardır ve bu, bölümün sonunda istemci kitaplıklarının kullanımıyla ilgili bir tartışmadır.</span><span class="sxs-lookup"><span data-stu-id="b1c09-109">There's also a comparison of using streaming services versus repeated fields for returning datasets, and there's a discussion of the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="b1c09-110">Örnek WCF uygulaması, bir hisse senedi Hizmetleri kümesinin en az bir saplama örneğidir.</span><span class="sxs-lookup"><span data-stu-id="b1c09-110">The sample WCF application is a minimal stub of a set of stock trading services.</span></span> <span data-ttu-id="b1c09-111">Bağımlılık ekleme için Autofac adlı açık kaynaklı denetim (IOC) kapsayıcı kitaplığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1c09-111">It uses the open-source Inversion of Control (IoC) container library called Autofac for dependency injection.</span></span> <span data-ttu-id="b1c09-112">Her WCF hizmet türü için bir tane olmak üzere üç hizmet içerir.</span><span class="sxs-lookup"><span data-stu-id="b1c09-112">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="b1c09-113">Hizmetler aşağıdaki bölümlerde daha ayrıntılı bir şekilde ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="b1c09-113">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="b1c09-114">GitHub 'da, [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) çözümlerini yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1c09-114">You can download the solutions from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="b1c09-115">Hizmetler, dış bağımlılıkları en aza indirmek için sahte veriler kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1c09-115">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="b1c09-116">Örnekler, her bir hizmetin WCF ve gRPC uygulamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b1c09-116">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b1c09-117">[Önceki](ws-protocols.md)
>[İleri](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="b1c09-117">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>

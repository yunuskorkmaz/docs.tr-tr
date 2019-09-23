---
title: WCF geliştiricileri için bir WCF çözümünü gRPC-gRPC 'ye geçirme
description: Farklı türlerde WCF hizmetini gRPC 'de eşdeğerine geçirme.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a9cfb87361194d998a3c4dfff4fe434be64f0d65
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184297"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="cbd43-103">WCF çözümünü gRPC 'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="cbd43-103">Migrate a WCF solution to gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="cbd43-104">Bu bölümde, ASP.NET Core 3,0 gRPC projeleriyle nasıl çalışılacağı ve farklı türlerde WCF hizmetinin gRPC eşdeğerine geçirilmesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cbd43-104">This chapter will look at how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of WCF service to the gRPC equivalent:</span></span>

- <span data-ttu-id="cbd43-105">ASP.NET Core 3,0 gRPC projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cbd43-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="cbd43-106">Basit Istek-gRPC birli RPC 'ye yönelik yanıt verme işlemleri.</span><span class="sxs-lookup"><span data-stu-id="cbd43-106">Simple Request-Reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="cbd43-107">GRPC istemci akışı RPC 'ye tek yönlü işlemler.</span><span class="sxs-lookup"><span data-stu-id="cbd43-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="cbd43-108">GRPC çift yönlü akış RPC 'ye tam çift yönlü hizmetler.</span><span class="sxs-lookup"><span data-stu-id="cbd43-108">Full Duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="cbd43-109">Ayrıca, veri kümelerinin döndürülmesi için yinelenen alanlar ve Bölüm sonundaki istemci kitaplıklarının kullanımı gibi akış Hizmetleri kullanmanın bir karşılaştırması de vardır.</span><span class="sxs-lookup"><span data-stu-id="cbd43-109">There's also a comparison of using streaming services versus repeated fields for returning data sets, and the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="cbd43-110">Örnek WCF uygulaması, bağımlılık ekleme için *Autofac* adlı, açık kaynaklı denetim (IOC) kapsayıcı kitaplığının kullanıldığı bir hisse senedi Hizmetleri kümesinin en az bir saplaması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="cbd43-110">The sample WCF application is a minimal stub of a set of stock trading services, using the open-source Inversion of Control (IoC) container library called *Autofac* for dependency injection.</span></span> <span data-ttu-id="cbd43-111">Her WCF hizmet türü için bir tane olmak üzere üç hizmet içerir.</span><span class="sxs-lookup"><span data-stu-id="cbd43-111">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="cbd43-112">Hizmetler aşağıdaki bölümlerde daha ayrıntılı bir şekilde ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="cbd43-112">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="cbd43-113">Çözümler, GitHub 'daki [Rendlelabs/GRPC-for-WCF-geliştiricilerinden](https://github.com/dotnet-architecture/grpc-for-wcf-developers) indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cbd43-113">The solutions can be downloaded from [RendleLabs/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="cbd43-114">Hizmetler, dış bağımlılıkları en aza indirmek için sahte veriler kullanır.</span><span class="sxs-lookup"><span data-stu-id="cbd43-114">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="cbd43-115">Örnekler, her bir hizmetin WCF ve gRPC uygulamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cbd43-115">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cbd43-116">[Önceki](ws-protocols.md)
>[İleri](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="cbd43-116">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>

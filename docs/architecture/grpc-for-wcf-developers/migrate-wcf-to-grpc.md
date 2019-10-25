---
title: WCF geliştiricileri için bir WCF çözümünü gRPC-gRPC 'ye geçirme
description: Farklı türlerde WCF hizmetini gRPC 'de eşdeğerine geçirme.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 65c30b777d9981cb3291b846f698f2a69b4498fc
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846597"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="5e3ca-103">WCF çözümünü gRPC'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="5e3ca-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="5e3ca-104">Bu bölümde, ASP.NET Core 3,0 gRPC projeleriyle nasıl çalışılacağı ve farklı türlerde WCF hizmetinin gRPC eşdeğerine geçirilmesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5e3ca-104">This chapter will look at how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of WCF service to the gRPC equivalent:</span></span>

- <span data-ttu-id="5e3ca-105">ASP.NET Core 3,0 gRPC projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="5e3ca-106">Basit Istek-gRPC birli RPC 'ye yönelik yanıt verme işlemleri.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-106">Simple Request-Reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="5e3ca-107">GRPC istemci akışı RPC 'ye tek yönlü işlemler.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="5e3ca-108">GRPC çift yönlü akış RPC 'ye tam çift yönlü hizmetler.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-108">Full Duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="5e3ca-109">Ayrıca, veri kümelerinin döndürülmesi için yinelenen alanlar ve Bölüm sonundaki istemci kitaplıklarının kullanımı gibi akış Hizmetleri kullanmanın bir karşılaştırması de vardır.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-109">There's also a comparison of using streaming services versus repeated fields for returning data sets, and the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="5e3ca-110">Örnek WCF uygulaması, bağımlılık ekleme için *Autofac* adlı, açık kaynaklı denetim (IOC) kapsayıcı kitaplığının kullanıldığı bir hisse senedi Hizmetleri kümesinin en az bir saplaması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-110">The sample WCF application is a minimal stub of a set of stock trading services, using the open-source Inversion of Control (IoC) container library called *Autofac* for dependency injection.</span></span> <span data-ttu-id="5e3ca-111">Her WCF hizmet türü için bir tane olmak üzere üç hizmet içerir.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-111">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="5e3ca-112">Hizmetler aşağıdaki bölümlerde daha ayrıntılı bir şekilde ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-112">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="5e3ca-113">Çözümler, GitHub 'da [DotNet-Architecture/GRPC-for-WCF-geliştiricilerinden](https://github.com/dotnet-architecture/grpc-for-wcf-developers) indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-113">The solutions can be downloaded from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="5e3ca-114">Hizmetler, dış bağımlılıkları en aza indirmek için sahte veriler kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-114">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="5e3ca-115">Örnekler, her bir hizmetin WCF ve gRPC uygulamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5e3ca-115">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5e3ca-116">[Önceki](ws-protocols.md)
>[İleri](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="5e3ca-116">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>

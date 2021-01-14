---
title: .NET için Azure SDK genel bakış
description: .NET için Azure SDK 'nın ne olduğuna ve bir .NET uygulamasında SDK 'Yı kullanmak için temel adımlara genel bakış sağlar
ms.date: 11/30/2020
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: b547e105b13d380ffae049ab55e76aa25abe8cc3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189206"
---
# <a name="azure-sdk-for-net-overview"></a><span data-ttu-id="f27a3-103">.NET için Azure SDK genel bakış</span><span class="sxs-lookup"><span data-stu-id="f27a3-103">Azure SDK for .NET overview</span></span>

## <a name="what-is-the-azure-sdk-for-net"></a><span data-ttu-id="f27a3-104">.NET için Azure SDK nedir?</span><span class="sxs-lookup"><span data-stu-id="f27a3-104">What is the Azure SDK for .NET</span></span>

<span data-ttu-id="f27a3-105">**.Net Için Azure SDK** , .NET uygulamalarınızdan Azure hizmetlerini kullanmayı kolaylaştırmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f27a3-105">The **Azure SDK for .NET** is designed to make it easy to use Azure services from your .NET applications.</span></span>  <span data-ttu-id="f27a3-106">.NET için Azure SDK, Azure hizmetlerine erişmek için tutarlı ve tanıdık bir arabirim sağlar ve BLOB depolamaya dosya yükleme ve indirme, uygulama gizli dizileri Azure Key Vault veya Azure Event Hubs arasındaki bildirimleri işleme olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="f27a3-106">Whether it is uploading and downloading files to Blob Storage, retrieving application secrets from Azure Key Vault, or processing notifications from Azure Event Hubs, the Azure SDK for .NET provides a consistent and familiar interface to access Azure services.</span></span>  

<span data-ttu-id="f27a3-107">.NET için Azure SDK, hem .NET Core (2,1 ve üzeri) hem de .NET Framework (4.6.1 ve üzeri) uygulamalarda kullanılabilen NuGet paketleri serisi olarak sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f27a3-107">The Azure SDK for .NET is available as series of NuGet packages that can be used in both .NET Core (2.1 and higher) and .NET Framework (4.6.1 and higher) applications.</span></span>

![.NET uygulamalarının Azure hizmetlerine erişmek için Azure SDK 'sını nasıl kullandığını gösteren diyagram](./media/azure-sdk-for-dotnet-overview.png)

## <a name="use-the-azure-sdk-for-net-in-your-applications"></a><span data-ttu-id="f27a3-109">Uygulamalarınızda .NET için Azure SDK 'sını kullanın</span><span class="sxs-lookup"><span data-stu-id="f27a3-109">Use the Azure SDK for .NET in your applications</span></span>

<span data-ttu-id="f27a3-110">.NET uygulamalarınızdan birinde bir Azure SDK paketi kullanmak için, bu adımları takip etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f27a3-110">To use an Azure SDK package in one of your .NET applications, you want to follow these steps.</span></span>

1. <span data-ttu-id="f27a3-111">**Uygun SDK paketini bulun-** Üzerinde çalıştığınız Azure hizmetine uygun paketi bulmak için [paket listesini](../packages.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f27a3-111">**Locate the appropriate SDK package -** Use the [package list](../packages.md) to find the appropriate package for the Azure service you are working with.</span></span>  <span data-ttu-id="f27a3-112">Çoğu hizmetin, hizmet ile birlikte çalışmak için bir istemci paketi ve hizmet örnekleri oluşturma ve yönetme için bir yönetim paketi olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="f27a3-112">Be advised that most services have a client package for working with the service and a management package for creating and managing instances of the service.</span></span>  <span data-ttu-id="f27a3-113">Çoğu durumda, istemci paketini tercih edersiniz.</span><span class="sxs-lookup"><span data-stu-id="f27a3-113">In most cases, you will want the client package.</span></span>  <span data-ttu-id="f27a3-114">Bu paketi, NuGet kullanarak uygulamanıza yükler.</span><span class="sxs-lookup"><span data-stu-id="f27a3-114">Install this package in your application using NuGet.</span></span>

2. <span data-ttu-id="f27a3-115">**Uygulamanız için kimlik doğrulamasını ayarlama-** Azure kaynaklarına erişmek için uygulamanızın Azure 'da atanmış uygun kimlik bilgilerine ve erişim haklarına sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f27a3-115">**Set up authentication for your application -** To access Azure resources, your application will need to have the appropriate credentials and access rights assigned in Azure.</span></span>  <span data-ttu-id="f27a3-116">[.NET uygulamalarının](../authentication.md)kimlik doğrulamasını Azure 'da nasıl yapılandıracağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="f27a3-116">Learn how to configure authentication in [Authenticating .NET applications to Azure](../authentication.md).</span></span>

3. <span data-ttu-id="f27a3-117">**Uygulamanızdaki SDK 'yı kullanarak kod yazın-** Azure hizmetleriyle çalışırken kodunuz, önce hizmetle birlikte çalışmak üzere bir istemci nesnesi oluşturur ve sonra hizmetle etkileşimde bulunmak için bu istemci nesnesi üzerinde Yöntemler çağırır.</span><span class="sxs-lookup"><span data-stu-id="f27a3-117">**Write code using the SDK in your application -** When working with Azure services, your code will first create a client object to work with the service and then call methods on that client object to interact with the service.</span></span>  <span data-ttu-id="f27a3-118">Hem zaman uyumlu hem de zaman uyumsuz yöntemler sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f27a3-118">Both synchronous and asynchronous methods are provided.</span></span>  <span data-ttu-id="f27a3-119">Her bir SDK paketinin kullanılmasıyla ilgili örnekler, Azure belgelerinin tamamında sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f27a3-119">Examples of using each individual SDK package are provided throughout the Azure documentation.</span></span>

4. <span data-ttu-id="f27a3-120">**SDK için günlüğü yapılandırma (isteğe bağlı)-** Uygulamanız ile Azure arasındaki sorunları tanılamanıza gerek duyuyorsanız, [.net Için Azure SDK 'da günlüğü etkinleştirebilirsiniz](../logging.md).</span><span class="sxs-lookup"><span data-stu-id="f27a3-120">**Configure logging for the SDK (optional) -** If you need to diagnose issues between your application and Azure, you can [enable logging in the Azure SDK for .NET](../logging.md).</span></span>

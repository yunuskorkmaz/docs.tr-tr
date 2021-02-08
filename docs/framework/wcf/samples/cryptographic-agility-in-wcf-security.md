---
description: 'Daha fazla bilgi edinin: WCF güvenliğine yönelik şifreleme çevikliği'
title: WCF güvenliğine ilişkin şifreleme çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: ab46034b16a846f7399220480fc928655d931be0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778353"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="5f6c9-103">WCF güvenliğine ilişkin şifreleme çevikliği</span><span class="sxs-lookup"><span data-stu-id="5f6c9-103">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="5f6c9-104">Bu örnek, bir Windows Communication Foundation (WCF) istemcisinde ve hizmetinde şifreli çevik uygulama sağlamak için standart/özel algoritmada nasıl belirtme gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-104">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="5f6c9-105">Örnek, aşağıdaki projelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="5f6c9-105">The sample is composed of the following projects:</span></span>

<span data-ttu-id="5f6c9-106">**Hizmet**</span><span class="sxs-lookup"><span data-stu-id="5f6c9-106">**Service**</span></span>

<span data-ttu-id="5f6c9-107">Bu, `ICalculator` arabirimini uygulayan ve <xref:System.ServiceModel.WSHttpBinding> güvenli oturum ve güvenilir oturumu devre dışı olarak kullanarak uç noktanın güvenliğini sağlayan, şirket içinde BARıNDıRıLAN bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-107">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="5f6c9-108">Hizmet, `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirtmek için özel bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-108">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="5f6c9-109">**İstemci**</span><span class="sxs-lookup"><span data-stu-id="5f6c9-109">**Client**</span></span>

<span data-ttu-id="5f6c9-110">Bu, başarılı kimlik doğrulamasından sonra hizmete erişen bir WCF istemcsahiptir.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-110">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="5f6c9-111">Arabirim tarafından sunulan `ICalculator` ve hizmet tarafından uygulanan işlemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-111">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="5f6c9-112">İstemci Ayrıca, `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirtmek için aynı özel sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-112">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="5f6c9-113">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="5f6c9-113">To use this sample</span></span>

1. <span data-ttu-id="5f6c9-114">Visual Studio 2012 ' de Cryptoçeviklik. sln çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-114">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="5f6c9-115">Çözümü derlemek için CTRL+SHIFT+B'ye basın.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-115">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="5f6c9-116">Dosya Gezgini 'ni açın ve \WCF\Basic\Security\CryptoAgility\Service\bin dizinine gidin ve service.exe sağ tıklayıp **yönetici olarak çalıştır**' ı seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-116">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="5f6c9-117">\WCF\Basic\Security\CryptoAgility\Client\bin dizinine gidin ve client.exe dosyasını normal şekilde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-117">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f6c9-118">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f6c9-119">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5f6c9-120">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5f6c9-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f6c9-121">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="5f6c9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f6c9-122">See also</span></span>

- [<span data-ttu-id="5f6c9-123">Windows Communication Foundation Güvenliği</span><span class="sxs-lookup"><span data-stu-id="5f6c9-123">Windows Communication Foundation Security</span></span>](../feature-details/security.md)

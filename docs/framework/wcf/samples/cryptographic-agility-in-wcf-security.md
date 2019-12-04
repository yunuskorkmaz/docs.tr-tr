---
title: WCF güvenliğine ilişkin şifreleme çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714932"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="24c4a-102">WCF güvenliğine ilişkin şifreleme çevikliği</span><span class="sxs-lookup"><span data-stu-id="24c4a-102">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="24c4a-103">Bu örnek, bir Windows Communication Foundation (WCF) istemcisinde ve hizmetinde şifreli çevik uygulama sağlamak için standart/özel algoritmada nasıl belirtme gösterir.</span><span class="sxs-lookup"><span data-stu-id="24c4a-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="24c4a-104">Örnek, aşağıdaki projelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="24c4a-104">The sample is composed of the following projects:</span></span>

<span data-ttu-id="24c4a-105">**Hizmet**</span><span class="sxs-lookup"><span data-stu-id="24c4a-105">**Service**</span></span>

<span data-ttu-id="24c4a-106">Bu, `ICalculator` arabirimini uygulayan ve güvenli oturum ve güvenilir oturum devre dışı bırakılmış <xref:System.ServiceModel.WSHttpBinding> kullanarak uç noktanın güvenliğini sağlayan, şirket içinde barındırılan bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="24c4a-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="24c4a-107">Hizmet, ileti güvenliği için kullanılacak şifreleme algoritmalarını belirtmek için özel bir `SecurityAlgorithmSuite` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24c4a-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="24c4a-108">**İstemci**</span><span class="sxs-lookup"><span data-stu-id="24c4a-108">**Client**</span></span>

<span data-ttu-id="24c4a-109">Bu, başarılı kimlik doğrulamasından sonra hizmete erişen bir WCF istemcsahiptir.</span><span class="sxs-lookup"><span data-stu-id="24c4a-109">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="24c4a-110">`ICalculator` arabirimi tarafından sunulan ve hizmet tarafından uygulanan işlemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="24c4a-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="24c4a-111">İstemci Ayrıca, ileti güvenliği için kullanılacak şifreleme algoritmalarını belirtmek için aynı özel `SecurityAlgorithmSuite` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24c4a-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="24c4a-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="24c4a-112">To use this sample</span></span>

1. <span data-ttu-id="24c4a-113">Visual Studio 2012 ' de Cryptoçeviklik. sln çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="24c4a-113">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="24c4a-114">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="24c4a-114">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="24c4a-115">Dosya Gezgini 'ni açın ve \WCF\Basic\Security\CryptoAgility\Service\bin dizinine gidin ve Service. exe dosyasını sağ tıklayıp yönetici **olarak çalıştır**' ı seçerek yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="24c4a-115">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="24c4a-116">\WCF\Basic\Security\CryptoAgility\Client\bin dizinine gidin ve Client. exe dosyasını normal olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="24c4a-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24c4a-117">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="24c4a-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="24c4a-118">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="24c4a-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="24c4a-119">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="24c4a-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24c4a-120">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="24c4a-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="24c4a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24c4a-121">See also</span></span>

- [<span data-ttu-id="24c4a-122">Windows Communication Foundation güvenliği</span><span class="sxs-lookup"><span data-stu-id="24c4a-122">Windows Communication Foundation Security</span></span>](../feature-details/security.md)

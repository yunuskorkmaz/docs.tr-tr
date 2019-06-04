---
title: WCF güvenliğinde şifreleme çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: b8e3b6dc62baf31901520d7f5edac0529e937016
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490945"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="338eb-102">WCF güvenliğinde şifreleme çevikliği</span><span class="sxs-lookup"><span data-stu-id="338eb-102">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="338eb-103">Bu örnek, bir Windows Communication Foundation (WCF) istemci ve hizmet şifreleme ve Çevik bir uygulama sağlamak için bir standart/özel algoritması belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="338eb-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="338eb-104">Örnek, aşağıdaki projelerin oluşur:</span><span class="sxs-lookup"><span data-stu-id="338eb-104">The sample is composed of the following projects:</span></span>

<span data-ttu-id="338eb-105">**Hizmet**</span><span class="sxs-lookup"><span data-stu-id="338eb-105">**Service**</span></span>

<span data-ttu-id="338eb-106">Bu uygulayan şirket içinde barındırılan bir WCF hizmeti, `ICalculator` arabirim ve uç noktayı kullanarak korur <xref:System.ServiceModel.WSHttpBinding> güvenli oturum ve güvenilir oturum devre dışı.</span><span class="sxs-lookup"><span data-stu-id="338eb-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="338eb-107">Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="338eb-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="338eb-108">**İstemci**</span><span class="sxs-lookup"><span data-stu-id="338eb-108">**Client**</span></span>

<span data-ttu-id="338eb-109">Başarılı kimlik doğrulamasından sonra hizmete erişen bir WCF istemcisi budur.</span><span class="sxs-lookup"><span data-stu-id="338eb-109">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="338eb-110">Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="338eb-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="338eb-111">İstemci Ayrıca, aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="338eb-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="338eb-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="338eb-112">To use this sample</span></span>

1. <span data-ttu-id="338eb-113">Visual Studio 2012'de CryptoAgility.sln çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="338eb-113">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="338eb-114">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="338eb-114">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="338eb-115">Dosya Gezgini'ni açın ve \WCF\Basic\Security\CryptoAgility\Service\bin dizine gidin ve service.exe sağ tıklatıp seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="338eb-115">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="338eb-116">\WCF\Basic\Security\CryptoAgility\Client\bin dizine gidin ve normalde client.exe dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="338eb-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="338eb-117">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="338eb-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="338eb-118">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="338eb-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="338eb-119">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="338eb-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="338eb-120">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="338eb-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="338eb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="338eb-121">See also</span></span>

- [<span data-ttu-id="338eb-122">Windows Communication Foundation güvenliği</span><span class="sxs-lookup"><span data-stu-id="338eb-122">Windows Communication Foundation Security</span></span>](../feature-details/security.md)

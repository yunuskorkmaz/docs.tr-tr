---
title: İş Akışı Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b3a2d88028f3854746d4e1d2fad80aae4f6be7be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143492"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="53367-102">İş Akışı Keşif Örneği</span><span class="sxs-lookup"><span data-stu-id="53367-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="53367-103">Bu örnek, bir iş akışı hizmetinin nasıl keşfedilebilir hale getirilebildiğini ve belirli bir hizmeti arayan özel bir kod etkinliğinin nasıl yazılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="53367-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="53367-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="53367-104">Demonstrates</span></span>  
 <span data-ttu-id="53367-105">Bulma Bulma Etkinliği ve İş Akışı Kullanımı</span><span class="sxs-lookup"><span data-stu-id="53367-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="53367-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="53367-106">Discussion</span></span>  
 <span data-ttu-id="53367-107">Örneğin ilk bölümünde, bir iş akışı hizmeti yapılandırma kullanılarak keşfedilebilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="53367-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="53367-108">Yapılandırma, hizmeti özel meta verilerle (kapsamlar gibi) uygun şekilde uygulamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53367-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="53367-109">İstemci de, örnek belirli bir sözleşme eşleşen bir hizmet aramak için Discovery kullanan özel bir kod etkinliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="53367-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="53367-110">Kod etkinliği, daha sonra bir gönderme etkinliği tarafından kullanılan bir URI çıktırıyor.</span><span class="sxs-lookup"><span data-stu-id="53367-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="53367-111">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="53367-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="53367-112">Bu örnek, çalıştırmak için uygun URL ALA'larına sahip olması gereken HTTP uç noktalarını kullanır (ayrıntılar için [HTTP ve HTTPS'yi yapılandırmaya](../feature-details/configuring-http-and-https.md) bakın).</span><span class="sxs-lookup"><span data-stu-id="53367-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="53367-113">Aşağıdaki komutu yükseltilmiş bir komut isteminde yürütme uygun ALA'ları eklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="53367-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="53367-114">Kabuğunuz değişken biçimini anlamıyorsa, Etki Alanı nızı ve Kullanıcı Adınızı aşağıdaki bağımsız değişkenler için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="53367-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
     <span data-ttu-id="53367-115">**netsh http urlaclhttp://+:8000/ url ekle=\\kullanıcı=%DOMAIN% %UserName%**</span><span class="sxs-lookup"><span data-stu-id="53367-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="53367-116">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="53367-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="53367-117">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="53367-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="53367-118">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="53367-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="53367-119">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="53367-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`

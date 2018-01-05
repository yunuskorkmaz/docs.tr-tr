---
title: Meta veri deposu ile programlama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b8bfce17169a1095d2d2817467fcc8f3366ead3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="1e375-102">Meta veri deposu ile programlama</span><span class="sxs-lookup"><span data-stu-id="1e375-102">Metadata Store Programmability</span></span>
<span data-ttu-id="1e375-103">Meta veri deposu bir [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] CLR öznitelikleri biçiminde rasgele meta verileri ilişkilendirme için olanak tanıyan özelliği çalışma zamanında türleri.</span><span class="sxs-lookup"><span data-stu-id="1e375-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="1e375-104">Bu çalışma zamanı bileşenleri ve tasarım zamanı dekiler yanı sıra, çalışma zamanı etkilemeden tasarım zamanı bileşenleri değiştirme yeteneğini arasında gevşek bir bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e375-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="1e375-105">Örnek, bir çalışma zamanı türü için hiçbir denetim üzerinden sahibiz kaynak özniteliklerini uygulayarak karşı meta veri deposu program gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e375-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="1e375-106">Genellikle kullanılan terminolojiyi barındırma uygulama türleri kümesi için meta verileri kaydeder ' dir.</span><span class="sxs-lookup"><span data-stu-id="1e375-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="1e375-107">Çıktısı bir ek, beklenmeyen öznitelik karşılaşabilirsiniz <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1e375-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="1e375-108">Bu meta verileri API'si kullanılırken eklenir ve örnek çalışan üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="1e375-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="1e375-109">Bu örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1e375-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1e375-110">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="1e375-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="1e375-111">Meta verileri kullanarak özniteliği ekleme API depolar.</span><span class="sxs-lookup"><span data-stu-id="1e375-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="1e375-112">Meta veri kaydı ertelemek için bir geri dönüş mekanizması kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="1e375-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1e375-113">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="1e375-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1e375-114">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ProgrammingMetadataStore.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1e375-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="1e375-115">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e375-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1e375-116">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e375-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e375-117">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e375-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1e375-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1e375-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1e375-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1e375-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1e375-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1e375-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`
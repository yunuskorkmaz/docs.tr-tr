---
title: Meta veri Store programlama
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 4ea6117686b985a9ea18ce4e5cc4ea2b5c25524c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881430"
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="b5808-102">Meta veri Store programlama</span><span class="sxs-lookup"><span data-stu-id="b5808-102">Metadata Store Programmability</span></span>
<span data-ttu-id="b5808-103">Meta veri deposu bir [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] türlerini çalışma zamanında CLR öznitelikleri biçiminde rastgele meta veriler ilişkisini olanak tanıyan özellik.</span><span class="sxs-lookup"><span data-stu-id="b5808-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="b5808-104">Bu çalışma zamanı bileşenlerini ve tasarım zamanı karşılıkları yanı sıra, çalışma zamanı etkilemeden tasarım saati bileşenlerini değiştirme olanağı arasında gevşek bir bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5808-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="b5808-105">Örnek, bir çalışma zamanı türü, biz denetimi içinde olan kaynak öznitelikleri uygulayarak meta veri deposuna karşı programlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b5808-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="b5808-106">Genellikle kullanılan terimler, barındırma uygulaması türleri kümesi için meta verileri kaydeder ' dir.</span><span class="sxs-lookup"><span data-stu-id="b5808-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="b5808-107">Çıktısı, beklenmeyen ek bir öznitelik fark edebilirsiniz <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="b5808-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="b5808-108">Bu meta veri API'si kullanılırken eklenir ve örnek çalışmasını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="b5808-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="b5808-109">Bu örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="b5808-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b5808-110">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="b5808-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="b5808-111">Öznitelik ekleme meta verileri kullanarak API depolayın.</span><span class="sxs-lookup"><span data-stu-id="b5808-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="b5808-112">Meta veri kaydı ertelemek için bir geri dönüş mekanizması kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="b5808-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b5808-113">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b5808-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b5808-114">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ProgrammingMetadataStore.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b5808-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b5808-115">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="b5808-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b5808-116">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b5808-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b5808-117">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="b5808-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5808-118">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b5808-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b5808-119">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b5808-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5808-120">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b5808-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`
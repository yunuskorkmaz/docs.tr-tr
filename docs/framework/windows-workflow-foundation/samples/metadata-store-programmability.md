---
title: Meta veri deposu ile programlama
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 6efcb86e29f19a29d6ef382afa336d0ca2ce4306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517443"
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="1164a-102">Meta veri deposu ile programlama</span><span class="sxs-lookup"><span data-stu-id="1164a-102">Metadata Store Programmability</span></span>
<span data-ttu-id="1164a-103">Meta veri deposu bir [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] CLR öznitelikleri biçiminde rasgele meta verileri ilişkilendirme için olanak tanıyan özelliği çalışma zamanında türleri.</span><span class="sxs-lookup"><span data-stu-id="1164a-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="1164a-104">Bu çalışma zamanı bileşenleri ve tasarım zamanı dekiler yanı sıra, çalışma zamanı etkilemeden tasarım zamanı bileşenleri değiştirme yeteneğini arasında gevşek bir bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1164a-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="1164a-105">Örnek, bir çalışma zamanı türü için hiçbir denetim üzerinden sahibiz kaynak özniteliklerini uygulayarak karşı meta veri deposu program gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1164a-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="1164a-106">Genellikle kullanılan terminolojiyi barındırma uygulama türleri kümesi için meta verileri kaydeder ' dir.</span><span class="sxs-lookup"><span data-stu-id="1164a-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="1164a-107">Çıktısı bir ek, beklenmeyen öznitelik karşılaşabilirsiniz <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1164a-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="1164a-108">Bu meta verileri API'si kullanılırken eklenir ve örnek çalışan üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="1164a-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="1164a-109">Bu örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1164a-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1164a-110">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="1164a-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="1164a-111">Meta verileri kullanarak özniteliği ekleme API depolar.</span><span class="sxs-lookup"><span data-stu-id="1164a-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="1164a-112">Meta veri kaydı ertelemek için bir geri dönüş mekanizması kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="1164a-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1164a-113">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="1164a-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1164a-114">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ProgrammingMetadataStore.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1164a-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="1164a-115">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1164a-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1164a-116">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1164a-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1164a-117">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1164a-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1164a-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1164a-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1164a-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1164a-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1164a-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1164a-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`
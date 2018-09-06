---
title: ByteStream Kodlayıcı
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: cbd4110ecc04923b79d6b910fcf7ab4ca2012680
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855458"
---
# <a name="bytestream-encoder"></a><span data-ttu-id="c3853-102">ByteStream Kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="c3853-102">ByteStream Encoder</span></span>
<span data-ttu-id="c3853-103">Bu örnek nasıl oluşturulacağını gösterir. bir `ByteStreamHttpBinding`, <xref:System.ServiceModel.Channels.Binding> , bayt akışı Kodlayıcı işlevselliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3853-103">This sample demonstrates how to create a `ByteStreamHttpBinding`, a <xref:System.ServiceModel.Channels.Binding> that demonstrates the functionality of the byte stream encoder.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c3853-104">Tartışma</span><span class="sxs-lookup"><span data-stu-id="c3853-104">Discussion</span></span>  
 <span data-ttu-id="c3853-105">Bu örnek, standart bir oluşturma işlemini gösterir <xref:System.ServiceModel.Channels.Binding> standart bağlama öğeleri kullanılarak <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="c3853-105">This sample demonstrates how to create a standard <xref:System.ServiceModel.Channels.Binding> using the standard binding elements <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span> <span data-ttu-id="c3853-106">Bu örnek, bayt akışı Kodlayıcı karşıya yükleme ve bir resim indirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3853-106">This sample shows how to use the byte stream encoder to upload and download an image.</span></span> <span data-ttu-id="c3853-107">Bayt akışı Kodlayıcısı özelliği yalnızca HTTP aktarımı destekler ve güvenilir Mesajlaşma veya güvenlik gibi özellikleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c3853-107">The byte stream encoder feature only supports the HTTP transport and it does not support features such as reliable messaging or security.</span></span> <span data-ttu-id="c3853-108">Yalnızca <xref:System.ServiceModel.Channels.MessageVersion> desteklenir <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3853-108">The only <xref:System.ServiceModel.Channels.MessageVersion> supported is <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3853-109">Bu örnek çalıştırıyorsanız, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] veya [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], çalıştığından emin olun [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükseltilmiş ayrıcalıklara sahip.</span><span class="sxs-lookup"><span data-stu-id="c3853-109">If you are running this sample in [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] or [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ensure that you are running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with elevated privileges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3853-110">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="c3853-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3853-111">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c3853-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3853-112">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c3853-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3853-113">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c3853-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c3853-114">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c3853-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c3853-115">ByteStreamHttpBinding.sln açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3853-115">Open the ByteStreamHttpBinding.sln file in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3853-116">Çözüm Gezgini'nde projeye sağ tıklatıp seçerek ByteStreamHttpBindingServer projeye yeni bir örneğini Başlat **hata ayıklama**, ardından **yeni örnek Başlat** bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="c3853-116">Start a new instance of the ByteStreamHttpBindingServer project by right-clicking the project in the Solution Explorer and selecting **Debug**, and then **Start new instance** from the context menu.</span></span>  
  
3.  <span data-ttu-id="c3853-117">Çözüm Gezgini'nde projeye sağ tıklatıp seçerek ByteStreamHttpBindingClient projeye yeni bir örneğini Başlat **hata ayıklama**, **yeni örnek Başlat** bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="c3853-117">Start a new instance of the ByteStreamHttpBindingClient project by right-clicking the project in the Solution Explorer and selecting **Debug**, **Start new instance** from the context menu.</span></span>

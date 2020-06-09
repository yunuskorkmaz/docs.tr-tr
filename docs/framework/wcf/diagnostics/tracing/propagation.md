---
title: Yayma
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 732ae5cb1ce311b78728f8d5de0fd9102bf32499
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578961"
---
# <a name="propagation"></a><span data-ttu-id="99807-102">Yayma</span><span class="sxs-lookup"><span data-stu-id="99807-102">Propagation</span></span>
<span data-ttu-id="99807-103">Bu konu, Windows Communication Foundation (WCF) izleme modelinde etkinlik yaymayı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="99807-103">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="99807-104">Uç noktalar genelinde etkinlikleri Ilişkilendirmek için yayılmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="99807-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="99807-105">Yayma, kullanıcıya, örneğin bir istek gibi uygulama uç noktaları genelinde aynı işleme birimi için hata izlemelerinin doğrudan bağıntısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="99807-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="99807-106">Aynı işleme birimi için farklı uç noktalara yayılan hatalar, uygulama etki alanları arasında bile aynı etkinlik halinde gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="99807-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="99807-107">Bu, ileti üst bilgilerindeki etkinlik KIMLIĞI yayması aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="99807-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="99807-108">Bu nedenle, sunucuda bir iç hata nedeniyle istemci zaman aşımına uğrarsa, her iki hata da doğrudan bağıntı için aynı etkinlikte görünür.</span><span class="sxs-lookup"><span data-stu-id="99807-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="99807-109">Bunu yapmak için, `ActivityTracing` Önceki örnekte gösterildiği gibi ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="99807-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="99807-110">Ayrıca, `propagateActivity` `System.ServiceModel` tüm uç noktalarında izleme kaynağı için özniteliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="99807-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="99807-111">Etkinlik yayma, WCF 'nin, TLS üzerindeki etkinlik KIMLIĞINI içeren giden iletilere üst bilgi eklemesine neden olan yapılandırılabilir bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="99807-111">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="99807-112">Bunu sunucu tarafındaki izleyen izlemelere ekleyerek, istemci ve sunucu etkinliklerini ilişkilendirebiliriz.</span><span class="sxs-lookup"><span data-stu-id="99807-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="99807-113">Yayma tanımı</span><span class="sxs-lookup"><span data-stu-id="99807-113">Propagation Definition</span></span>  
 <span data-ttu-id="99807-114">Aşağıdaki koşulların tümü geçerliyse, etkinliğin gAId 'si etkinlik N 'ye yayılır.</span><span class="sxs-lookup"><span data-stu-id="99807-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
- <span data-ttu-id="99807-115">N, d nedeniyle oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="99807-115">N is created because of M</span></span>  
  
- <span data-ttu-id="99807-116">E 'nin gAId 'si N olarak bilinir</span><span class="sxs-lookup"><span data-stu-id="99807-116">M’s gAId is known to N</span></span>  
  
- <span data-ttu-id="99807-117">N 'nin gAId 'si, 8 ' in gAId değerine eşit.</span><span class="sxs-lookup"><span data-stu-id="99807-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="99807-118">GAId, aşağıdaki XML şemasında gösterildiği gibi ActivityId ileti üst bilgisi aracılığıyla dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="99807-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="99807-119">Aşağıda ileti üstbilgisinin bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="99807-119">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="99807-120">Yayma ve etkinlik sınırları</span><span class="sxs-lookup"><span data-stu-id="99807-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="99807-121">Etkinlik KIMLIĞI uç noktalar arasında yayıldığında, ileti alıcısı bu (yayılan) etkinlik KIMLIĞIYLE bir başlangıç ve durdurma izlemeleri yayar.</span><span class="sxs-lookup"><span data-stu-id="99807-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="99807-122">Bu nedenle, her bir izleme kaynağından bu gAId ile bir başlatma ve durdurma izlemesi vardır.</span><span class="sxs-lookup"><span data-stu-id="99807-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="99807-123">Uç noktalar aynı işlemden ve aynı izleme kaynağı adını kullanıyorsa aynı şekilde aynı (aynı gAId, aynı izleme kaynağı, aynı işleme) ile birden çok başlatma ve durdurma oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="99807-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="99807-124">Eşitleme</span><span class="sxs-lookup"><span data-stu-id="99807-124">Synchronization</span></span>  
 <span data-ttu-id="99807-125">Olayları farklı makinelerde çalışan uç noktalar arasında senkronize etmek için, ileti içine yayılan ActivityId üstbilgisine bir Bağıntıkimliği eklenir.</span><span class="sxs-lookup"><span data-stu-id="99807-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="99807-126">Araçlar, saat tutarsızlığı olan makineler arasında olayları eşleştirmek için bu KIMLIĞI kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="99807-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="99807-127">Özellikle, hizmet Izleme Görüntüleyicisi Aracı, uç noktalar arasındaki ileti akışlarını göstermek için bu KIMLIĞI kullanır.</span><span class="sxs-lookup"><span data-stu-id="99807-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99807-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99807-128">See also</span></span>

- [<span data-ttu-id="99807-129">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="99807-129">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="99807-130">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma </span><span class="sxs-lookup"><span data-stu-id="99807-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="99807-131">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="99807-131">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="99807-132">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="99807-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)

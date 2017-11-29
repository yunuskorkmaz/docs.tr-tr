---
title: "WMI Sınıfı Başvurusu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ee03f0c567f2b154eaf2e7fdf608b093cfbe2d1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="wmi-class-reference"></a><span data-ttu-id="26315-102">WMI Sınıfı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="26315-102">WMI Class Reference</span></span>
<span data-ttu-id="26315-103">Bu bölüm tarafından sunulan tüm WMI sınıfları listeler [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] WMI sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="26315-103">This section lists all the WMI classes exposed by the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="26315-104">WMI örnekleri erişme</span><span class="sxs-lookup"><span data-stu-id="26315-104">Accessing WMI Instances</span></span>  
 <span data-ttu-id="26315-105">WMI nesnesi Reference içinde listelenen tüm sınıflar doğrudan, hizmet, AppDomain, sözleşme, ServiceAppDomain, ServiceToEndpointAssociation ve uç nokta dışında başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="26315-105">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="26315-106">Diğer örneklere erişmek için yukarıda açıklanan üst düzey sınıflar özelliklerini erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26315-106">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="26315-107">Örneğin, TransportBindingElement örneği erişebilir örneği -> uç noktasından bağlama BindingElements ->.</span><span class="sxs-lookup"><span data-stu-id="26315-107">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26315-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="26315-108">In This Section</span></span>  
 [<span data-ttu-id="26315-109">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="26315-109">ActivityTransfer</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/activitytransfer.md)  
  
 [<span data-ttu-id="26315-110">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="26315-110">AppDomainInfo</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)  
  
 [<span data-ttu-id="26315-111">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="26315-111">AspNetCompatibilityRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="26315-112">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-112">AsymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="26315-113">"Davranışı sınıf"</span><span class="sxs-lookup"><span data-stu-id="26315-113">"Behavior class"</span></span>  
  
 [<span data-ttu-id="26315-114">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-114">BinaryMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="26315-115">Bağlama</span><span class="sxs-lookup"><span data-stu-id="26315-115">Binding</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binding.md)  
  
 [<span data-ttu-id="26315-116">BindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-116">BindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/bindingelement.md)  
  
 [<span data-ttu-id="26315-117">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-117">CallbackBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/callbackbehavior.md)  
  
 [<span data-ttu-id="26315-118">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="26315-118">Channel class</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channel-class.md)  
  
 [<span data-ttu-id="26315-119">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="26315-119">ChannelPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channelpoolsettings.md)  
  
 [<span data-ttu-id="26315-120">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="26315-120">ClientCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientcredentials.md)  
  
 [<span data-ttu-id="26315-121">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-121">ClientViaBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)  
  
 [<span data-ttu-id="26315-122">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-122">CompositeDuplexBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="26315-123">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-123">ConnectionOrientedTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="26315-124">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="26315-124">Contract</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/contract.md)  
  
 [<span data-ttu-id="26315-125">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-125">CustomBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/custombindingelement.md)  
  
 [<span data-ttu-id="26315-126">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="26315-126">DeliveryRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="26315-127">Uç noktası</span><span class="sxs-lookup"><span data-stu-id="26315-127">Endpoint</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)  
  
 [<span data-ttu-id="26315-128">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-128">HttpsTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httpstransportbindingelement.md)  
  
 [<span data-ttu-id="26315-129">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-129">HttpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httptransportbindingelement.md)  
  
 [<span data-ttu-id="26315-130">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="26315-130">LocalServiceSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/localservicesecuritysettings.md)  
  
 [<span data-ttu-id="26315-131">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-131">MatchAllEndpointBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/matchallendpointbehavior.md)  
  
 [<span data-ttu-id="26315-132">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-132">MessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/messageencodingbindingelement.md)  
  
 [<span data-ttu-id="26315-133">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="26315-133">MsmqBindingElementBase</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqbindingelementbase.md)  
  
 [<span data-ttu-id="26315-134">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-134">MsmqIntegrationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="26315-135">Hem MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-135">MsmqTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="26315-136">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-136">MtomMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="26315-137">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-137">MustUnderstandBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mustunderstandbehavior.md)  
  
 [<span data-ttu-id="26315-138">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="26315-138">NamedPipeConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="26315-139">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-139">NamedPipeTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="26315-140">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-140">OneWayBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/onewaybindingelement.md)  
  
 <span data-ttu-id="26315-141">"İşlem sınıf"</span><span class="sxs-lookup"><span data-stu-id="26315-141">"Operation class"</span></span>  
  
 [<span data-ttu-id="26315-142">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="26315-142">OperationBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/operationbehaviorattribute.md)  
  
 [<span data-ttu-id="26315-143">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-143">PeerCustomResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="26315-144">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-144">PeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peerresolverbindingelement.md)  
  
 [<span data-ttu-id="26315-145">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="26315-145">PeerSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peersecuritysettings.md)  
  
 [<span data-ttu-id="26315-146">Duyduğunuz arabirimi belirtin</span><span class="sxs-lookup"><span data-stu-id="26315-146">PeerTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportbindingelement.md)  
  
 [<span data-ttu-id="26315-147">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="26315-147">PeerTransportSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="26315-148">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-148">PnrpPeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="26315-149">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-149">PrivacyNoticeBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/privacynoticebindingelement.md)  
  
 [<span data-ttu-id="26315-150">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-150">ReliableSessionBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="26315-151">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-151">SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md)  
  
 [<span data-ttu-id="26315-152">Hizmeti</span><span class="sxs-lookup"><span data-stu-id="26315-152">Service</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/service.md)  
  
 [<span data-ttu-id="26315-153">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="26315-153">ServiceAppDomain</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceappdomain.md)  
  
 [<span data-ttu-id="26315-154">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-154">ServiceAuthorizationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="26315-155">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="26315-155">ServiceBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicebehaviorattribute.md)  
  
 [<span data-ttu-id="26315-156">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="26315-156">ServiceCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicecredentials.md)  
  
 [<span data-ttu-id="26315-157">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-157">ServiceDebugBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicedebugbehavior.md)  
  
 [<span data-ttu-id="26315-158">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-158">ServiceMetadataBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicemetadatabehavior.md)  
  
 [<span data-ttu-id="26315-159">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-159">ServiceSecurityAuditBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="26315-160">ServiceThrottlingBehavior'dan</span><span class="sxs-lookup"><span data-stu-id="26315-160">ServiceThrottlingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="26315-161">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-161">ServiceTimeoutsBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="26315-162">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="26315-162">ServiceToEndpointAssociation</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetoendpointassociation.md)  
  
 [<span data-ttu-id="26315-163">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-163">SslStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="26315-164">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-164">SymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="26315-165">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-165">SynchronousReceiveBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="26315-166">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="26315-166">TcpConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="26315-167">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-167">TcpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcptransportbindingelement.md)  
  
 [<span data-ttu-id="26315-168">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-168">TextMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="26315-169">TraceListener</span><span class="sxs-lookup"><span data-stu-id="26315-169">TraceListener</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistener.md)  
  
 [<span data-ttu-id="26315-170">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="26315-170">TraceListenerArgument</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistenerargument.md)  
  
 [<span data-ttu-id="26315-171">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-171">TransactedBatchingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="26315-172">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="26315-172">TransactionFlowAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowattribute.md)  
  
 [<span data-ttu-id="26315-173">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-173">TransactionFlowBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowbindingelement.md)  
  
 [<span data-ttu-id="26315-174">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-174">TransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportbindingelement.md)  
  
 [<span data-ttu-id="26315-175">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-175">TransportSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="26315-176">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-176">UseManagedPresentationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="26315-177">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="26315-177">WindowsStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="26315-178">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="26315-178">WSAT_TraceEvent</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceevent.md)  
  
 [<span data-ttu-id="26315-179">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="26315-179">WSAT_TraceProvider</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceprovider.md)  
  
 [<span data-ttu-id="26315-180">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="26315-180">WSAT_TraceRecord</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-tracerecord.md)  
  
 [<span data-ttu-id="26315-181">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="26315-181">XmlDictionaryReaderQuotas</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="26315-182">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="26315-182">XmlSerializerOperationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmlserializeroperationbehavior.md)

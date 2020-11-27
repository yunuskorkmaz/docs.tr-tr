---
title: WMI Sınıfı Başvurusu
ms.date: 03/30/2017
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
ms.openlocfilehash: 9830fbf50e8df625e3d3077a66c66e0370204acb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262261"
---
# <a name="wmi-class-reference"></a><span data-ttu-id="f2dff-102">WMI Sınıfı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f2dff-102">WMI Class Reference</span></span>

<span data-ttu-id="f2dff-103">Bu bölümde Windows Communication Foundation (WCF) WMI sağlayıcısı tarafından sunulan tüm WMI sınıfları listelenir.</span><span class="sxs-lookup"><span data-stu-id="f2dff-103">This section lists all the WMI classes exposed by the Windows Communication Foundation (WCF) WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="f2dff-104">WMI örneklerine erişme</span><span class="sxs-lookup"><span data-stu-id="f2dff-104">Accessing WMI Instances</span></span>  

 <span data-ttu-id="f2dff-105">WMI nesne başvurusunda listelenen tüm sınıflar, Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation ve Endpoint dışında doğrudan başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="f2dff-105">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="f2dff-106">Diğer örneklere erişmek için, daha önce belirtilen en üst düzey sınıfların özelliklerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2dff-106">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="f2dff-107">Örneğin, > bağlama-> BindingElements uç nokta örneğinden TransportBindingElement Instance 'a erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2dff-107">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2dff-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f2dff-108">In This Section</span></span>  

 [<span data-ttu-id="f2dff-109">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="f2dff-109">ActivityTransfer</span></span>](activitytransfer.md)  
  
 [<span data-ttu-id="f2dff-110">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="f2dff-110">AppDomainInfo</span></span>](appdomaininfo.md)  
  
 [<span data-ttu-id="f2dff-111">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="f2dff-111">AspNetCompatibilityRequirementsAttribute</span></span>](aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="f2dff-112">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-112">AsymmetricSecurityBindingElement</span></span>](asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="f2dff-113">"Davranış sınıfı"</span><span class="sxs-lookup"><span data-stu-id="f2dff-113">"Behavior class"</span></span>  
  
 [<span data-ttu-id="f2dff-114">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-114">BinaryMessageEncodingBindingElement</span></span>](binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="f2dff-115">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f2dff-115">Binding</span></span>](binding.md)  
  
 [<span data-ttu-id="f2dff-116">BindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-116">BindingElement</span></span>](bindingelement.md)  
  
 [<span data-ttu-id="f2dff-117">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-117">CallbackBehavior</span></span>](callbackbehavior.md)  
  
 [<span data-ttu-id="f2dff-118">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="f2dff-118">Channel class</span></span>](channel-class.md)  
  
 [<span data-ttu-id="f2dff-119">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f2dff-119">ChannelPoolSettings</span></span>](channelpoolsettings.md)  
  
 [<span data-ttu-id="f2dff-120">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="f2dff-120">ClientCredentials</span></span>](clientcredentials.md)  
  
 [<span data-ttu-id="f2dff-121">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-121">ClientViaBehavior</span></span>](clientviabehavior.md)  
  
 [<span data-ttu-id="f2dff-122">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-122">CompositeDuplexBindingElement</span></span>](compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="f2dff-123">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-123">ConnectionOrientedTransportBindingElement</span></span>](connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="f2dff-124">Anlaşma</span><span class="sxs-lookup"><span data-stu-id="f2dff-124">Contract</span></span>](contract.md)  
  
 [<span data-ttu-id="f2dff-125">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-125">CustomBindingElement</span></span>](custombindingelement.md)  
  
 [<span data-ttu-id="f2dff-126">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="f2dff-126">DeliveryRequirementsAttribute</span></span>](deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="f2dff-127">Uç Nokta</span><span class="sxs-lookup"><span data-stu-id="f2dff-127">Endpoint</span></span>](endpoint.md)  
  
 [<span data-ttu-id="f2dff-128">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-128">HttpsTransportBindingElement</span></span>](httpstransportbindingelement.md)  
  
 [<span data-ttu-id="f2dff-129">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-129">HttpTransportBindingElement</span></span>](httptransportbindingelement.md)  
  
 [<span data-ttu-id="f2dff-130">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f2dff-130">LocalServiceSecuritySettings</span></span>](localservicesecuritysettings.md)  
  
 [<span data-ttu-id="f2dff-131">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-131">MatchAllEndpointBehavior</span></span>](matchallendpointbehavior.md)  
  
 [<span data-ttu-id="f2dff-132">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-132">MessageEncodingBindingElement</span></span>](messageencodingbindingelement.md)  
  
 [<span data-ttu-id="f2dff-133">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="f2dff-133">MsmqBindingElementBase</span></span>](msmqbindingelementbase.md)  
  
 [<span data-ttu-id="f2dff-134">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-134">MsmqIntegrationBindingElement</span></span>](msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="f2dff-135">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-135">MsmqTransportBindingElement</span></span>](msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="f2dff-136">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-136">MtomMessageEncodingBindingElement</span></span>](mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="f2dff-137">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-137">MustUnderstandBehavior</span></span>](mustunderstandbehavior.md)  
  
 [<span data-ttu-id="f2dff-138">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f2dff-138">NamedPipeConnectionPoolSettings</span></span>](namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="f2dff-139">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-139">NamedPipeTransportBindingElement</span></span>](namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="f2dff-140">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-140">OneWayBindingElement</span></span>](onewaybindingelement.md)  
  
 <span data-ttu-id="f2dff-141">"İşlem sınıfı"</span><span class="sxs-lookup"><span data-stu-id="f2dff-141">"Operation class"</span></span>  
  
 [<span data-ttu-id="f2dff-142">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="f2dff-142">OperationBehaviorAttribute</span></span>](operationbehaviorattribute.md)  
  
 [<span data-ttu-id="f2dff-143">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-143">PeerCustomResolverBindingElement</span></span>](peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="f2dff-144">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-144">PeerResolverBindingElement</span></span>](peerresolverbindingelement.md)  
  
 [<span data-ttu-id="f2dff-145">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f2dff-145">PeerSecuritySettings</span></span>](peersecuritysettings.md)  
  
 [<span data-ttu-id="f2dff-146">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-146">PeerTransportBindingElement</span></span>](peertransportbindingelement.md)  
  
 [<span data-ttu-id="f2dff-147">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f2dff-147">PeerTransportSecuritySettings</span></span>](peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="f2dff-148">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-148">PnrpPeerResolverBindingElement</span></span>](pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="f2dff-149">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-149">PrivacyNoticeBindingElement</span></span>](privacynoticebindingelement.md)  
  
 [<span data-ttu-id="f2dff-150">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-150">ReliableSessionBindingElement</span></span>](reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="f2dff-151">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-151">SecurityBindingElement</span></span>](securitybindingelement.md)  
  
 [<span data-ttu-id="f2dff-152">Hizmet</span><span class="sxs-lookup"><span data-stu-id="f2dff-152">Service</span></span>](service.md)  
  
 [<span data-ttu-id="f2dff-153">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="f2dff-153">ServiceAppDomain</span></span>](serviceappdomain.md)  
  
 [<span data-ttu-id="f2dff-154">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-154">ServiceAuthorizationBehavior</span></span>](serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="f2dff-155">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="f2dff-155">ServiceBehaviorAttribute</span></span>](servicebehaviorattribute.md)  
  
 [<span data-ttu-id="f2dff-156">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="f2dff-156">ServiceCredentials</span></span>](servicecredentials.md)  
  
 [<span data-ttu-id="f2dff-157">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-157">ServiceDebugBehavior</span></span>](servicedebugbehavior.md)  
  
 [<span data-ttu-id="f2dff-158">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-158">ServiceMetadataBehavior</span></span>](servicemetadatabehavior.md)  
  
 [<span data-ttu-id="f2dff-159">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-159">ServiceSecurityAuditBehavior</span></span>](servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="f2dff-160">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-160">ServiceThrottlingBehavior</span></span>](servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="f2dff-161">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-161">ServiceTimeoutsBehavior</span></span>](servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="f2dff-162">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="f2dff-162">ServiceToEndpointAssociation</span></span>](servicetoendpointassociation.md)  
  
 [<span data-ttu-id="f2dff-163">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-163">SslStreamSecurityBindingElement</span></span>](sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="f2dff-164">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-164">SymmetricSecurityBindingElement</span></span>](symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="f2dff-165">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-165">SynchronousReceiveBehavior</span></span>](synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="f2dff-166">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f2dff-166">TcpConnectionPoolSettings</span></span>](tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="f2dff-167">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-167">TcpTransportBindingElement</span></span>](tcptransportbindingelement.md)  
  
 [<span data-ttu-id="f2dff-168">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-168">TextMessageEncodingBindingElement</span></span>](textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="f2dff-169">TraceListener</span><span class="sxs-lookup"><span data-stu-id="f2dff-169">TraceListener</span></span>](tracelistener.md)  
  
 [<span data-ttu-id="f2dff-170">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="f2dff-170">TraceListenerArgument</span></span>](tracelistenerargument.md)  
  
 [<span data-ttu-id="f2dff-171">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-171">TransactedBatchingBehavior</span></span>](transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="f2dff-172">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="f2dff-172">TransactionFlowAttribute</span></span>](transactionflowattribute.md)  
  
 [<span data-ttu-id="f2dff-173">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-173">TransactionFlowBindingElement</span></span>](transactionflowbindingelement.md)  
  
 [<span data-ttu-id="f2dff-174">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-174">TransportBindingElement</span></span>](transportbindingelement.md)  
  
 [<span data-ttu-id="f2dff-175">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-175">TransportSecurityBindingElement</span></span>](transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="f2dff-176">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-176">UseManagedPresentationBindingElement</span></span>](usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="f2dff-177">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f2dff-177">WindowsStreamSecurityBindingElement</span></span>](windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="f2dff-178">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="f2dff-178">WSAT_TraceEvent</span></span>](wsat-traceevent.md)  
  
 [<span data-ttu-id="f2dff-179">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="f2dff-179">WSAT_TraceProvider</span></span>](wsat-traceprovider.md)  
  
 [<span data-ttu-id="f2dff-180">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f2dff-180">WSAT_TraceRecord</span></span>](wsat-tracerecord.md)  
  
 [<span data-ttu-id="f2dff-181">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f2dff-181">XmlDictionaryReaderQuotas</span></span>](xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="f2dff-182">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="f2dff-182">XmlSerializerOperationBehavior</span></span>](xmlserializeroperationbehavior.md)

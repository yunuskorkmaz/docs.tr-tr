---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399536"
---
# \<soapProcessing>

<span data-ttu-id="068ba-101">Farklı bağlama türleri ve ileti sürümleri arasındaki iletileri sıralamak için kullanılan istemci uç noktası davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="068ba-101">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**
  
## <a name="syntax"></a><span data-ttu-id="068ba-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="068ba-102">Syntax</span></span>  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="068ba-103">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="068ba-103">Attributes and elements</span></span>  
  
<span data-ttu-id="068ba-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="068ba-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="068ba-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="068ba-105">Attributes</span></span>  
  
|                   | <span data-ttu-id="068ba-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="068ba-106">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="068ba-107">SOAP iletisi sürümleri arasında iletilerin sıralanması gerekip gerekmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="068ba-107">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="068ba-108">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="068ba-108">Child elements</span></span>

<span data-ttu-id="068ba-109">Yok</span><span class="sxs-lookup"><span data-stu-id="068ba-109">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="068ba-110">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="068ba-110">Parent elements</span></span>

|     | <span data-ttu-id="068ba-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="068ba-111">Description</span></span> |
| --- | ----------- |
| [**\<behavior>**](behavior-of-endpointbehaviors.md) | <span data-ttu-id="068ba-112">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="068ba-112">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="068ba-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="068ba-113">Remarks</span></span>

<span data-ttu-id="068ba-114">SOAP işleme, iletilerin ileti sürümleri arasında dönüştürüldüğü işlemdir.</span><span class="sxs-lookup"><span data-stu-id="068ba-114">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="068ba-115">Windows Communication Foundation (WCF) yönlendirme hizmeti, iletileri bir protokolden diğerine dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="068ba-115">The Windows Communication Foundation (WCF) Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="068ba-116">Gelen ve giden Ileti sürümleri farklıysa, doğru sürüme yönelik yeni bir ileti oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="068ba-116">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="068ba-117">İletileri bir diğerine işlemek <xref:System.ServiceModel.Channels.MessageVersion> , gelen WCF iletisinden gövde parçasını ve ilgili üstbilgileri içeren yeni BIR WCF iletisi oluşturarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="068ba-117">Processing messages from one <xref:System.ServiceModel.Channels.MessageVersion> to another is accomplished by constructing a new WCF message that contains the body part and relevant headers from the incoming WCF message.</span></span> <span data-ttu-id="068ba-118">Adresleme 'ye özgü olan veya yönlendirici düzeyinde anlaşılabilecek üstbilgiler, bu üst bilgiler farklı bir sürümlük (adresleme üstbilgileri durumunda) veya istemci ile yönlendirici arasındaki iletişimin bir parçası olarak işlendiği için yeni WCF iletisinin oluşturulması sırasında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="068ba-118">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="068ba-119">Giden iletiye bir üstbilginin yerleştirilip yerleştirilmediği, gelen kanal katmanından geçerken anlaşıldığı şekilde işaretlenip işaretlenmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="068ba-119">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="068ba-120">Anlaşılmayan (özel üstbilgiler gibi) üstbilgiler kaldırılmaz ve bu nedenle Giden iletiye kopyalanarak yönlendirme hizmetini geçirin.</span><span class="sxs-lookup"><span data-stu-id="068ba-120">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="068ba-121">İletinin gövdesi Giden iletiye kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="068ba-121">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="068ba-122">İleti daha sonra giden kanal gönderilir ve bu iletişim protokolüne/taşımasına özgü tüm üst bilgiler ve diğer zarf verileri oluşturulur ve eklenir.</span><span class="sxs-lookup"><span data-stu-id="068ba-122">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="068ba-123">Bu tür işleme adımları SOAP işleme davranışı belirtildiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="068ba-123">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="068ba-124">Bu [\<soapProcessingExtension>](soapprocessing.md) davranış, yönlendirme hizmeti başlatıldığında tüm istemci (giden) uç noktalarına uygulanan bir uç nokta davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="068ba-124">This [\<soapProcessingExtension>](soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="068ba-125">Varsayılan olarak, [\<routing>](routing-of-servicebehavior.md) davranış [\<soapProcessingExtension>](soapprocessing.md) `processMessages` `true` her istemci uç noktası için olarak ayarlanmış yeni bir davranış oluşturur ve ekler.</span><span class="sxs-lookup"><span data-stu-id="068ba-125">default, the [\<routing>](routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="068ba-126">Yönlendirme hizmetinin anlayamadığı bir protokolüne sahipseniz veya varsayılan işleme davranışını geçersiz kılmak istiyorsanız, tüm yönlendirme hizmeti veya yalnızca belirli uç noktalar için SOAP işlemeyi devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="068ba-126">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="068ba-127">Tüm uç noktalarında tüm yönlendirme hizmeti için SOAP işlemeyi devre dışı bırakmak için `soapProcessing` [\<routing>](routing-of-servicebehavior.md) davranışın özniteliğini olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="068ba-127">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="068ba-128">Belirli bir uç nokta için SOAP işlemeyi devre dışı bırakmak için, bu davranışı kullanın ve `processMessages` özniteliğini olarak ayarlayın `false` , ardından bu davranışı varsayılan işleme kodunun çalıştırılmasını istemediğiniz uç noktaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="068ba-128">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="068ba-129">[\<routing>](routing-of-servicebehavior.md)Davranış yönlendirme hizmetini ayarlarken, zaten mevcut olduğundan, uç nokta davranışının yeniden uygulanması atlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="068ba-129">When the [\<routing>](routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>

---
description: 'Daha fazla bilgi edinin: taşınabilir alt küme projesinde Hizmet Başvurusu Ekle'
title: Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 85c7c38c26481487b02c39917986c916ac31282f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677489"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="97baf-103">Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="97baf-103">Add Service Reference in a Portable Subset Project</span></span>

<span data-ttu-id="97baf-104">Taşınabilir alt küme projeleri, .NET derleme programcılarının tek bir kaynak ağacı ve derleme sistemi ile aynı zamanda birden çok .NET uygulaması (Masaüstü, Silverlight, Windows Phone ve Xbox) desteklemeye devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="97baf-104">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and Xbox).</span></span> <span data-ttu-id="97baf-105">Taşınabilir alt küme projeleri yalnızca .NET uygulamalarında kullanılabilen, .NET derlemeleri olan taşınabilir kitaplıklara başvurur.</span><span class="sxs-lookup"><span data-stu-id="97baf-105">Portable subset projects only reference portable libraries that are .NET assemblies that can be used on any .NET implementation.</span></span>
  
## <a name="add-service-reference-details"></a><span data-ttu-id="97baf-106">Hizmet Başvurusu Ekle ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="97baf-106">Add Service Reference Details</span></span>  

 <span data-ttu-id="97baf-107">Taşınabilir alt küme projesine hizmet başvurusu eklerken aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="97baf-107">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1. <span data-ttu-id="97baf-108">İçin <xref:System.Xml.Serialization.XmlSerializer> yalnızca sabit değer kodlamalarına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="97baf-108">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="97baf-109">SOAP kodlamaları içeri aktarma sırasında bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97baf-109">SOAP encodings generate an error during import.</span></span>  
  
2. <span data-ttu-id="97baf-110">Senaryoları kullanan hizmetler için <xref:System.Runtime.Serialization.DataContractSerializer> , yeniden kullanılan türlerin yalnızca taşınabilir alt kümeden geldiğinden emin olmak için bir veri sözleşmesi yedeği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="97baf-110">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3. <span data-ttu-id="97baf-111">Taşınabilir kitaplıklarda desteklenmeyen bağlamalara dayanan uç noktalar ( <xref:System.ServiceModel.BasicHttpBinding> <xref:System.ServiceModel.WSHttpBinding> işlem akışı, güvenilir oturumlar veya MTOM kodlaması olmadan ve eşdeğer özel bağlamalar hariç tüm bağlamalar) yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="97baf-111">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4. <span data-ttu-id="97baf-112">İleti üstbilgileri, içeri aktarmadan önce tüm işlemlerde tüm ileti açıklamalarından silinir.</span><span class="sxs-lookup"><span data-stu-id="97baf-112">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5. <span data-ttu-id="97baf-113">Taşınabilir olmayan öznitelikler <xref:System.ComponentModel.DesignerCategoryAttribute> , <xref:System.SerializableAttribute> ve <xref:System.ServiceModel.TransactionFlowAttribute> oluşturulan istemci proxy kodundan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="97baf-113">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6. <span data-ttu-id="97baf-114">Taşınabilir olmayan özellikler ProtectionLevel, SessionMode, IsInitiating, ısating, ve öğesinden <xref:System.ServiceModel.ServiceContractAttribute> kaldırılır <xref:System.ServiceModel.OperationContractAttribute> <xref:System.ServiceModel.FaultContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="97baf-114">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7. <span data-ttu-id="97baf-115">Tüm hizmet işlemleri istemci proxy 'sinde zaman uyumsuz işlemler olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="97baf-115">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8. <span data-ttu-id="97baf-116">Taşınabilir olmayan türler kullanan oluşturulan istemci oluşturucuları kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="97baf-116">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="97baf-117"><xref:System.Net.CookieContainer>Oluşturulan istemcide bir örnek gösterilir.</span><span class="sxs-lookup"><span data-stu-id="97baf-117">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="97baf-118">Kod oluşturucunun derlemesini ve sürümünü tanımlayan dosyanın en üstüne bir açıklama eklenir:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="97baf-118">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="97baf-119"><xref:System.Runtime.Serialization.ISerializable>Arabirim desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="97baf-119">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="97baf-120">Net. TCP ve PollingDuplex bağlamaları desteklenmez</span><span class="sxs-lookup"><span data-stu-id="97baf-120">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="97baf-121"><xref:System.Runtime.Serialization.DataContractSerializer>Her zaman hatalar için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="97baf-121">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="97baf-122"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> Taşınabilir alt küme projelerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="97baf-122"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97baf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97baf-123">See also</span></span>

- [<span data-ttu-id="97baf-124">WCF İstemcisi Kullanarak Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="97baf-124">Accessing Services Using a WCF Client</span></span>](accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="97baf-125">Taşınabilir Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="97baf-125">Portable Class Library</span></span>](../cross-platform/portable-class-library.md)

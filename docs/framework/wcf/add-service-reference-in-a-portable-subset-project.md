---
title: Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: e1d65df46c0ed6d9d271727ad04a661c5e34a1ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145437"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="d0059-102">Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="d0059-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="d0059-103">Taşınabilir alt küme projeleri bir tek kaynak ağacının Bakımı ve birden çok .NET uygulamalarını (masaüstünde, Silverlight, Windows Phone ve XBOX) hala desteklerken yapı sistemi .NET derleme programcılar etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d0059-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="d0059-104">Taşınabilir alt küme projeleri yalnızca herhangi bir .NET uygulaması üzerinde kullanılabilen bir .NET framework derlemesi olan bir .NET taşınabilir kitaplıklar başvuru.</span><span class="sxs-lookup"><span data-stu-id="d0059-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="d0059-105">Hizmet başvuru ayrıntıları ekleyin</span><span class="sxs-lookup"><span data-stu-id="d0059-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="d0059-106">Bir taşınabilir alt küme projesine hizmet başvurusu ekleme, aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="d0059-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1.  <span data-ttu-id="d0059-107">İçin <xref:System.Xml.Serialization.XmlSerializer>, yalnızca sabit Kodlamalar izin verilir.</span><span class="sxs-lookup"><span data-stu-id="d0059-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="d0059-108">SOAP Kodlamalar, içeri aktarma sırasında bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d0059-108">SOAP encodings generate an error during import.</span></span>  
  
2.  <span data-ttu-id="d0059-109">Hizmetleri kullanan <xref:System.Runtime.Serialization.DataContractSerializer> senaryoları, veri sözleşme vekil yeniden kullanılan türleri yalnızca taşınabilir alt kümesinden geldiğini emin olmak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d0059-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3.  <span data-ttu-id="d0059-110">Taşınabilir kitaplıklarda desteklenmeyen bağlamalar kullanan uç noktaları (dışındaki tüm bağlamaları <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> işlem akışı, güvenilir oturumlar veya MTOM kodlama ve eşdeğer özel bağlamalar olmadan) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="d0059-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4.  <span data-ttu-id="d0059-111">İleti üstbilgileri içeri aktarmadan önce tüm işlemlerdeki tüm ileti açıklamalarını silinir.</span><span class="sxs-lookup"><span data-stu-id="d0059-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5.  <span data-ttu-id="d0059-112">Taşınabilir olmayan öznitelikler <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, ve <xref:System.ServiceModel.TransactionFlowAttribute> oluşturulan istemci proxy koddan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="d0059-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6.  <span data-ttu-id="d0059-113">ProtectionLevel, Sessionmode'u, IsInitiating ve IsTerminating kaldırılma taşınabilir olmayan özellikler <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, ve <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d0059-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7.  <span data-ttu-id="d0059-114">Tüm hizmet işlemlerini zaman uyumsuz işlemler istemci proxy'de'olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d0059-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8.  <span data-ttu-id="d0059-115">Taşınabilir olmayan türler kullanan oluşturulan istemci oluşturucular kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d0059-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="d0059-116">A <xref:System.Net.CookieContainer> örneği oluşturulan istemcide gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d0059-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="d0059-117">Bir yorum derlemeyi ve kod oluşturucunun sürümünü tanımlayan dosyasının en üstüne eklenir:</span><span class="sxs-lookup"><span data-stu-id="d0059-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:</span></span>`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`  
  
11. <span data-ttu-id="d0059-118"><xref:System.Runtime.Serialization.ISerializable> Arabirimi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d0059-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="d0059-119">Net.Tcp ve PollingDuplex bağlamaları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d0059-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="d0059-120"><xref:System.Runtime.Serialization.DataContractSerializer> Hataları için her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0059-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> <span data-ttu-id="d0059-121">Taşınabilir alt küme projelerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d0059-121">is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0059-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0059-122">See also</span></span>

- [<span data-ttu-id="d0059-123">WCF İstemcisi Kullanarak Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="d0059-123">Accessing Services Using a WCF Client</span></span>](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="d0059-124">Taşınabilir Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d0059-124">Portable Class Library</span></span>](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)

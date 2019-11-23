---
title: Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 764ce487d8f2673eb2c75f8cd05da4ccbae3c935
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320845"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="0396e-102">Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="0396e-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="0396e-103">Taşınabilir alt küme projeleri, .NET derleme programcılarının tek bir kaynak ağacı ve derleme sistemi ile aynı zamanda birden çok .NET uygulaması (Masaüstü, Silverlight, Windows Phone ve XBOX) desteklemeye devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="0396e-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="0396e-104">Taşınabilir alt küme projeleri yalnızca .NET uygulamalarında kullanılabilecek .NET Framework derlemesi olan .NET taşınabilir kitaplıklarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="0396e-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="0396e-105">Hizmet Başvurusu Ekle ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="0396e-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="0396e-106">Taşınabilir alt küme projesine hizmet başvurusu eklerken aşağıdaki kısıtlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="0396e-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1. <span data-ttu-id="0396e-107"><xref:System.Xml.Serialization.XmlSerializer>için yalnızca sabit kodlamalara izin verilir.</span><span class="sxs-lookup"><span data-stu-id="0396e-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="0396e-108">SOAP kodlamaları içeri aktarma sırasında bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0396e-108">SOAP encodings generate an error during import.</span></span>  
  
2. <span data-ttu-id="0396e-109"><xref:System.Runtime.Serialization.DataContractSerializer> senaryolar kullanan hizmetler için, yeniden kullanılan türlerin yalnızca taşınabilir alt kümeden gelmesini sağlamak üzere bir veri sözleşmesi yedeği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0396e-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3. <span data-ttu-id="0396e-110">Taşınabilir kitaplıklarda desteklenmeyen bağlamalara dayanan uç noktalar (<xref:System.ServiceModel.BasicHttpBinding>, işlem akışı olmadan <xref:System.ServiceModel.WSHttpBinding>, güvenilir oturumlar veya MTOM kodlaması ve eşdeğer özel bağlamalar) hariç tüm bağlamalar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="0396e-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4. <span data-ttu-id="0396e-111">İleti üstbilgileri, içeri aktarmadan önce tüm işlemlerde tüm ileti açıklamalarından silinir.</span><span class="sxs-lookup"><span data-stu-id="0396e-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5. <span data-ttu-id="0396e-112">Taşınabilir olmayan öznitelikler <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>ve <xref:System.ServiceModel.TransactionFlowAttribute>, oluşturulan istemci proxy kodundan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="0396e-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6. <span data-ttu-id="0396e-113">Taşınabilir olmayan özellikler ProtectionLevel, SessionMode, IsInitiating, ısating <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>ve <xref:System.ServiceModel.FaultContractAttribute>kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="0396e-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7. <span data-ttu-id="0396e-114">Tüm hizmet işlemleri istemci proxy 'sinde zaman uyumsuz işlemler olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0396e-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8. <span data-ttu-id="0396e-115">Taşınabilir olmayan türler kullanan oluşturulan istemci oluşturucuları kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="0396e-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="0396e-116">Oluşturulan istemcide <xref:System.Net.CookieContainer> bir örnek gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0396e-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="0396e-117">Kod oluşturucunun derlemesini ve sürümünü tanımlayan dosyanın üst kısmına bir açıklama eklenir:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="0396e-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="0396e-118"><xref:System.Runtime.Serialization.ISerializable> arabirimi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0396e-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="0396e-119">Net. TCP ve PollingDuplex bağlamaları desteklenmez</span><span class="sxs-lookup"><span data-stu-id="0396e-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="0396e-120"><xref:System.Runtime.Serialization.DataContractSerializer> her zaman hatalar için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="0396e-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="0396e-121">Taşınabilir alt küme projelerinde <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0396e-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0396e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0396e-122">See also</span></span>

- [<span data-ttu-id="0396e-123">WCF İstemcisi Kullanarak Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="0396e-123">Accessing Services Using a WCF Client</span></span>](accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="0396e-124">Taşınabilir Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="0396e-124">Portable Class Library</span></span>](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)

---
title: Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 5d094bb1d2d1155565e48850a2f41829a93cff84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460495"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="642b7-102">Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="642b7-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="642b7-103">Taşınabilir alt projeleri .NET derleme programcıların tek kaynak ağaç korumak ve birden çok .NET uygulamalarında (Masaüstü, Silverlight, Windows Phone ve XBOX) hala desteklerken oluşturma sistemi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="642b7-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="642b7-104">Taşınabilir alt projeleri üzerinde herhangi bir .NET uygulaması kullanılabilir bir .NET framework derlemesi olan .NET taşınabilir kitaplıklara yalnızca başvuru.</span><span class="sxs-lookup"><span data-stu-id="642b7-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="642b7-105">Hizmet başvurusu ayrıntılarını Ekle</span><span class="sxs-lookup"><span data-stu-id="642b7-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="642b7-106">Bir taşınabilir alt küme projesine hizmet başvurusu eklerken aşağıdaki sınırlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="642b7-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1.  <span data-ttu-id="642b7-107">İçin <xref:System.Xml.Serialization.XmlSerializer>, yalnızca sabit Kodlamalar izin verilir.</span><span class="sxs-lookup"><span data-stu-id="642b7-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="642b7-108">SOAP Kodlamalar içeri aktarma sırasında bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="642b7-108">SOAP encodings generate an error during import.</span></span>  
  
2.  <span data-ttu-id="642b7-109">Kullanan Hizmetleri için <xref:System.Runtime.Serialization.DataContractSerializer> senaryolar, bir veri sözleşmesi yedek yeniden kullanılan türleri yalnızca taşınabilir alt geldiğini emin olmak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="642b7-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3.  <span data-ttu-id="642b7-110">Taşınabilir kitaplıklara desteklenmeyen bağlamaları Bel uç noktaları (dışındaki tüm bağlamaları <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> işlem akışı, güvenilir oturumlar veya MTOM kodlama ve eşdeğer özel bağlama olmadan) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="642b7-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4.  <span data-ttu-id="642b7-111">İleti üstbilgilerini içe aktarma işleminden önce tüm işlemleri tüm ileti açıklamasında silinir.</span><span class="sxs-lookup"><span data-stu-id="642b7-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5.  <span data-ttu-id="642b7-112">Taşınamaz öznitelikleri <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, ve <xref:System.ServiceModel.TransactionFlowAttribute> oluşturulan istemci proxy kodundan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="642b7-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6.  <span data-ttu-id="642b7-113">ProtectionLevel SessionMode, IsInitiating, IsTerminating kaldırılma taşınamaz özellikleri <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, ve <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="642b7-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7.  <span data-ttu-id="642b7-114">Tüm hizmet işlemlerini zaman uyumsuz işlemleri istemci proxy olarak üretilir.</span><span class="sxs-lookup"><span data-stu-id="642b7-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8.  <span data-ttu-id="642b7-115">Taşınabilir olmayan türler kullanan oluşturulan istemci oluşturucular kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="642b7-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="642b7-116">A <xref:System.Net.CookieContainer> örneği üzerinde oluşturulan istemci gösterilir.</span><span class="sxs-lookup"><span data-stu-id="642b7-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="642b7-117">Açıklama, derleme ve sürüm kod oluşturucunun tanımlama dosyasının en üstte eklenir:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="642b7-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="642b7-118"><xref:System.Runtime.Serialization.ISerializable> Arabirimi desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="642b7-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="642b7-119">Net.Tcp ve PollingDuplex bağlamaları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="642b7-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="642b7-120"><xref:System.Runtime.Serialization.DataContractSerializer> Hataları için her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="642b7-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="642b7-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> Taşınabilir alt projelerinde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="642b7-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="642b7-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="642b7-122">See Also</span></span>  
 [<span data-ttu-id="642b7-123">WCF İstemcisi Kullanarak Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="642b7-123">Accessing Services Using a WCF Client</span></span>](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 <span data-ttu-id="642b7-124">[Taşınabilir Sınıf Kitaplığı](http://msdn.microsoft.com/library/gg597391\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="642b7-124">[Portable Class Library](http://msdn.microsoft.com/library/gg597391\(v=vs.110\))</span></span>

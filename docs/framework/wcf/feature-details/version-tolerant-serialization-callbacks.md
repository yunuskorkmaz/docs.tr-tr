---
title: Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: 0736f94b1fe1a91b20ee76da673e0bc139aa802a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959561"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="91673-102">Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları</span><span class="sxs-lookup"><span data-stu-id="91673-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="91673-103">Veri sözleşmesi programlama modeli, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> sınıflarının desteklediği sürüm dayanıklı serileştirme geri çağırma yöntemlerini tam olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="91673-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="91673-104">Sürüm dayanıklı öznitelikler</span><span class="sxs-lookup"><span data-stu-id="91673-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="91673-105">Dört geri çağrı özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="91673-105">There are four callback attributes.</span></span> <span data-ttu-id="91673-106">Her öznitelik, serileştirme/seri kaldırma altyapısının çeşitli zamanlarda çağırdığı bir yönteme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="91673-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="91673-107">Aşağıdaki tabloda her bir özniteliğin ne zaman kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91673-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="91673-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="91673-108">Attribute</span></span>|<span data-ttu-id="91673-109">Karşılık gelen yöntem çağrıldığında</span><span class="sxs-lookup"><span data-stu-id="91673-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="91673-110">Tür serileştirilden önce çağırılır.</span><span class="sxs-lookup"><span data-stu-id="91673-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="91673-111">Tür serileştirildikten sonra çağırılır.</span><span class="sxs-lookup"><span data-stu-id="91673-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="91673-112">Türü seri durumdan çıkarılırken çağırılır.</span><span class="sxs-lookup"><span data-stu-id="91673-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="91673-113">Türün serisi kaldırıldıktan sonra çağırılır.</span><span class="sxs-lookup"><span data-stu-id="91673-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="91673-114">Yöntemler bir <xref:System.Runtime.Serialization.StreamingContext> parametreyi kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="91673-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="91673-115">Bu yöntemler öncelikle sürüm oluşturma veya başlatma ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="91673-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="91673-116">Seri durumdan çıkarma sırasında hiçbir Oluşturucu çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="91673-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="91673-117">Bu nedenle, veri üyeleri gelen akışta eksik (örneğin, veriler, bazı veri üyelerini içermeyen bir türün önceki bir sürümünden geliyorsa), bu üyelerin verileri doğru başlatılmamış olabilir (amaçlanan varsayılan değerlere göre).</span><span class="sxs-lookup"><span data-stu-id="91673-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="91673-118">Bunu düzeltmek için, aşağıdaki örnekte gösterildiği gibi, ile <xref:System.Runtime.Serialization.OnDeserializingAttribute>işaretlenmiş geri çağırma yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="91673-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="91673-119">Yukarıdaki geri çağırma özniteliklerinin her biri ile, her tür için yalnızca bir yöntem işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91673-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="91673-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="91673-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="91673-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91673-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="91673-122">Sürüme Dayanıklı Serileştirme</span><span class="sxs-lookup"><span data-stu-id="91673-122">Version Tolerant Serialization</span></span>](../../../standard/serialization/version-tolerant-serialization.md)

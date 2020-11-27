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
ms.openlocfilehash: ad162f24042f30eabee7a1fad2025072b26d9af5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289379"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="a9f74-102">Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları</span><span class="sxs-lookup"><span data-stu-id="a9f74-102">Version-Tolerant Serialization Callbacks</span></span>

<span data-ttu-id="a9f74-103">Veri sözleşmesi programlama modeli, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve sınıflarının desteklediği sürüm dayanıklı serileştirme geri çağırma yöntemlerini tam olarak destekler <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> .</span><span class="sxs-lookup"><span data-stu-id="a9f74-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="a9f74-104">Version-Tolerant öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="a9f74-104">Version-Tolerant Attributes</span></span>  

 <span data-ttu-id="a9f74-105">Dört geri çağrı özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="a9f74-105">There are four callback attributes.</span></span> <span data-ttu-id="a9f74-106">Her öznitelik, serileştirme/seri kaldırma altyapısının çeşitli zamanlarda çağırdığı bir yönteme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a9f74-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="a9f74-107">Aşağıdaki tabloda her bir özniteliğin ne zaman kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9f74-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="a9f74-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a9f74-108">Attribute</span></span>|<span data-ttu-id="a9f74-109">Karşılık gelen yöntem çağrıldığında</span><span class="sxs-lookup"><span data-stu-id="a9f74-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="a9f74-110">Tür serileştirilden önce çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a9f74-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="a9f74-111">Tür serileştirildikten sonra çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a9f74-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="a9f74-112">Türü seri durumdan çıkarılırken çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a9f74-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="a9f74-113">Türün serisi kaldırıldıktan sonra çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a9f74-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="a9f74-114">Yöntemler bir parametreyi kabul etmelidir <xref:System.Runtime.Serialization.StreamingContext> .</span><span class="sxs-lookup"><span data-stu-id="a9f74-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="a9f74-115">Bu yöntemler öncelikle sürüm oluşturma veya başlatma ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a9f74-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="a9f74-116">Seri durumdan çıkarma sırasında hiçbir Oluşturucu çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="a9f74-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="a9f74-117">Bu nedenle, veri üyeleri gelen akışta eksik (örneğin, veriler, bazı veri üyelerini içermeyen bir türün önceki bir sürümünden geliyorsa), bu üyelerin verileri doğru başlatılmamış olabilir (amaçlanan varsayılan değerlere göre).</span><span class="sxs-lookup"><span data-stu-id="a9f74-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="a9f74-118">Bunu düzeltmek için, <xref:System.Runtime.Serialization.OnDeserializingAttribute> Aşağıdaki örnekte gösterildiği gibi, ile işaretlenmiş geri çağırma yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a9f74-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="a9f74-119">Yukarıdaki geri çağırma özniteliklerinin her biri ile, her tür için yalnızca bir yöntem işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9f74-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a9f74-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9f74-120">Example</span></span>  

 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="a9f74-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9f74-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="a9f74-122">Sürüme Dayanıklı Serileştirme</span><span class="sxs-lookup"><span data-stu-id="a9f74-122">Version Tolerant Serialization</span></span>](../../../standard/serialization/version-tolerant-serialization.md)

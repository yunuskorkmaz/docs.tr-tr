---
description: 'Hakkında daha fazla bilgi edinin: Version-Tolerant serileştirme geri çağırmaları'
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
ms.openlocfilehash: 8ee53e96b90ae6b0f2993a543fc129d75eb3481f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756012"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="765d7-103">Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları</span><span class="sxs-lookup"><span data-stu-id="765d7-103">Version-Tolerant Serialization Callbacks</span></span>

<span data-ttu-id="765d7-104">Veri sözleşmesi programlama modeli, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve sınıflarının desteklediği sürüm dayanıklı serileştirme geri çağırma yöntemlerini tam olarak destekler <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> .</span><span class="sxs-lookup"><span data-stu-id="765d7-104">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="765d7-105">Version-Tolerant öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="765d7-105">Version-Tolerant Attributes</span></span>  

 <span data-ttu-id="765d7-106">Dört geri çağrı özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="765d7-106">There are four callback attributes.</span></span> <span data-ttu-id="765d7-107">Her öznitelik, serileştirme/seri kaldırma altyapısının çeşitli zamanlarda çağırdığı bir yönteme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="765d7-107">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="765d7-108">Aşağıdaki tabloda her bir özniteliğin ne zaman kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="765d7-108">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="765d7-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="765d7-109">Attribute</span></span>|<span data-ttu-id="765d7-110">Karşılık gelen yöntem çağrıldığında</span><span class="sxs-lookup"><span data-stu-id="765d7-110">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="765d7-111">Tür serileştirilden önce çağırılır.</span><span class="sxs-lookup"><span data-stu-id="765d7-111">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="765d7-112">Tür serileştirildikten sonra çağırılır.</span><span class="sxs-lookup"><span data-stu-id="765d7-112">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="765d7-113">Türü seri durumdan çıkarılırken çağırılır.</span><span class="sxs-lookup"><span data-stu-id="765d7-113">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="765d7-114">Türün serisi kaldırıldıktan sonra çağırılır.</span><span class="sxs-lookup"><span data-stu-id="765d7-114">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="765d7-115">Yöntemler bir parametreyi kabul etmelidir <xref:System.Runtime.Serialization.StreamingContext> .</span><span class="sxs-lookup"><span data-stu-id="765d7-115">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="765d7-116">Bu yöntemler öncelikle sürüm oluşturma veya başlatma ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="765d7-116">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="765d7-117">Seri durumdan çıkarma sırasında hiçbir Oluşturucu çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="765d7-117">During deserialization, no constructors are called.</span></span> <span data-ttu-id="765d7-118">Bu nedenle, veri üyeleri gelen akışta eksik (örneğin, veriler, bazı veri üyelerini içermeyen bir türün önceki bir sürümünden geliyorsa), bu üyelerin verileri doğru başlatılmamış olabilir (amaçlanan varsayılan değerlere göre).</span><span class="sxs-lookup"><span data-stu-id="765d7-118">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="765d7-119">Bunu düzeltmek için, <xref:System.Runtime.Serialization.OnDeserializingAttribute> Aşağıdaki örnekte gösterildiği gibi, ile işaretlenmiş geri çağırma yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="765d7-119">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="765d7-120">Yukarıdaki geri çağırma özniteliklerinin her biri ile, her tür için yalnızca bir yöntem işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="765d7-120">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="765d7-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="765d7-121">Example</span></span>  

 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="765d7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="765d7-122">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="765d7-123">Sürüme Dayanıklı Serileştirme</span><span class="sxs-lookup"><span data-stu-id="765d7-123">Version Tolerant Serialization</span></span>](../../../standard/serialization/version-tolerant-serialization.md)

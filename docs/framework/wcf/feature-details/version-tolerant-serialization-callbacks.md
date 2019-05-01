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
ms.openlocfilehash: da13f9989b427da047c4a94f77907847ed2ae4d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932632"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="e52bb-102">Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları</span><span class="sxs-lookup"><span data-stu-id="e52bb-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="e52bb-103">Veri sözleşmesi programlama modeli tam sürüme dayanıklı serileştirme geri çağırma yöntemleri destekler, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> destek sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e52bb-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="e52bb-104">Sürüm toleranslı öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="e52bb-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="e52bb-105">Dört geri çağırma özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="e52bb-105">There are four callback attributes.</span></span> <span data-ttu-id="e52bb-106">Her öznitelik, serileştirme/seri durumundan çıkarma altyapısı çeşitli zamanlarda çağıran yönteme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e52bb-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="e52bb-107">Aşağıdaki tabloda her bir öznitelik kullanıldığı durumlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e52bb-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="e52bb-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e52bb-108">Attribute</span></span>|<span data-ttu-id="e52bb-109">İlgili yöntem olduğunda çağrılır</span><span class="sxs-lookup"><span data-stu-id="e52bb-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="e52bb-110">Türü serileştirme önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e52bb-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="e52bb-111">Türü seri hale getirme sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e52bb-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="e52bb-112">Türü seri durumdan çıkarılırken önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e52bb-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="e52bb-113">Türü seri durumdan çıkarılırken sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e52bb-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="e52bb-114">Yöntemleri kabul etmesi gereken bir <xref:System.Runtime.Serialization.StreamingContext> parametresi.</span><span class="sxs-lookup"><span data-stu-id="e52bb-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="e52bb-115">Bu yöntemler, sürüm oluşturma veya başlatma kullanmak için öncelikle yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e52bb-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="e52bb-116">Hiçbir oluşturucuya seri durumundan çıkarma sırasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e52bb-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="e52bb-117">Bu üyeleri için verileri gelen akışta, örneğin, eksikse, bazı veri üyeleri eksik bir türü bir önceki sürümünden verileri geliyorsa, bu nedenle, veri üyeleri doğru (hedeflenen varsayılan değerlere) başlatılmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="e52bb-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="e52bb-118">Bu durumu düzeltmek için geri çağırma yöntemi ile işaretlenen kullanın <xref:System.Runtime.Serialization.OnDeserializingAttribute>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e52bb-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="e52bb-119">Tür başına yalnızca bir yöntem ile önceki geri çağırma özniteliklerin her birini işaretleme yapabilirler.</span><span class="sxs-lookup"><span data-stu-id="e52bb-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e52bb-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="e52bb-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e52bb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e52bb-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="e52bb-122">Sürüme Dayanıklı Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e52bb-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)

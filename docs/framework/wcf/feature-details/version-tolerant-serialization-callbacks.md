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
ms.openlocfilehash: 84e38451f10acc341642c0bf0923cc73b79d771f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497938"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="ebf72-102">Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları</span><span class="sxs-lookup"><span data-stu-id="ebf72-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="ebf72-103">Veri sözleşmesi programlama modeli tam sürüm toleranslı seri hale getirme geri çağırma yöntemlerini destekler, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> sınıfları desteği.</span><span class="sxs-lookup"><span data-stu-id="ebf72-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="ebf72-104">Sürüm toleranslı öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="ebf72-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="ebf72-105">Dört geri çağırma özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="ebf72-105">There are four callback attributes.</span></span> <span data-ttu-id="ebf72-106">Her özniteliğin serileştirme/seri durumdan çıkarma altyapısı çeşitli zamanlarda çağıran bir yöntemi uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ebf72-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="ebf72-107">Aşağıdaki tabloda her özniteliği kullanıldığı durumlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ebf72-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="ebf72-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ebf72-108">Attribute</span></span>|<span data-ttu-id="ebf72-109">İlgili yöntem olduğunda çağrılır</span><span class="sxs-lookup"><span data-stu-id="ebf72-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="ebf72-110">Türü seri hale getirme önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ebf72-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="ebf72-111">Türü seri hale getirme sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ebf72-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="ebf72-112">Türü seri durumdan önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ebf72-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="ebf72-113">Türü seri durumdan sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ebf72-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="ebf72-114">Yöntemleri kabul etmelisiniz bir <xref:System.Runtime.Serialization.StreamingContext> parametresi.</span><span class="sxs-lookup"><span data-stu-id="ebf72-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="ebf72-115">Bu yöntemler öncelikle sürüm oluşturma veya başlatma ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ebf72-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="ebf72-116">Seri durumdan çıkarma sırasında oluşturucu yok denir.</span><span class="sxs-lookup"><span data-stu-id="ebf72-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="ebf72-117">Bu üyeler için verileri gelen akışta, örneğin, yoksa veri bazı veri üyeleri eksik bir türde önceki bir sürümden geliyorsa, bu nedenle, veri üyeleri doğru (hedeflenen varsayılan değerler) başlatılmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="ebf72-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="ebf72-118">Bu sorunu gidermek için işaretlenmiş geri çağırma yöntemini kullanmak <xref:System.Runtime.Serialization.OnDeserializingAttribute>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ebf72-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="ebf72-119">Tür başına yalnızca bir yöntemi önceki geri çağırma özniteliklerinin her biriyle ile işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebf72-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ebf72-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ebf72-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="ebf72-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebf72-121">See Also</span></span>  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 [<span data-ttu-id="ebf72-122">Sürüme Dayanıklı Serileştirme</span><span class="sxs-lookup"><span data-stu-id="ebf72-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)

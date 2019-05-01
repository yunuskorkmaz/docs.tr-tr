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
# <a name="version-tolerant-serialization-callbacks"></a>Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları
Veri sözleşmesi programlama modeli tam sürüme dayanıklı serileştirme geri çağırma yöntemleri destekler, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> destek sınıfları.  
  
## <a name="version-tolerant-attributes"></a>Sürüm toleranslı öznitelikleri  
 Dört geri çağırma özniteliği vardır. Her öznitelik, serileştirme/seri durumundan çıkarma altyapısı çeşitli zamanlarda çağıran yönteme uygulanabilir. Aşağıdaki tabloda her bir öznitelik kullanıldığı durumlar açıklanmaktadır.  
  
|Öznitelik|İlgili yöntem olduğunda çağrılır|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Türü serileştirme önce çağrılır.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Türü seri hale getirme sonra çağrılır.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Türü seri durumdan çıkarılırken önce çağrılır.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Türü seri durumdan çıkarılırken sonra çağrılır.|  
  
 Yöntemleri kabul etmesi gereken bir <xref:System.Runtime.Serialization.StreamingContext> parametresi.  
  
 Bu yöntemler, sürüm oluşturma veya başlatma kullanmak için öncelikle yöneliktir. Hiçbir oluşturucuya seri durumundan çıkarma sırasında çağrılır. Bu üyeleri için verileri gelen akışta, örneğin, eksikse, bazı veri üyeleri eksik bir türü bir önceki sürümünden verileri geliyorsa, bu nedenle, veri üyeleri doğru (hedeflenen varsayılan değerlere) başlatılmamış olabilir. Bu durumu düzeltmek için geri çağırma yöntemi ile işaretlenen kullanın <xref:System.Runtime.Serialization.OnDeserializingAttribute>, aşağıdaki örnekte gösterildiği gibi.  
  
 Tür başına yalnızca bir yöntem ile önceki geri çağırma özniteliklerin her birini işaretleme yapabilirler.  
  
### <a name="example"></a>Örnek  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [Sürüme Dayanıklı Serileştirme](../../../../docs/standard/serialization/version-tolerant-serialization.md)

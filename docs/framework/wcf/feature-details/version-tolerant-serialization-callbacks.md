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
# <a name="version-tolerant-serialization-callbacks"></a>Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları
Veri sözleşmesi programlama modeli, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> sınıflarının desteklediği sürüm dayanıklı serileştirme geri çağırma yöntemlerini tam olarak destekler.  
  
## <a name="version-tolerant-attributes"></a>Sürüm dayanıklı öznitelikler  
 Dört geri çağrı özniteliği vardır. Her öznitelik, serileştirme/seri kaldırma altyapısının çeşitli zamanlarda çağırdığı bir yönteme uygulanabilir. Aşağıdaki tabloda her bir özniteliğin ne zaman kullanılacağı açıklanmaktadır.  
  
|Öznitelik|Karşılık gelen yöntem çağrıldığında|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Tür serileştirilden önce çağırılır.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Tür serileştirildikten sonra çağırılır.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Türü seri durumdan çıkarılırken çağırılır.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Türün serisi kaldırıldıktan sonra çağırılır.|  
  
 Yöntemler bir <xref:System.Runtime.Serialization.StreamingContext> parametreyi kabul etmelidir.  
  
 Bu yöntemler öncelikle sürüm oluşturma veya başlatma ile kullanılmak üzere tasarlanmıştır. Seri durumdan çıkarma sırasında hiçbir Oluşturucu çağrılmaz. Bu nedenle, veri üyeleri gelen akışta eksik (örneğin, veriler, bazı veri üyelerini içermeyen bir türün önceki bir sürümünden geliyorsa), bu üyelerin verileri doğru başlatılmamış olabilir (amaçlanan varsayılan değerlere göre). Bunu düzeltmek için, aşağıdaki örnekte gösterildiği gibi, ile <xref:System.Runtime.Serialization.OnDeserializingAttribute>işaretlenmiş geri çağırma yöntemini kullanın.  
  
 Yukarıdaki geri çağırma özniteliklerinin her biri ile, her tür için yalnızca bir yöntem işaretleyebilirsiniz.  
  
### <a name="example"></a>Örnek  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [Sürüme Dayanıklı Serileştirme](../../../standard/serialization/version-tolerant-serialization.md)

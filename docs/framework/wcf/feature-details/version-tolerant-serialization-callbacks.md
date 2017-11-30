---
title: "Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c00cadd4b0e643e35f7f56a28760e261c423699
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="version-tolerant-serialization-callbacks"></a>Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları
Veri sözleşmesi programlama modeli tam sürüm toleranslı seri hale getirme geri çağırma yöntemlerini destekler, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> sınıfları desteği.  
  
## <a name="version-tolerant-attributes"></a>Sürüm toleranslı öznitelikleri  
 Dört geri çağırma özniteliği vardır. Her özniteliğin serileştirme/seri durumdan çıkarma altyapısı çeşitli zamanlarda çağıran bir yöntemi uygulanabilir. Aşağıdaki tabloda her özniteliği kullanıldığı durumlar açıklanmaktadır.  
  
|Öznitelik|İlgili yöntem olduğunda çağrılır|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Türü seri hale getirme önce çağrılır.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Türü seri hale getirme sonra çağrılır.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Türü seri durumdan önce çağrılır.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Türü seri durumdan sonra çağrılır.|  
  
 Yöntemleri kabul etmelisiniz bir <xref:System.Runtime.Serialization.StreamingContext> parametresi.  
  
 Bu yöntemler öncelikle sürüm oluşturma veya başlatma ile kullanılmak üzere tasarlanmıştır. Seri durumdan çıkarma sırasında oluşturucu yok denir. Bu üyeler için verileri gelen akışta, örneğin, yoksa veri bazı veri üyeleri eksik bir türde önceki bir sürümden geliyorsa, bu nedenle, veri üyeleri doğru (hedeflenen varsayılan değerler) başlatılmamış olabilir. Bu sorunu gidermek için işaretlenmiş geri çağırma yöntemini kullanmak <xref:System.Runtime.Serialization.OnDeserializingAttribute>, aşağıdaki örnekte gösterildiği gibi.  
  
 Tür başına yalnızca bir yöntemi önceki geri çağırma özniteliklerinin her biriyle ile işaretleyebilirsiniz.  
  
### <a name="example"></a>Örnek  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 [Sürüm dayanıklı seri hale getirme](../../../../docs/standard/serialization/version-tolerant-serialization.md)

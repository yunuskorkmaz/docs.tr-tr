---
title: İleri Uyumlu Veri Sözleşmeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 34bde56b78ec0148cf6b924f8edd29343b97faa4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597390"
---
# <a name="forward-compatible-data-contracts"></a>İleri Uyumlu Veri Sözleşmeleri
Windows Communication Foundation (WCF) veri sözleşmesi sisteminin bir özelliği, sözleşmelerin zaman içinde bölünemez yollarla gelişebilmesidir. Diğer bir deyişle, bir veri sözleşmesinin eski sürümüne sahip bir istemci aynı veri sözleşmesinin daha yeni bir sürümüyle iletişim kurabilir veya bir veri sözleşmesinin daha yeni bir sürümünü içeren bir istemci aynı veri sözleşmesinin daha eski bir sürümüyle iletişim kurabilir. Daha fazla bilgi için bkz. [En Iyi uygulamalar: veri sözleşmesi sürümü oluşturma](../best-practices-data-contract-versioning.md).  
  
 Mevcut bir veri sözleşmesinin yeni sürümleri oluşturulduğunda, sürüm oluşturma özelliklerinin çoğunu gereken bir şekilde uygulayabilirsiniz. Ancak, bir sürüm oluşturma özelliğinin *, doğru*şekilde çalışması için ilk sürümden türün içine yerleşik olması gerekir.  
  
## <a name="round-tripping"></a>Gidiş dönüşü  
 Veriler yeni bir sürümden eski bir sürüme geçtiğinde ve bir veri sözleşmesinin yeni sürümüne geri geçtiğinde, gidiş dönüş oluşur. Gidiş dönüşü, hiçbir veri kaybolmamasını garanti eder. Gidiş dönüşü etkinleştirmek, daha sonra veri sözleşmesi sürüm oluşturma modeli tarafından desteklenen herhangi bir değişiklik ile tür ileri uyumlu hale getirir.  
  
 Belirli bir tür için gidiş-dönüşü etkinleştirmek üzere, türünün arabirimini uygulaması gerekir <xref:System.Runtime.Serialization.IExtensibleDataObject> . Arabirim bir özellik içerir <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> ( <xref:System.Runtime.Serialization.ExtensionDataObject> türü döndürülüyor). Özelliği, geçerli sürüme bilinmeyen veri sözleşmesinin gelecekteki sürümlerindeki tüm verileri depolar.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki veri sözleşmesi gelecekteki değişikliklerle ileri uyumlu değildir.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Türü gelecekteki değişikliklerle uyumlu hale getirmek için ("phoneNumber" adlı yeni bir veri üyesi ekleme gibi), <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimini uygulayın.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 WCF altyapısı özgün veri sözleşmesinin parçası olmayan verilerle karşılaştığında, veriler özellikte depolanır ve korunur. Geçici depolama dışında başka hiçbir şekilde işlenmez. Nesne kaynağına geri döndürülürse, özgün (bilinmeyen) veriler de döndürülür. Bu nedenle, veriler, kayıp olmadan kaynak uç noktasından bir gidiş dönüş yaptı. Ancak, kaynak uç noktası işlenecek verileri gerektiriyorsa, beklenme karşılanmadığını ve uç noktanın değişikliği algılaması ve buna uyum sağlaması gerektiğini unutmayın.  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject>Tür hiçbir ortak yöntem veya özellik içermiyor. Bu nedenle, özelliğin içinde depolanan verilere doğrudan erişim sağlamak olanaksızdır <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> .  
  
 Gidiş-dönüşü özelliği, `ignoreExtensionDataObject` oluşturucuda olarak ayarlanarak `true` veya özelliği ' de <xref:System.Runtime.Serialization.DataContractSerializer> olarak ayarlanarak kapalı olabilir <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> `true` <xref:System.ServiceModel.ServiceBehaviorAttribute> . Bu özellik kapalıyken, seri durumdan çıkarma <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliği görünmez ve seri hale getirici özelliğin içeriğini göstermeyecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- [Veri Sözleşmesi Sürümü Oluşturma](data-contract-versioning.md)
- [En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma](../best-practices-data-contract-versioning.md)

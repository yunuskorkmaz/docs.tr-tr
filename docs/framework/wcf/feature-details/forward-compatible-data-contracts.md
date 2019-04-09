---
title: İleri Uyumlu Veri Sözleşmeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 90d9409d7e41ddda99caf24ebe0e249ee04723d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095899"
---
# <a name="forward-compatible-data-contracts"></a>İleri Uyumlu Veri Sözleşmeleri
Bir özellik, Windows Communication Foundation (veri sözleşme sistem sözleşmelerin WCF) zaman içindeki bölünemez şekilde geliştirebilirsiniz. Diğer bir deyişle, bir istemci bir veri anlaşması daha eski bir sürümüyle aynı veri anlaşması bir sürüme sahip bir hizmet ile iletişim kurabilir veya bir istemci bir veri anlaşması'nın daha yeni bir sürümü ile aynı veri anlaşması daha eski bir sürümü ile iletişim kurabilir. Daha fazla bilgi için [en iyi uygulamalar: Veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
 Mevcut bir veri anlaşması yeni sürümlerini oluşturulduğunda bir gerektiği şekilde sürüm oluşturma özelliklerinin çoğu uygulayabilirsiniz. Ancak, bir sürüm oluşturma özelliği, *gidiş dönüşü*, ilk sürüm türünden düzgün çalışması için yerleşik gerekir.  
  
## <a name="round-tripping"></a>Gidiş dönüşü  
 Gidiş dönüşü, verileri yeni bir sürümü eski bir sürüm ve tekrar yeni bir veri sözleşmesi sürümü başarılı olduğunda gerçekleşir. Gidiş dönüşü, veri kaybı olmamasına garanti eder. Gidiş dönüşü etkinleştirme İleri uyumlu veri sözleşmesi sürümü oluşturma modeli tarafından desteklenen tüm gelecek değişiklikler ile yapar.  
  
 Belirli bir tür için gidiş dönüşü etkinleştirmek için tür uygulamalıdır <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Arabirim bir özellik içeren <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (döndüren <xref:System.Runtime.Serialization.ExtensionDataObject> türü). Özelliği, geçerli sürümü için bilinmeyen veri anlaşması'nın gelecek sürümlerinden herhangi bir veri depolar.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki veri anlaşması ile gelecekteki değişiklikleri İleri uyumlu değil.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Türü gelecekteki değişiklikler (örneğin, "phoneNumber" adlı yeni bir veri üye ekleme) ile uyumlu hale getirmek için uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 WCF altyapısı özgün veri sözleşmesinin bir parçası olmayan veriler karşılaştığında, veriler için özellik içinde saklanan ve korunur. Geçici depolama dışında herhangi bir şekilde işlenmez. Geri kaynaklandığı için nesne döndürülür, özgün (bilinmiyor) veriler de döndürülür. Bu nedenle, veri kaybı olmadan kaynak uç noktası gelen ve gidiş dönüş yaptı. Ancak, işlenecek verileri kaynak uç noktası gerekirse bu beklentisi karşılaşılmamış ve uç nokta şekilde algılamanız ve uyum değişiklik olduğunu unutmayın.  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject> Türü genel yöntem ya da özellikleri içerir. Bu nedenle, içinde depolanan verilere doğrudan erişmek mümkün değildir <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliği.  
  
 Gidiş dönüşü özelliğini ayarlayarak ya da kapalı `ignoreExtensionDataObject` için `true` içinde <xref:System.Runtime.Serialization.DataContractSerializer> Oluşturucusu veya ayarlayarak <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> özelliğini `true` üzerinde <xref:System.ServiceModel.ServiceBehaviorAttribute>. Bu özelliği devre dışıyken seri durumdan çıkarıcı değil doldurmak <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliği ve seri hale getirici ktıları özelliğinin içeriği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- [Veri Sözleşmesi Sürümü Oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [En İyi Yöntemler: Veri Sözleşmesi Sürümü Oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)

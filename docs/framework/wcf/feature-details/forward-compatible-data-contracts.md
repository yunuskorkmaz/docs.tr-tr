---
title: İleri Uyumlu Veri Sözleşmeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 95a72d5d09538bc6f663f2376c7f8f928909cd57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492212"
---
# <a name="forward-compatible-data-contracts"></a>İleri Uyumlu Veri Sözleşmeleri
Bir özellik, Windows Communication Foundation (veri sözleşmesi sistem sözleşmelerin WCF) zamanla bölünemez yollarla gelişmesi. Diğer bir deyişle, bir istemci bir veri sözleşmesi daha eski bir sürümü ile aynı veri sözleşmesi daha yeni bir sürümü olan bir hizmeti ile iletişim kurabilir veya bir istemci bir veri sözleşmesi daha yeni bir sürümü ile aynı veri sözleşmesi daha eski bir sürümü ile iletişim kurabilir. Daha fazla bilgi için bkz: [en iyi uygulamalar: veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
 Var olan bir veri sözleşmeyi yeni sürümlerini oluşturduğunuzda gerektiği ölçüde temeline göre sürüm oluşturma özelliklerinin çoğu uygulayabilirsiniz. Ancak, tek bir sürüm oluşturma özelliği *gidiş*, ilk sürüm türünden düzgün çalışması için yerleşik gerekir.  
  
## <a name="round-tripping"></a>Gidiş  
 Eski bir sürümüne ve tekrar yeni bir veri sözleşmesi sürümü yeni bir sürümden verileri geçirmeden gidiş oluşur. Gidiş veri kaybı olmamasına güvence altına alır. Gidiş etkinleştirme türü ileri uyumlu veri sözleşmesi sürümü oluşturma modeli tarafından desteklenen herhangi bir gelecekteki değişiklikle hale getirir.  
  
 Belirli bir tür için gidiş etkinleştirmek için türü uygulamalıdır <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Bir özellik arabirimi içerir <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (döndürme <xref:System.Runtime.Serialization.ExtensionDataObject> türü). Özelliği için geçerli sürümü bilinmiyor veri sözleşmesi gelecek sürümlerinden herhangi bir veri depolar.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki veri sözleşmesi gelecekteki değişikliklerle İleri uyumlu değil.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Türü (örneğin, "phoneNumber" adlı yeni bir veri üye ekleme) gelecekteki değişiklikler ile uyumlu hale getirmek için uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 WCF altyapı özgün veri sözleşmenin parçası olmayan veriler karşılaştığında, veriler özellikte depolanan ve korunur. Geçici depolama dışında herhangi bir şekilde işlenmez. Nesne geri onu başlatıldığı için döndürülürse, özgün (bilinmiyor) verileri de döndürülür. Bu nedenle, veri kaybı olmadan kaynak uç noktası gelen ve giden gidiş dönüş yaptı. Ancak, kaynak uç noktası işlenecek verileri gerekirse, bu Beklenti unmet, olduğunu unutmayın ve uç nokta gerekir şekilde algılamak ve değişiklik uyum sağlamak.  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject> Türü, genel yöntemleri ya da özellikleri içerir. Bu nedenle, içinde depolanan verilere doğrudan erişmek mümkün değildir <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliği.  
  
 Gidiş özelliğini ayarlayarak ya da kapalı `ignoreExtensionDataObject` için `true` içinde <xref:System.Runtime.Serialization.DataContractSerializer> Oluşturucusu veya ayarlayarak <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> özelliğine `true` üzerinde <xref:System.ServiceModel.ServiceBehaviorAttribute>. Bu özellik devre dışı olduğunda seri durumdan çıkarıcının değil doldurmak <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliği ve seri hale getirici değil yayma özelliğinin içeriği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 [Veri Anlaşması Sürümü Oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)

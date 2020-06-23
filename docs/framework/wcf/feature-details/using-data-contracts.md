---
title: Veri Sözleşmelerini Kullanma
description: Her bir parametre ya da dönüş türü için, bir WCF istemcisi ve sunucusu arasında hangi verilerin değiştirildiğini tanımlayan bir veri sözleşmesi hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 80ea2a8bd67c627fbe11ee07e640704c1a41ef7b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244731"
---
# <a name="using-data-contracts"></a>Veri Sözleşmelerini Kullanma
*Veri anlaşması* , bir hizmet ile bir istemci arasındaki, alışverişe yönelik verileri tanımlayan resmi bir anlaşmadır. Diğer bir deyişle, iletişim için, istemci ve hizmetin aynı türleri paylaşması gerekmez, yalnızca aynı veri sözleşmeleri vardır. Bir veri sözleşmesi, her bir parametre veya dönüş türü için, hangi verilerin (XML 'e açıktır) değiş tokuş edilecek şekilde tam olarak tanımlar.  
  
## <a name="data-contract-basics"></a>Veri sözleşmesi temelleri  
 Windows Communication Foundation (WCF), verileri seri hale getirmek ve seri durumdan çıkarmak (XML 'e dönüştürmek) için varsayılan olarak veri sözleşmesi serileştiricisi adlı bir serileştirme altyapısı kullanır. Tamsayılar ve dizeler gibi basit türlerin yanı sıra, ve gibi temel öğeler olarak değerlendirilen belirli türler, <xref:System.DateTime> <xref:System.Xml.XmlElement> başka bir hazırlık olmadan seri hale getirilebilir ve varsayılan veri sözleşmeleri olduğu kabul edilir. .NET Framework Birçok .NET Framework türü de var olan veri sözleşmeleri de vardır. Seri hale getirilebilir türlerin tam listesi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](types-supported-by-the-data-contract-serializer.md).  
  
 Oluşturduğunuz yeni karmaşık türlerin seri hale getirilebilir olmaları için tanımlanmış bir veri anlaşması olması gerekir. Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesini algılar ve herkese açık olarak görünen tüm türleri seri hale getirir. Türün tüm genel okuma/yazma özellikleri ve alanları serileştirilir. ' İ kullanarak üyeleri Serileştirmeden çevirebilirsiniz <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> . Ayrıca, ve özniteliklerini kullanarak açıkça bir veri sözleşmesi oluşturabilirsiniz <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> . Bu, genellikle türüne özniteliği uygulanarak yapılır <xref:System.Runtime.Serialization.DataContractAttribute> . Bu öznitelik, sınıflara, yapılara ve numaralandırmalara uygulanabilir. <xref:System.Runtime.Serialization.DataMemberAttribute>Daha sonra bu öznitelik, bir *veri üyesi*olduğunu göstermek için veri sözleşmesi türünün her üyesine uygulanmalıdır; yani serileştirilmelidir. Daha fazla bilgi için bkz. [serileştirilebilir türler](serializable-types.md).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.ServiceModel.ServiceContractAttribute> ve özniteliklerinin açıkça uygulandığı bir hizmet sözleşmesini (bir arabirim) gösterir <xref:System.ServiceModel.OperationContractAttribute> . Örnek, basit türlerin bir veri sözleşmesi gerektirmediğinden karmaşık bir tür olduğu gösterilmektedir.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 Aşağıdaki örnek, `MyTypes.PurchaseOrder` <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerini sınıfına ve üyelerine uygulayarak, türü için bir veri sözleşmesinin nasıl oluşturulduğunu gösterir.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Notlar  
 Aşağıdaki notlar, veri sözleşmeleri oluştururken dikkate alınması gereken öğeleri sağlar:  
  
- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>Özniteliği yalnızca işaretsiz türlerle kullanıldığında kabul edilir. Bu,,, veya özniteliklerinden biri ile işaretlenmemiş ya da <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.CollectionDataContractAttribute> <xref:System.Runtime.Serialization.EnumMemberAttribute> başka bir yöntemle seri hale getirilebilir olarak işaretlenen türleri içerir (örneğin, <xref:System.Xml.Serialization.IXmlSerializable> ).  
  
- <xref:System.Runtime.Serialization.DataMemberAttribute>Özniteliği alanlara ve özelliklere uygulayabilirsiniz.  
  
- Üye erişilebilirlik düzeyleri (iç, özel, korumalı veya ortak), veri sözleşmesini herhangi bir şekilde etkilemez.  
  
- <xref:System.Runtime.Serialization.DataMemberAttribute>Özniteliği statik üyelere uygulanmışsa yok sayılır.  
  
- Serileştirme sırasında, özellik veri üyeleri için, seri hale getirilecek özelliklerin değerini almak üzere Property-Get kodu çağırılır.  
  
- Seri durumdan çıkarma sırasında, tür üzerinde herhangi bir Oluşturucu çağrılmadan başlatılmamış bir nesne ilk oluşturulur. Ardından tüm veri üyeleri seri durumdan çıkarılmakta.  
  
- Seri durumdan çıkarma sırasında özellik kümesi kodu, özellik veri üyeleri için, özellikleri seri durumdan çıkarılacak değere ayarlanacak şekilde çağrılır.  
  
- Bir veri sözleşmesinin geçerli olması için, tüm veri üyelerini seri hale getirmek mümkün olmalıdır. Seri hale getirilebilir türlerin tam listesi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](types-supported-by-the-data-contract-serializer.md).  
  
     Genel türler genel olmayan türlerle tamamen aynı şekilde işlenir. Genel parametreler için özel gereksinimler yoktur. Örneğin, aşağıdaki türü göz önünde bulundurun.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Bu tür, genel tür parametresi () için kullanılan türün serileştirilebilir olup olmadığı seri hale getirilebilir `T` . Tüm veri üyelerini seri hale getirmek mümkün olması gerektiğinden, aşağıdaki kodda gösterildiği gibi, genel tür parametresi de seri hale getirilebilir ise aşağıdaki tür serileştirilebilir olur.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Bir veri sözleşmesini tanımlayan bir WCF hizmetinin tüm kod örneği için bkz. [temel veri sözleşmesi](../samples/basic-data-contract.md) örneği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Seri Hale Getirilebilir Türler](serializable-types.md)
- [Veri Sözleşmesi Adları](data-contract-names.md)
- [Veri Sözleşmesi Eşitliği](data-contract-equivalence.md)
- [Veri Üye Sırası](data-member-order.md)
- [Veri Anlaşması Bilinen Türler](data-contract-known-types.md)
- [İleri Uyumlu Veri Sözleşmeleri](forward-compatible-data-contracts.md)
- [Veri Sözleşmesi Sürümü Oluşturma](data-contract-versioning.md)
- [Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları](version-tolerant-serialization-callbacks.md)
- [Veri Üyesi Varsayılan Değerler](data-member-default-values.md)
- [Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler](types-supported-by-the-data-contract-serializer.md)
- [Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)

---
title: "Veri Sözleşmelerini Kullanma"
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
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
caps.latest.revision: "38"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 258e7fd0235ffa67ee8c293831cb8230d48a894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-data-contracts"></a>Veri Sözleşmelerini Kullanma
A *veri sözleşmesi* hizmet bağlamalarında değiştirilebilmesi için verileri tanımlayan bir istemci arasındaki resmi anlaşması. Diğer bir deyişle, iletişim kurmak için istemci ve hizmet aynı türleri, yalnızca aynı veri sözleşmeleri paylaşmak gerekmez. Veri sözleşmesi tam olarak, hangi verilerin (XML içinde açık) serileştirilmiş her parametresi ya da döndürme türü için tanımlar değiştirilmek üzere.  
  
## <a name="data-contract-basics"></a>Veri sözleşmesi temelleri  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]seri hale getirmek ve (XML gelen ve giden dönüştürmeden) veri serisi için varsayılan olarak veri sözleşmesi seri hale getirici adlı bir seri hale getirme altyapısı kullanır. Tüm [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tamsayılar ve dizeler gibi ilkel türler ve bunun yanı sıra belirli türleri gibi temel olarak kabul <xref:System.DateTime> ve <xref:System.Xml.XmlElement>ile başka bir hazırlık olmadan seri hale ve varsayılan veri sözleşmeleri sahip olarak kabul edilir. Birçok [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri mevcut veri sözleşmeleri de. Seri hale getirilebilir türlerinin tam listesi için bkz: [veri sözleşmesi seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Oluşturduğunuz yeni karmaşık türleri seri hale getirilebilir kendileri için tanımlanmış bir veri sözleşmesi olması gerekir. Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesi oluşturur ve tüm herkese görünür türleri serileştirir. Tüm ortak okuma/yazma özellikleri ve türünde alanlar serileştirilir. Seri hale getirme üyelerinden çıkışı kullanarak seçebilirsiniz <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>. Kullanarak bir veri sözleşmesi açıkça oluşturabilirsiniz <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri. Bu normalde uygulanarak yapılır <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik türü. Bu öznitelik, sınıflar, yapılar ve numaralandırmaları uygulanabilir. <xref:System.Runtime.Serialization.DataMemberAttribute> Özniteliği her bir üyesi olduğunu belirtmek için veri sözleşmesi türü sonra uygulanmalıdır bir *veri üyesi*, diğer bir deyişle, serileştirilmelidir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir hizmet sözleşmesini (bir arabirim) olduğu gösterilmektedir <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri açıkça uygulandı. Bu örnek, bir karmaşık türü sırada ilkel türler bir veri sözleşmesi gerektirmeyen gösterir.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 Aşağıdaki örnek, bir veri sözleşmesi için nasıl gösterir `MyTypes.PurchaseOrder` türü uygulayarak oluşturulur <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı ve üyelerini öznitelikleri.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Notlar  
 Aşağıdaki Notlar veri sözleşmeleri oluştururken dikkate alınması gereken öğeler sağlar:  
  
-   <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> Özniteliği yalnızca dikkate işaretsiz türleri ile kullanıldığında. Bu biri ile işaretlenmemiş türleri içerir <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, veya <xref:System.Runtime.Serialization.EnumMemberAttribute> öznitelikleri veya diğer herhangi bir yolla seri hale getirilebilir olarak işaretlenmiş (gibi <xref:System.Xml.Serialization.IXmlSerializable>).  
  
-   Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği alanlar ve özellikler.  
  
-   Üye erişilebilirlik düzeyleri (iç, özel, korumalı veya ortak) herhangi bir şekilde veri sözleşmesi etkilemez.  
  
-   <xref:System.Runtime.Serialization.DataMemberAttribute> Özniteliği için statik üyeler uygulanırsa yoksayılır.  
  
-   Seri hale getirme sırasında get özelliği kod serileştirilmesi için özellikler değerini almak özellik veri üyeleri için çağrılır.  
  
-   Seri durumdan çıkarma sırasında başlatılmamış bir nesneye önce tüm oluşturucular türüne çağırmadan oluşturulur. Ardından tüm veri üyeleri serisi.  
  
-   Seri durumdan çıkarma sırasında seri durumdan çıkarılmakta değerine özelliklerini ayarlamak özellik veri üyeleri için özellik kümesi kod çağrılır.  
  
-   Bir veri sözleşmesi geçerli olması, tüm veri üyeleri serileştirmek olası olmalıdır. Seri hale getirilebilir türlerinin tam listesi için bkz: [veri sözleşmesi seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
     Genel türler genel olmayan türleri ile aynı şekilde ele alınır. Genel parametreler için özel gereksinimi yoktur. Örneğin, aşağıdaki tür göz önünde bulundurun.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Bu tür genel tür parametresi için kullanılıp seri hale getirilebilir türüdür (`T`) seri hale getirilebilir olup. Tüm veri üyeleri serileştirmek mümkün olması nedeniyle şu türü yalnızca genel tür parametresi de aşağıdaki kodda gösterildiği gibi seri hale getirilebilir, seri hale getirilebilir yapmasıdır.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Veri sözleşmesi tanımlayan WCF hizmeti bir tam kod örnek için bkz [temel veri sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md) örnek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [Seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [Veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Veri sözleşmesi eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [Veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [Veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Sürüm toleranslı seri hale getirme geri çağrıları](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [Veri üyesi varsayılan değerler](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)  
 [Veri sözleşmesi seri hale getirici tarafından desteklenen türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)  
 [Nasıl yapılır: bir sınıf veya yapı için bir temel veri sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)

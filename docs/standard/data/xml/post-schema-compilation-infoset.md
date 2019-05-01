---
title: Şema Derleme Sonrası Bilgi Kümesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e7892289248c9651b529bcc68d7228b8babb28a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949506"
---
# <a name="post-schema-compilation-infoset"></a>Şema Derleme Sonrası Bilgi Kümesi
[World Wide Web Consortium (W3C) XML Şeması öneri](https://www.w3.org/XML/Schema) öncesi şema doğrulama ve şema derleme için sunulmalıdır bilgisi kümesi (bilgi kümesi) ele alınmaktadır. XML şema nesne modeli (SOM) önce ve sonra bu Etkilenme görünümleri <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> çağrılır.  
  
 Öncesi schema doğrulama bilgi kümesi şemasını düzenleme sırasında oluşturulmuştur. Şema derleme sonrası bilgi kümesi sonra oluşturulan <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> şemanın derlenmesi sırasında çağrılır ve özellikler olarak gösterilir.  
  
 SOM öncesi şema doğrulama ve şema derleme infosets temsil eden nesne modelidir; sınıflarda oluşan <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı. Tüm okuma ve yazma özellikleri sınıflarda oluşan <xref:System.Xml.Schema> ad alanı ait sınıflarda salt okunur tüm özelliklerini sırasında öncesi schema doğrulama bilgi kümesi <xref:System.Xml.Schema> ad alanı için şema derleme sonrası bilgi kümesi ait. Bu kuralın istisnası olarak, hem ön schema doğrulama bilgi kümesi hem de şema derleme sonrası bilgi kümesi özellikleri aşağıdaki özellikleri olan.  
  
|örneği|Özellik|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Örneğin, <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaComplexType> sınıflarının her ikisi de `BlockResolved` ve `FinalResolved` özellikleri. Bu özelliklerin değerlerini tutmak için kullanılan `Block` ve `Final` şema derlenen ve doğrulandı sonra özellikleri. `BlockResolved` ve `FinalResolved` şema derleme sonrası bilgi kümesi parçası olan salt okunur özelliklerdir.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> sınıf kümesi şeması doğruladıktan sonra. Doğrulama önce özelliği içeren bir `null` başvuru ve <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> türü adına söz konusu ayarlanır. Doğrulama sonrasında <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> geçerli bir tür olarak çözümlenir ve tür nesnesi aracılığıyla kullanılabilir <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> özelliği.  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)

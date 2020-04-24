---
title: Şema Derleme Sonrası Bilgi Kümesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
ms.openlocfilehash: 016032b2b37ced5592edc18934ed183c475f5598
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710485"
---
# <a name="post-schema-compilation-infoset"></a>Şema Derleme Sonrası Bilgi Kümesi
[World Wide Web Konsorsiyumu (W3C) XML şeması önerisi](https://www.w3.org/XML/Schema) , şema öncesi doğrulama ve şema sonrası derleme için açığa çıkarılması gereken bilgi kümesini (Infoset) açıklar. XML şeması nesne modeli (SOM), <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> Bu pozlamayı ' ın yönteminden önce ve sonra görüntüler.  
  
 Şema düzenlemesi sırasında şema öncesi doğrulama bilgi kümesi oluşturulur. Şema sonrası derleme bilgi kümesi, şema derlenirken, öğesinin <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> yöntemi çağırılır ve özellikler olarak gösterilir.  
  
 SOM, şema öncesi doğrulama ve şema sonrası derleme bilgi kümelerini temsil eden nesne modelidir; <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki sınıflardan oluşur. <xref:System.Xml.Schema> Ad alanındaki sınıfların tüm okuma ve yazma özellikleri, ön şema doğrulama bilgi kümesine aittir, ancak <xref:System.Xml.Schema> ad alanındaki sınıfların tüm salt okuma özellikleri şema sonrası derleme bilgi kümesine aittir. Bu kuralın istisnası, hem şema öncesi doğrulama bilgi kümesi hem de şema sonrası derleme bilgi kümesi özellikleri olan aşağıdaki özelliklerdir.  
  
|Sınıf|Özellik|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Örneğin, <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaComplexType> sınıflarının her ikisi de `BlockResolved` ve `FinalResolved` özelliklerdir. Bu özellikler, `Block` şema derlendikten ve doğrulandıktan sonra ve `Final` özellikleri için değerleri tutmak üzere kullanılır. `BlockResolved`ve `FinalResolved` şema sonrası derleme bilgi kümesinin parçası olan salt yazılır özelliklerdir.  
  
 Aşağıdaki örnek, şema doğrulandıktan <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> sonra <xref:System.Xml.Schema.XmlSchemaElement> sınıf kümesinin özelliğini gösterir. Doğrulamadan önce, özelliği bir `null` başvuru içerir ve bu, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> söz konusu türün adına ayarlanır. Doğrulamadan <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> sonra, geçerli bir tür olarak çözümlenir ve tür nesnesi <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> özelliği aracılığıyla kullanılabilir.  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)

---
title: XML Belgelerinden Şema Çıkarımı Yapma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 5c2d997d9006a3f1eb971eac20982b9dd5677ebf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710758"
---
# <a name="inferring-schemas-from-xml-documents"></a>XML Belgelerinden Şema Çıkarımı Yapma
Bu konu, bir XML belgesi yapısından bir XML şeması tanım dili (XSD) şeması çıkarsmak için <xref:System.Xml.Schema.XmlSchemaInference> sınıfının nasıl kullanılacağını açıklar.  
  
## <a name="the-schema-inference-process"></a>Şema çıkarımı Işlemi  
 <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanının <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, bir XML belgesi yapısından bir veya daha fazla XML şeması tanım dili (XSD) şeması oluşturmak için kullanılır. Oluşturulan şemalar özgün XML belgesini doğrulamak için kullanılabilir.  
  
 Bir XML belgesi <xref:System.Xml.Schema.XmlSchemaInference> sınıfı tarafından işlendiği için <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, XML belgesindeki öğeleri ve öznitelikleri tanımlayan şema bileşenleriyle ilgili varsayımlar yapar. <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, belirli bir öğe veya öznitelik için en kısıtlayıcı türü azaltarak, şema bileşenlerini kısıtlanmış bir şekilde de algılar. XML belgesi hakkında daha fazla bilgi toplandığından, bu kısıtlamalar daha az kısıtlayıcı olan türleri azaltarak gevşur. Çıkarsanan en az kısıtlayıcı tür `xs:string`.  
  
 Örneğin, bir XML belgesinin aşağıdaki parçasını alın.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 Yukarıdaki örnekte, `attribute1` özniteliğine <xref:System.Xml.Schema.XmlSchemaInference> işlem tarafından `6` değeri ile karşılaşıldığında, `xs:unsignedByte`türünde olduğu varsayılır. İkinci `parent` öğesi <xref:System.Xml.Schema.XmlSchemaInference> işlem tarafından karşılaşıldığında, `attribute1` özniteliğinin değeri artık `A`olduğundan, kısıtlama, türü `xs:string` olarak değiştirilerek gevşendi. Benzer şekilde, şemada gösterilen tüm `child` öğeleri için `minOccurs` özniteliği, ikinci üst öğenin alt öğeleri olmadığından `minOccurs="0"` için gevşulmuş.  
  
## <a name="inferring-schemas-from-xml-documents"></a>XML Belgelerinden Şema Çıkarımı Yapma  
 <xref:System.Xml.Schema.XmlSchemaInference> sınıfı bir XML belgesinden şemayı çıkarması için iki aşırı yüklenmiş <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi kullanır.  
  
 İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi, bir XML belgesini temel alan bir şema oluşturmak için kullanılır. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi, birden çok XML belgesini açıklayan bir şemayı çıkarmakta kullanılır. Örneğin, tüm XML belgesi kümesini açıklayan bir şema oluşturmak için birden çok XML belgesini tek seferde <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemine ekleyebilirsiniz.  
  
 İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi bir <xref:System.Xml.XmlReader> nesnesinde bulunan bir XML belgesinden şemayı içerir ve çıkarılan şemayı içeren bir <xref:System.Xml.Schema.XmlSchemaSet> nesnesi döndürür. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi, <xref:System.Xml.XmlReader> nesnesinde bulunan XML belgesiyle aynı hedef ad alanına sahip bir şema için bir <xref:System.Xml.Schema.XmlSchemaSet> nesnesi arar, varolan şemayı iyileştirir ve çıkarılan şemayı içeren bir <xref:System.Xml.Schema.XmlSchemaSet> nesnesi döndürür.  
  
 İyileştirilmiş şemada yapılan değişiklikler XML belgesinde bulunan yeni yapıyı temel alır. Örneğin, bir XML belgesi çapraz yapıldıkça, bulunan veri türleri hakkında varsayımlar yapılır ve şema bu varsayımlar temel alınarak oluşturulur. Ancak, özgün varsayıma göre farklılık gösteren ikinci bir çıkarım geçişinde veriye karşılaşılırsa, şema iyileştirilmektedir. Aşağıdaki örnek, iyileştirme sürecini gösterir.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 Örnek, `item1.xml`ilk giriş olarak aşağıdaki dosyayı alır.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Örnek, `item2.xml` dosyayı ikinci girdi olarak alır:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 İlk XML belgesinde `productID` özniteliği ile karşılaşıldığında, `123456789` değerinin `xs:unsignedInt` bir tür olduğu varsayılır. Ancak, ikinci XML belgesi okunmadıysa ve `A53-246` değeri bulunursa `xs:unsignedInt` tür artık kabul edilebilir. Şema iyileştirilmektedir ve `productID` türü `xs:string`olarak değiştirilir. Ayrıca, `supplierID` öğesi için `minOccurs` özniteliği `0`olarak ayarlanır, çünkü ikinci XML belgesi `supplierID` öğesi içermiyor.  
  
 İlk XML belgesinden çıkarılan şema aşağıda verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Aşağıda, birinci XML belgesinden çıkarılan ve ikinci XML belgesi tarafından iyileştirilmiş şema verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Satır içi şemalar  
 <xref:System.Xml.Schema.XmlSchemaInference> işlemi sırasında satır içi XML şeması tanım dili (XSD) şemasına karşılaşılırsa, bir <xref:System.Xml.Schema.XmlSchemaInferenceException> oluşturulur. Örneğin, aşağıdaki satır içi şema bir <xref:System.Xml.Schema.XmlSchemaInferenceException>oluşturur.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Iyileştirilelemez şemalar  
 XML şeması tanım dili (XSD) şeması <xref:System.Xml.Schema.XmlSchemaInference> işlem, iyileştirmek için bir tür verildiyse ve bir özel durumun oluşturulmasına neden olursa, XML şema tanımı dili (XSD) şema işleme tarafından işleyemeyebilir. Üst düzey kompozisyonu bir sıra dışında herhangi bir şey olan karmaşık bir tür gibi. Şema nesne modelinde (SOM), bu, <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSequence>örneği olmayan bir <xref:System.Xml.Schema.XmlSchemaComplexType> karşılık gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaInference>
- [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
- [Basit Türlerin Çıkarımını Yapma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)

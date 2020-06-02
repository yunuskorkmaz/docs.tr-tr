---
title: XML Belgelerinden Şema Çıkarımı Yapma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 5b0f9bea33346083ce0015fbf3cdfeb0e0ea1181
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287668"
---
# <a name="inferring-schemas-from-xml-documents"></a>XML Belgelerinden Şema Çıkarımı Yapma
Bu konuda, sınıfının bir XML <xref:System.Xml.Schema.XmlSchemaInference> belgesi yapısından BIR XML şeması tanım dili (xsd) şeması çıkarması için nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="the-schema-inference-process"></a>Şema çıkarımı Işlemi  
 <xref:System.Xml.Schema.XmlSchemaInference>Ad alanı sınıfı, <xref:System.Xml.Schema?displayProperty=nameWithType> bir XML belgesi yapısından bir veya daha fazla XML şeması tanım DILI (xsd) şeması oluşturmak için kullanılır. Oluşturulan şemalar özgün XML belgesini doğrulamak için kullanılabilir.  
  
 Sınıfı tarafından bir XML belgesi işlendiği için <xref:System.Xml.Schema.XmlSchemaInference> , <xref:System.Xml.Schema.XmlSchemaInference> sınıfı XML belgesindeki öğeleri ve öznitelikleri tanımlayan şema bileşenleriyle ilgili varsayımlar yapar. <xref:System.Xml.Schema.XmlSchemaInference>Sınıfı, belirli bir öğe veya öznitelik için en kısıtlayıcı türü azaltarak, şema bileşenlerini kısıtlanmış bir şekilde de algılar. XML belgesi hakkında daha fazla bilgi toplandığından, bu kısıtlamalar daha az kısıtlayıcı olan türleri azaltarak gevşur. Çıkarsanan en az kısıtlayıcı tür `xs:string` .  
  
 Örneğin, bir XML belgesinin aşağıdaki parçasını alın.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A" />
```  
  
 Yukarıdaki örnekte, `attribute1` özniteliğe işlem tarafından bir değer ile karşılaşıldığında `6` <xref:System.Xml.Schema.XmlSchemaInference> , türünde olduğu varsayılır `xs:unsignedByte` . `parent`İşlem tarafından ikinci öğe ile karşılaşıldığında <xref:System.Xml.Schema.XmlSchemaInference> , `xs:string` özniteliğinin değeri artık olduğundan, kısıtlama, türü olarak değiştirilerek gevşerek yapılır `attribute1` `A` . Benzer şekilde, `minOccurs` `child` şemada çıkarılan tüm öğelerin özniteliği, `minOccurs="0"` ikinci üst öğenin alt öğeleri olmadığından, öğesine gevşulmuş olarak ayarlanır.  
  
## <a name="inferring-schemas-from-xml-documents"></a>XML Belgelerinden Şema Çıkarımı Yapma  
 <xref:System.Xml.Schema.XmlSchemaInference>Sınıfı BIR <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> XML belgesinden şemayı çıkarsmak için iki aşırı yüklenmiş yöntem kullanır.  
  
 İlk yöntem, bir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> XML belgesini temel alan bir şema oluşturmak için kullanılır. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem, birden çok XML belgesini açıklayan bir şemayı çıkarmakta kullanılır. Örneğin, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> tüm XML belgesi kümesini açıklayan bir şema oluşturmak için birden çok XML belgesini tek seferde bir kez akışa aktarabilirsiniz.  
  
 İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem bir nesne içindeki BIR XML belgesinden şemayı içerir <xref:System.Xml.XmlReader> ve <xref:System.Xml.Schema.XmlSchemaSet> çıkarılan şemayı içeren bir nesne döndürür. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem, <xref:System.Xml.Schema.XmlSchemaSet> NESNESINDE bulunan XML belgesiyle aynı hedef ad alanına sahip bir şema için bir nesne arar <xref:System.Xml.XmlReader> , varolan şemayı iyileştirir ve <xref:System.Xml.Schema.XmlSchemaSet> çıkarılan şemayı içeren bir nesne döndürür.  
  
 İyileştirilmiş şemada yapılan değişiklikler XML belgesinde bulunan yeni yapıyı temel alır. Örneğin, bir XML belgesi çapraz yapıldıkça, bulunan veri türleri hakkında varsayımlar yapılır ve şema bu varsayımlar temel alınarak oluşturulur. Ancak, özgün varsayıma göre farklılık gösteren ikinci bir çıkarım geçişinde veriye karşılaşılırsa, şema iyileştirilmektedir. Aşağıdaki örnek, iyileştirme sürecini gösterir.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 Örnek, `item1.xml` ilk girişi olarak aşağıdaki dosyayı alır.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Örnek, `item2.xml` dosyayı ikinci girdi olarak alır:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 `productID`Ilk XML belgesinde özniteliğiyle karşılaşıldığında, değerinin `123456789` bir tür olduğu varsayılır `xs:unsignedInt` . Ancak, ikinci XML belgesi okunmadıysa ve değeri `A53-246` bulunursa, `xs:unsignedInt` tür artık kabul edilebilir değildir. Şema iyileştirilmektedir ve türü `productID` olarak değişir `xs:string` . Ayrıca, `minOccurs` öğesi için özniteliği olarak `supplierID` ayarlanır `0` , çünkü ikinci XML belgesi hiç `supplierID` öğe içermiyor.  
  
 İlk XML belgesinden çıkarılan şema aşağıda verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Aşağıda, birinci XML belgesinden çıkarılan ve ikinci XML belgesi tarafından iyileştirilmiş şema verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Satır içi şemalar  
 İşlem sırasında satır içi bir XML şeması tanım dili (XSD) şemasına karşılaşılırsa <xref:System.Xml.Schema.XmlSchemaInference> , bir oluşturulur <xref:System.Xml.Schema.XmlSchemaInferenceException> . Örneğin, aşağıdaki satır içi şema bir oluşturur <xref:System.Xml.Schema.XmlSchemaInferenceException> .  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Iyileştirilelemez şemalar  
 XML şeması tanım dili (XSD) şema <xref:System.Xml.Schema.XmlSchemaInference> işleminin, daraltmak için bir tür verildiyse ve bir özel durumun oluşturulmasına neden olması halinde işleyememesi gereken W3C xml şema yapıları vardır. Üst düzey kompozisyonu bir sıra dışında herhangi bir şey olan karmaşık bir tür gibi. Şema nesne modelinde (SOM), bu bir <xref:System.Xml.Schema.XmlSchemaComplexType> <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> özelliği bir örneği olmayan öğesine karşılık gelir <xref:System.Xml.Schema.XmlSchemaSequence> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaInference>
- [XML Şema Nesne Modeli (SOM)](xml-schema-object-model-som.md)
- [XML Şemasından Çıkarım Yapma](inferring-an-xml-schema.md)
- [Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları](rules-for-inferring-schema-node-types-and-structure.md)
- [Basit Türlerin Çıkarımını Yapma Kuralları](rules-for-inferring-simple-types.md)

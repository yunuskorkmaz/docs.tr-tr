---
title: XML Belgelerinden Şema Çıkarımı Yapma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 2d991a7835d22af2c780b020d6884f626908665e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796177"
---
# <a name="inferring-schemas-from-xml-documents"></a>XML Belgelerinden Şema Çıkarımı Yapma
Bu konuda, <xref:System.Xml.Schema.XmlSchemaInference> sınıfının bir XML belgesi YAPıSıNDAN bir XML şeması tanım DILI (xsd) şeması çıkarması için nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="the-schema-inference-process"></a>Şema çıkarımı Işlemi  
 <xref:System.Xml.Schema?displayProperty=nameWithType> Ad alanı <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, bir XML belgesi yapısından BIR veya daha fazla XML ŞEMASı tanım dili (xsd) şeması oluşturmak için kullanılır. Oluşturulan şemalar özgün XML belgesini doğrulamak için kullanılabilir.  
  
 Sınıfı tarafından <xref:System.Xml.Schema.XmlSchemaInference> bir XML belgesi işlendiği için, <xref:System.Xml.Schema.XmlSchemaInference> sınıfı XML belgesindeki öğeleri ve öznitelikleri tanımlayan şema bileşenleriyle ilgili varsayımlar yapar. Sınıfı <xref:System.Xml.Schema.XmlSchemaInference> , belirli bir öğe veya öznitelik için en kısıtlayıcı türü azaltarak, şema bileşenlerini kısıtlanmış bir şekilde de algılar. XML belgesi hakkında daha fazla bilgi toplandığından, bu kısıtlamalar daha az kısıtlayıcı olan türleri azaltarak gevşur. Çıkarsanan en az kısıtlayıcı tür `xs:string`.  
  
 Örneğin, bir XML belgesinin aşağıdaki parçasını alın.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A" />
```  
  
 `attribute1` Yukarıdaki örnekte, `6` özniteliğe <xref:System.Xml.Schema.XmlSchemaInference> işlem tarafından bir değer ile karşılaşıldığında, türünde `xs:unsignedByte`olduğu varsayılır. <xref:System.Xml.Schema.XmlSchemaInference> İşlem `xs:string` tarafından ikinci `parent` öğe ile karşılaşıldığında, `attribute1` özniteliğinin değeri artık `A`olduğundan, kısıtlama, türü olarak değiştirilerek gevşerek yapılır. Benzer şekilde, `minOccurs` şemada çıkarılan tüm `child` öğelerin özniteliği, ikinci üst öğenin alt öğeleri olmadığından, öğesine `minOccurs="0"` gevşulmuş olarak ayarlanır.  
  
## <a name="inferring-schemas-from-xml-documents"></a>XML Belgelerinden Şema Çıkarımı Yapma  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfı bir XML belgesinden şemayı <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> çıkarsmak için iki aşırı yüklenmiş yöntem kullanır.  
  
 İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem, bir XML belgesini temel alan bir şema oluşturmak için kullanılır. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem, bırden çok XML belgesini açıklayan bir şemayı çıkarmakta kullanılır. Örneğin, tüm XML belgesi kümesini açıklayan bir şema oluşturmak için <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> bırden çok XML belgesini tek seferde bir kez akışa aktarabilirsiniz.  
  
 İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem bir <xref:System.Xml.XmlReader> nesne içindeki bir XML belgesinden şemayı içerir ve çıkarılan şemayı içeren bir <xref:System.Xml.Schema.XmlSchemaSet> nesne döndürür. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> Yöntem, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReader> nesnesinde bulunan XML belgesiyle aynı hedef ad alanına sahip bir şema için bir nesne arar, varolan şemayı iyileştirir ve çıkarılan şemayı içeren bir <xref:System.Xml.Schema.XmlSchemaSet> nesne döndürür.  
  
 İyileştirilmiş şemada yapılan değişiklikler XML belgesinde bulunan yeni yapıyı temel alır. Örneğin, bir XML belgesi çapraz yapıldıkça, bulunan veri türleri hakkında varsayımlar yapılır ve şema bu varsayımlar temel alınarak oluşturulur. Ancak, özgün varsayıma göre farklılık gösteren ikinci bir çıkarım geçişinde veriye karşılaşılırsa, şema iyileştirilmektedir. Aşağıdaki örnek, iyileştirme sürecini gösterir.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 Örnek, ilk girişi olarak aşağıdaki dosyayı `item1.xml`alır.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Örnek, `item2.xml` dosyayı ikinci girdi olarak alır:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 İlk XML `productID` belgesinde özniteliğiyle karşılaşıldığında, değerinin `123456789` bir `xs:unsignedInt` tür olduğu varsayılır. Ancak, ikinci XML belgesi okunmadıysa ve değeri `A53-246` bulunursa, `xs:unsignedInt` tür artık kabul edilebilir değildir. Şema iyileştirilmektedir ve türü `productID` olarak `xs:string`değişir. `minOccurs` Ayrıca, `supplierID` öğesi için özniteliği olarak AYARLANıR `0`, çünkü ikinci XML belgesi hiç `supplierID` öğe içermiyor.  
  
 İlk XML belgesinden çıkarılan şema aşağıda verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 Aşağıda, birinci XML belgesinden çıkarılan ve ikinci XML belgesi tarafından iyileştirilmiş şema verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Satır içi şemalar  
 <xref:System.Xml.Schema.XmlSchemaInference> İşlem sırasında satır ıçı bir XML şeması tanım DILI (xsd) şemasına karşılaşılırsa, bir <xref:System.Xml.Schema.XmlSchemaInferenceException> oluşturulur. Örneğin, aşağıdaki satır içi şema bir <xref:System.Xml.Schema.XmlSchemaInferenceException>oluşturur.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Iyileştirilelemez şemalar  
 XML şeması tanım dili (XSD) şema <xref:System.Xml.Schema.XmlSchemaInference> işleminin, daraltmak için bir tür verildiyse ve bir özel durumun oluşturulmasına neden olması halinde işleyememesi gereken W3C xml şema yapıları vardır. Üst düzey kompozisyonu bir sıra dışında herhangi bir şey olan karmaşık bir tür gibi. Şema nesne modelinde (SOM), bu bir <xref:System.Xml.Schema.XmlSchemaComplexType> <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> özelliği bir örneği olmayan öğesine karşılık gelir. <xref:System.Xml.Schema.XmlSchemaSequence>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaInference>
- [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
- [Basit Türlerin Çıkarımını Yapma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)

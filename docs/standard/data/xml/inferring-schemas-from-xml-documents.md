---
title: XML Belgelerinden Şema Çıkarımı Yapma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b4727ead8abb9b3618f8b9dda8f7a9eb4b2321f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968148"
---
# <a name="inferring-schemas-from-xml-documents"></a>XML Belgelerinden Şema Çıkarımı Yapma
Bu konu nasıl kullanılacağını açıklar <xref:System.Xml.Schema.XmlSchemaInference> yapısı bir XML belgesi bir XML Şeması Tanım Dili (XSD) şema çıkarsanacak sınıfı.  
  
## <a name="the-schema-inference-process"></a>Şema çıkarımı işlemi  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfının <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı, bir veya daha fazla XML Şeması Tanım Dili (XSD) şemaları yapısının bir XML belgesi oluşturmak için kullanılır. Oluşturulan şemaları, orijinal XML belgeyi doğrulamak için kullanılabilir.  
  
 Bir XML belgesi tarafından işlenen <xref:System.Xml.Schema.XmlSchemaInference> sınıfı <xref:System.Xml.Schema.XmlSchemaInference> sınıfı tanımlayan öğeler ve öznitelikler XML belgesi şema bileşenleri hakkında varsayımlar hale getirir. <xref:System.Xml.Schema.XmlSchemaInference> Sınıfı da çıkarsar şema bileşenleri kısıtlanmış yolla en kısıtlayıcı bir türde bir belirli öğesi veya özniteliği için'çıkarımını yapma. XML belgesi hakkında daha fazla bilgi toplandıktan gibi bu kısıtlamalar, daha az kısıtlayıcı türlerin çıkarımını yapma tarafından gevşetiliyormuş. Çıkarımı yapılan en az kısıtlayıcı türü `xs:string`.  
  
 Örneğin, bir XML belgesi aşağıdaki parçası'ı alın.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 Yukarıdaki örnekte, zaman içinde `attribute1` öznitelik değeri ile karşılaşıldığında `6` tarafından <xref:System.Xml.Schema.XmlSchemaInference> işlemi varsayılır türünde olmasını `xs:unsignedByte`. Zaman ikinci `parent` öğesi tarafından karşılaştı <xref:System.Xml.Schema.XmlSchemaInference> sürecini kısıtlaması izin vermek için gevşekleştirildiğini türüne değiştirerek `xs:string` çünkü değerini `attribute1` özniteliktir artık `A`. Benzer şekilde, `minOccurs` özniteliği için tüm `child` şemada çıkarılan öğeleri izin vermek için gevşekleştirildiğini için `minOccurs="0"` ikinci üst öğenin alt öğeleri olduğundan.  
  
## <a name="inferring-schemas-from-xml-documents"></a>XML Belgelerinden Şema Çıkarımı Yapma  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfını kullanan iki aşırı <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> bir XML belgesi bir şemanın çıkarsandığı yöntemleri.  
  
 İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi, bir XML belgesine dayanan bir şema oluşturmak için kullanılır. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi, birden çok XML belgeleri tanımlayan bir şema çıkarsanacak kullanılır. Örneğin, birden çok XML belgeleri için besleyebilecek <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> XML belgeleri tüm kümesini tanımlayan bir şema oluşturmak için bir zaman yöntemi.  
  
 İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi içindeki bir XML belgesi bir şema çıkarsar bir <xref:System.Xml.XmlReader> nesne ve döndürür bir <xref:System.Xml.Schema.XmlSchemaSet> çıkarsanan şema içeren nesne. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi aramaları bir <xref:System.Xml.Schema.XmlSchemaSet> nesne için bir şema aynı hedef ad ile içerdiği XML belgesi olarak <xref:System.Xml.XmlReader> nesnesi mevcut şema iyileştirir ve döndürür bir <xref:System.Xml.Schema.XmlSchemaSet> çıkarsanan içeren nesne Şema.  
  
 Daraltılmış şemaya yapılan değişiklikleri XML belgesinde bulunan yeni yapıyı temel alır. Örneğin, bir XML belgesi geçirildiği, bulunan veri türleri hakkında varsayımlar yapılan ve şema oluşturulur, bu varsayımları temel alarak. Ancak, veri, farklı bir ikinci çıkarımı pass özgün varsayımına karşılaşılırsa, şema geliştirilir. Aşağıdaki örnek, iyileştirme işlemini gösterir.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 Örneğin aşağıdaki dosyayı alır `item1.xml`, ilk giriş olarak.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Ardından örnek alan `item2.xml` dosyası olarak kendi ikinci giriş:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Zaman `productID` öznitelik değeri ilk XML belgesinde karşılaşıldığında `123456789` varsayılır bir `xs:unsignedInt` türü. Ancak, ikinci bir XML belgesi olduğunda okuma ve değerini `A53-246` bulunursa `xs:unsignedInt` türü artık kabul edilir. Şema geliştirilir ve türünü `productID` değiştirilir `xs:string`. Ayrıca, `minOccurs` özniteliğini `supplierID` ayarlanır `0`, ikinci bir XML belgesi içerip içermediğini `supplierID` öğesi.  
  
 Şema çıkarımı yapılan ilk XML belgesinden verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 İkinci bir XML belgesi iyileştirilmektedir ilk XML belgesi içinden gösterilen şeması verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Satır içi şema  
 Bir satır içi XML Şeması Tanım Dili (XSD) şemaya sırasında karşılaşılırsa <xref:System.Xml.Schema.XmlSchemaInference> işlemi, bir <xref:System.Xml.Schema.XmlSchemaInferenceException> oluşturulur. Örneğin, aşağıdaki satır içi şema oluşturur bir <xref:System.Xml.Schema.XmlSchemaInferenceException>.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Olamaz şemaları Refined  
 Vardır W3C XML şema oluşturur XML Şeması Tanım Dili (XSD) şemaya <xref:System.Xml.Schema.XmlSchemaInference> işlem, belirli bir türe iyileştirmek ve bir özel durum oluşturulmasına neden olursa işleyemez. Gibi karmaşık bir tür olan üst düzey oluşturucuya bir dizi dışında herhangi bir şey var. Şema nesne modeli (SOM)'da, bu karşılık gelen bir <xref:System.Xml.Schema.XmlSchemaComplexType> olan <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> özelliği bir örneği değil <xref:System.Xml.Schema.XmlSchemaSequence>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaInference>
- [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
- [Basit Türlerin Çıkarımını Yapma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)

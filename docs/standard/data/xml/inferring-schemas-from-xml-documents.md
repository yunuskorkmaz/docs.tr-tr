---
title: "XML belgelerden şemaları çıkarımını yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8085ecb86018460f14a2532b55907472988b67b2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="inferring-schemas-from-xml-documents"></a>XML belgelerden şemaları çıkarımını yapma
Bu konuda nasıl kullanılacağını açıklar <xref:System.Xml.Schema.XmlSchemaInference> bir XML belgesi yapısını bir XML Şeması Tanım Dili (XSD) şemadan gerçekleştirip sınıfı.  
  
## <a name="the-schema-inference-process"></a>Şema çıkarım işlemi  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfının <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı, bir veya daha fazla XML Şeması Tanım Dili (XSD) şemaları bir XML belgesi yapısından oluşturmak için kullanılır. Oluşturulan şemaları, özgün XML belgesi doğrulamak için kullanılabilir.  
  
 Bir XML olarak belge tarafından işlenen <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, <xref:System.Xml.Schema.XmlSchemaInference> sınıfı öğeleri ve öznitelikleri XML belgesindeki açıklayan şema bileşenleri hakkında varsayımlar yapar. <xref:System.Xml.Schema.XmlSchemaInference> Sınıfı ayrıca oluşturur şema bileşenleri kısıtlanmış bir şekilde belirli öğesi veya özniteliği için en kısıtlayıcı türü çıkarımını yapma. XML belgesi hakkında daha fazla bilgi toplanan gibi bu kısıtlamaların daha az kısıtlayıcı türlerinin çıkarımını yapma gevşetiliyormuş. Çıkarsanabileceği en az kısıtlayıcı türü `xs:string`.  
  
 , Örneğin, bir XML belgesi aşağıdaki parçası olur.  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 Yukarıdaki, ne zaman örnekte `attribute1` öznitelik değeri olan karşılaştı `6` tarafından <xref:System.Xml.Schema.XmlSchemaInference> işlemi varsayılır türünde olmasını `xs:unsignedByte`. Zaman ikinci `parent` tarafından öğesiyle karşılaştı <xref:System.Xml.Schema.XmlSchemaInference> işlem, kısıtlaması izin vermek için gevşekleştirildiğini türüne değiştirerek `xs:string` çünkü değerini `attribute1` özniteliktir şimdi `A`. Benzer şekilde, `minOccurs` özniteliği için tüm `child` şemada çıkarımı yapılan öğeleri izin vermek için gevşekleştirildiğini için `minOccurs="0"` ikinci ana öğesi alt öğe olduğundan.  
  
## <a name="inferring-schemas-from-xml-documents"></a>XML belgelerden şemaları çıkarımını yapma  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfını kullanan iki aşırı <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> bir XML belgesi şemadan anlamak için yöntemleri.  
  
 İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi, bir XML belgesi dayalı bir şema oluşturmak için kullanılır. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi, birden çok XML belgelerini tanımlayan bir şema anlamak için kullanılır. Örneğin, birden çok XML belgelerini besleyebilecek <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> XML belgeleri kümesinin tamamını tanımlayan bir şema oluşturmak için bir zaman yöntemi.  
  
 İlk <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi oluşturur içinde yer alan bir XML belgesi şemadan bir <xref:System.Xml.XmlReader> nesne ve döndürür bir <xref:System.Xml.Schema.XmlSchemaSet> oluşturulursa şema içeren bir nesne. İkinci <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> yöntemi aramaları bir <xref:System.Xml.Schema.XmlSchemaSet> nesnesi aynı hedef ad alanına sahip bir şema için XML belgesi yer alan olarak <xref:System.Xml.XmlReader> nesnesi, varolan şema iyileştirir ve döndürür bir <xref:System.Xml.Schema.XmlSchemaSet> oluşturulursa içeren nesnesi Şema.  
  
 Gelişmiş şema değişikliklerinin XML belgesinde bulunan yeni yapısı dayanır. Örneğin, bir XML belgesi geçirildiği varsayımlar bulunan veri türleri hakkında yapılan ve şema oluşturulan bu varsayımları temel alarak. Ancak, verileri, farklı bir ikinci çıkarım pass özgün varsayımına karşılaşılırsa, şema geliştirilir. Aşağıdaki örnek iyileştirme işlemi gösterilmektedir.  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 Aşağıdaki dosya örneğini alır `item1.xml`, ilk giriş olarak.  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 Örnek sonra geçen `item2.xml` dosya ikinci giriş olarak:  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 Zaman `productID` öznitelik değeri ilk XML belgesinde karşılaştı `123456789` varsayılır bir `xs:unsignedInt` türü. Ancak, ikinci bir XML belgesi olduğunda okuma ve değerini `A53-246` bulunan `xs:unsignedInt` türü artık olduğu varsayılır. Şema geliştirilir ve türünü `productID` değiştirilir `xs:string`. Ayrıca, `minOccurs` için öznitelik `supplierID` ayarlanır `0`, ikinci bir XML belgesi Hayır içerdiğinden `supplierID` öğesi.  
  
 İlk XML belgesinden çıkarımı yapılan şema verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 İkinci bir XML belgesi iyileştirilmiştir ilk XML belgesindeki çıkarımı yapılan şema verilmiştir.  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a>Satır içi şemalar  
 Satır içi bir XML Şeması Tanım Dili (XSD) şema sırasında karşılaşılan varsa <xref:System.Xml.Schema.XmlSchemaInference> işlemi, bir <xref:System.Xml.Schema.XmlSchemaInferenceException> oluşturulur. Örneğin, aşağıdaki satır içi şema atar bir <xref:System.Xml.Schema.XmlSchemaInferenceException>.  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a>Olamaz şemaları Refined  
 Vardır W3C XML şema yapıları XML Şeması Tanım Dili (XSD) şeması <xref:System.Xml.Schema.XmlSchemaInference> işlem iyileştirmek ve bir özel durum oluşturulmasına neden için bir türü verildiyse işleyemez. Bir karmaşık gibi üst düzey oluşturucuya bir sıra dışında her şey türüdür. Şema nesne modeli (SOM)'da, bu karşılık gelen bir <xref:System.Xml.Schema.XmlSchemaComplexType> , <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> özelliği bir örneği değil <xref:System.Xml.Schema.XmlSchemaSequence>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)  
 [Basit Türlerin Çıkarımını Yapma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)

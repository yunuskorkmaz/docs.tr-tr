---
title: Sınıflardan Şemaları Dışa Aktarma
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, schema import and export
- schemas [WCF], exporting from classes
- schemas [WCF]
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: bb57b962-70c1-45a9-93d5-e721e340a13f
ms.openlocfilehash: dcbccbea279796fdaec1227b7575cf39e47f9e4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856689"
---
# <a name="exporting-schemas-from-classes"></a>Sınıflardan Şemaları Dışa Aktarma
Veri sözleşmesi modeli kullandığınız sınıflardan XML Şeması Tanım Dili (XSD) şemaları oluşturmak için <xref:System.Runtime.Serialization.XsdDataContractExporter> sınıfı. Bu konuda şemaları oluşturma işlemi açıklanmaktadır.  
  
## <a name="the-export-process"></a>Dışa aktarma işlemi  
 Şema dışarı aktarma işlemi bir veya daha fazla türleri ile başlar ve üreten bir <xref:System.Xml.Schema.XmlSchemaSet> , bu tür XML projeksiyon açıklar.  
  
 `XmlSchemaSet` Parçasıdır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ın XSD şema belge kümesini temsil eden şema nesne modeli (SOM). XSD belgeleri oluşturmak için bir `XmlSchemaSet`, şemalardan koleksiyonunu kullanın <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği `XmlSchemaSet` sınıfı. Her seri <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Serialization.XmlSerializer>.  
  
#### <a name="to-export-schemas"></a>Şemaları dışarı aktarmak için  
  
1. Bir örneğini oluşturmak <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2. İsteğe bağlı. Başarılı bir <xref:System.Xml.Schema.XmlSchemaSet> oluşturucuda. Bu durumda, şema dışarı aktarma sırasında oluşturulan şema için eklenir <xref:System.Xml.Schema.XmlSchemaSet> örneği yerine boş bir ile başlayan <xref:System.Xml.Schema.XmlSchemaSet>.  
  
3. İsteğe bağlı. Birini çağırın <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> yöntemleri. Yöntemi, belirtilen türe dışarı olup olmadığını belirler. Has yöntemi olarak aynı aşırı `Export` sonraki adımda yöntemi.  
  
4. Birini çağırın <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> yöntemleri. Üç aşırı yükleme sürüyor bir <xref:System.Type>, <xref:System.Collections.Generic.List%601> , `Type` nesneler veya bir <xref:System.Collections.Generic.List%601> , <xref:System.Reflection.Assembly> nesneleri. En son durumda verilen derlemelerdeki tüm türleri verilir.  
  
     Birden çok çağrılar `Export` birden çok öğe aynı eklenen yöntemi sonuçlanıyor `XmlSchemaSet`. Bir tür içinde oluşturulmaz `XmlSchemaSet` zaten var olup olmadığını. Bu nedenle, çağırma `Export` üzerinde birden çok kez aynı `XsdDataContractExporter` birden çok örneğini oluşturmak için tercih edilir `XsdDataContractExporter` sınıfı. Bu yinelenen bir şema türü oluşturulmasını önler.  
  
    > [!NOTE]
    >  Dışarı aktarma sırasında bir hata varsa `XmlSchemaSet` öngörülemeyen durumda olacaktır.  
  
5. Erişim <xref:System.Xml.Schema.XmlSchemaSet> aracılığıyla <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> özelliği.  
  
## <a name="export-options"></a>Dışarı aktarma seçenekleri  
 Ayarlayabileceğiniz <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> özelliği <xref:System.Runtime.Serialization.XsdDataContractExporter> örneğine <xref:System.Runtime.Serialization.ExportOptions> dışarı aktarma işlemini çeşitli yönlerini denetlemek için sınıf. Özellikle, aşağıdaki seçenekleri ayarlayabilirsiniz:  
  
- <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Bu koleksiyonu `Type` dışarı aktarılan türler için bilinen türleri temsil eder. (Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) Bu bilinen türleri dışarı aktarılır her `Export` geçirilen türlerine ek olarak çağrı `Export` yöntemi.  
  
- <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. Bir <xref:System.Runtime.Serialization.IDataContractSurrogate> dışarı aktarma işlemini özelleştireceğim bu özelliği aracılığıyla sağlanabilir. Daha fazla bilgi için [veri anlaşması yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Varsayılan olarak, hiçbir vekil kullanılır.  
  
## <a name="helper-methods"></a>Yardımcı yöntemler  
 Şema, verme birincil rolü yanı sıra `XsdDataContractExporter` türleri hakkında bilgi sağlayan çeşitli yararlı yardımcı yöntemler sağlar. Bu güncelleştirmeler şunlardır:  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> yöntem. Bu yöntem bir `Type` ve döndüren bir <xref:System.Xml.XmlQualifiedName> kök öğe adı ve bu tür, kök nesnesi olarak seri duruma, kullanılacak ad alanını temsil eden.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> yöntem. Bu yöntem bir `Type` ve döndüren bir <xref:System.Xml.XmlQualifiedName> bu tür şemaya dışarı aktarıldı, kullanılacak XSD şema türü adını temsil eder. İçin <xref:System.Xml.Serialization.IXmlSerializable> türleri, şema anonim türler olarak temsil edilen bu yöntemi döndürür `null`.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> yöntem. Bu yöntem yalnızca çalışır <xref:System.Xml.Serialization.IXmlSerializable> döndürür ve şema anonim türler olarak temsil edilmektedir türleri `null` diğer tüm türleri için. Anonim türler için bu yöntemi döndürür bir <xref:System.Xml.Schema.XmlSchemaType> temsil eden bir verilen `Type`.  
  
 Bu yöntemlerin tümü, dışarı aktarma seçeneklerini etkiler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Şema İçeri ve Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Sınıf Oluşturmak için Şemayı İçeri Aktarma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)

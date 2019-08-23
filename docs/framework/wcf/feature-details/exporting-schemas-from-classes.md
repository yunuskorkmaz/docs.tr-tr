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
ms.openlocfilehash: 3db3cc1c529ab40bf775c06a5128e4dabf3c8a56
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963650"
---
# <a name="exporting-schemas-from-classes"></a>Sınıflardan Şemaları Dışa Aktarma
Veri anlaşması modelinde kullanılan sınıflardan XML şeması tanım dili (xsd) şemaları oluşturmak için <xref:System.Runtime.Serialization.XsdDataContractExporter> sınıfını kullanın. Bu konu başlığı, şema oluşturma işlemini açıklar.  
  
## <a name="the-export-process"></a>Dışarı aktarma Işlemi  
 Şema dışarı aktarma işlemi bir veya daha fazla tür ile başlar ve bu <xref:System.Xml.Schema.XmlSchemaSet> türlerin XML projeksiyonunu açıklayan bir oluşturur.  
  
 , `XmlSchemaSet` Bir xsd şeması belgelerinin kümesini temsil eden .NET Framework şema nesne modelinin (som) bir parçasıdır. Bir `XmlSchemaSet`öğesinden xsd belgeleri oluşturmak için, `XmlSchemaSet` sınıfının <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğinden şema koleksiyonunu kullanın. Ardından öğesini <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Serialization.XmlSerializer>kullanarak her nesneyi serileştirin.  
  
#### <a name="to-export-schemas"></a>Şemaları dışarı aktarmak için  
  
1. Öğesinin bir örneğini oluşturun <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2. İsteğe bağlı. Oluşturucuda bir <xref:System.Xml.Schema.XmlSchemaSet> geçirin. Bu durumda, şema dışa aktarma sırasında oluşturulan şema boş <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet>bir başlangıç yerine bu örneğe eklenir.  
  
3. İsteğe bağlı. <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> Yöntemlerden birini çağırın. Yöntemi, belirtilen türün verilemeyeceğini belirler. Yöntemi, sonraki adımda `Export` yöntemiyle aynı aşırı yüklemelerin aynısına sahiptir.  
  
4. <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> Yöntemlerden birini çağırın. Bir <xref:System.Type> <xref:System.Collections.Generic.List%601> nesneveya<xref:System.Reflection.Assembly> nesne alan üç aşırı yükleme vardır. <xref:System.Collections.Generic.List%601> `Type` Son durumda, tüm verilen derlemelerdeki tüm türler verilir.  
  
     Birden çok öğe çağrısı `Export` , aynı `XmlSchemaSet`öğeye birden çok öğe eklenmesine neden olur. Bir tür, `XmlSchemaSet` zaten varsa öğesine oluşturulmaz. Bu nedenle, `Export` aynı `XsdDataContractExporter` yerde birden çok kez çağırmak, `XsdDataContractExporter` sınıfının birden çok örneğini oluşturmak için tercih edilir. Bu, yinelenen şema türlerinin oluşturulmasını önler.  
  
    > [!NOTE]
    > Dışarı aktarma `XmlSchemaSet` sırasında bir hata oluşursa, beklenmeyen bir durumda olur.  
  
5. Özelliği<xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A>aracılığıylaöğesineerişin. <xref:System.Xml.Schema.XmlSchemaSet>  
  
## <a name="export-options"></a>Dışarı aktarma seçenekleri  
 Öğesinin <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> özelliğini, <xref:System.Runtime.Serialization.XsdDataContractExporter> dışa aktarma işleminin çeşitli yönlerini denetlemek için <xref:System.Runtime.Serialization.ExportOptions> sınıfının bir örneğine ayarlayabilirsiniz. Özellikle, aşağıdaki seçenekleri belirleyebilirsiniz:  
  
- <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Bu koleksiyon `Type` , aktarılan türlerin bilinen türlerini temsil eder. (Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) Bu bilinen türler, `Export` `Export` yöntemine geçirilen türlere ek olarak her çağrıya aktarılır.  
  
- <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. Dışarı <xref:System.Runtime.Serialization.IDataContractSurrogate> aktarma işlemini özelleştirecek bu özellik aracılığıyla bir sağlanabilir. Daha fazla bilgi için bkz. [veri sözleşmesi yedeklerin kapıları](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Varsayılan olarak, hiçbir yedek kullanılmaz.  
  
## <a name="helper-methods"></a>Yardımcı yöntemler  
 Şema dışa aktarma işleminin birincil rolüne ek olarak, `XsdDataContractExporter` türleri hakkında bilgi sağlayan çeşitli yararlı yardımcı yöntemler sağlar. Bu güncelleştirmeler şunlardır:  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A>yöntemidir. Bu yöntem bir `Type` kullanır ve bu tür <xref:System.Xml.XmlQualifiedName> kök nesne olarak seri hale getirilse kullanılacak kök öğe adı ve ad alanını temsil eden bir döndürür.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A>yöntemidir. Bu yöntem bir `Type` kullanır ve bu tür <xref:System.Xml.XmlQualifiedName> şemaya aktarılıyorsa kullanılacak xsd şema türünün adını temsil eden bir döndürür. Şemada <xref:System.Xml.Serialization.IXmlSerializable> anonim türler olarak temsil edilen türler için, bu yöntem döndürür. `null`  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A>yöntemidir. Bu yöntem yalnızca <xref:System.Xml.Serialization.IXmlSerializable> şemada anonim türler olarak temsil edilen türlerle, `null` diğer tüm türler için de geçerlidir. Anonim türler için, bu yöntem verilen <xref:System.Xml.Schema.XmlSchemaType> `Type`öğesini temsil eden bir döndürür.  
  
 Dışarı aktarma seçenekleri bu yöntemlerin tümünü etkiler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Şema İçeri ve Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Sınıf Oluşturmak için Şemayı İçeri Aktarma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)

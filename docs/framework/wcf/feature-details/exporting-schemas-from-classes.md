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
ms.openlocfilehash: d356450af8ce6690e2142f3487e153bcde095324
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595524"
---
# <a name="exporting-schemas-from-classes"></a>Sınıflardan Şemaları Dışa Aktarma
Veri anlaşması modelinde kullanılan sınıflardan XML şeması tanım dili (XSD) şemaları oluşturmak için <xref:System.Runtime.Serialization.XsdDataContractExporter> sınıfını kullanın. Bu konu başlığı, şema oluşturma işlemini açıklar.  
  
## <a name="the-export-process"></a>Dışarı aktarma Işlemi  
 Şema dışarı aktarma işlemi bir veya daha fazla tür ile başlar ve <xref:System.Xml.Schema.XmlSchemaSet> Bu TÜRLERIN XML projeksiyonunu açıklayan bir oluşturur.  
  
 , `XmlSchemaSet` BIR xsd şeması belgelerinin kümesini temsil eden .NET Framework şema nesne modelinin (som) bir parçasıdır. Bir öğesinden XSD belgeleri oluşturmak için `XmlSchemaSet` , sınıfının özelliğinden şema koleksiyonunu kullanın <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> `XmlSchemaSet` . Ardından öğesini kullanarak her nesneyi serileştirin <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Serialization.XmlSerializer> .  
  
#### <a name="to-export-schemas"></a>Şemaları dışarı aktarmak için  
  
1. <xref:System.Runtime.Serialization.XsdDataContractExporter> nesnesinin bir örneğini oluşturun.  
  
2. İsteğe bağlı. Oluşturucuda bir geçirin <xref:System.Xml.Schema.XmlSchemaSet> . Bu durumda, şema dışa aktarma sırasında oluşturulan şema <xref:System.Xml.Schema.XmlSchemaSet> boş bir başlangıç yerine bu örneğe eklenir <xref:System.Xml.Schema.XmlSchemaSet> .  
  
3. İsteğe bağlı. Yöntemlerden birini çağırın <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> . Yöntemi, belirtilen türün verilemeyeceğini belirler. Yöntemi, sonraki adımda yöntemiyle aynı aşırı yüklemelerin aynısına sahiptir `Export` .  
  
4. Yöntemlerden birini çağırın <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> . Bir <xref:System.Type> <xref:System.Collections.Generic.List%601> `Type` nesne veya <xref:System.Collections.Generic.List%601> nesne alan üç aşırı yükleme vardır <xref:System.Reflection.Assembly> . Son durumda, tüm verilen derlemelerdeki tüm türler verilir.  
  
     Birden çok öğe çağrısı `Export` , aynı öğeye birden çok öğe eklenmesine neden olur `XmlSchemaSet` . Bir tür, zaten varsa öğesine oluşturulmaz `XmlSchemaSet` . Bu nedenle, `Export` aynı yerde birden çok kez çağırmak, `XsdDataContractExporter` sınıfının birden çok örneğini oluşturmak için tercih edilir `XsdDataContractExporter` . Bu, yinelenen şema türlerinin oluşturulmasını önler.  
  
    > [!NOTE]
    > Dışarı aktarma sırasında bir hata oluşursa, `XmlSchemaSet` beklenmeyen bir durumda olur.  
  
5. <xref:System.Xml.Schema.XmlSchemaSet>Özelliği aracılığıyla öğesine erişin <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> .  
  
## <a name="export-options"></a>Dışarı aktarma seçenekleri  
 <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A>Öğesinin özelliğini, <xref:System.Runtime.Serialization.XsdDataContractExporter> <xref:System.Runtime.Serialization.ExportOptions> dışa aktarma işleminin çeşitli yönlerini denetlemek için sınıfının bir örneğine ayarlayabilirsiniz. Özellikle, aşağıdaki seçenekleri belirleyebilirsiniz:  
  
- <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Bu koleksiyon, `Type` aktarılan türlerin bilinen türlerini temsil eder. (Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](data-contract-known-types.md).) Bu bilinen türler `Export` , yöntemine geçirilen türlere ek olarak her çağrıya aktarılır `Export` .  
  
- <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. <xref:System.Runtime.Serialization.IDataContractSurrogate>Dışarı aktarma işlemini özelleştirecek bu özellik aracılığıyla bir sağlanabilir. Daha fazla bilgi için bkz. [veri sözleşmesi yedeklerin kapıları](../extending/data-contract-surrogates.md). Varsayılan olarak, hiçbir yedek kullanılmaz.  
  
## <a name="helper-methods"></a>Yardımcı yöntemler  
 Şema dışa aktarma işleminin birincil rolüne ek olarak, `XsdDataContractExporter` türleri hakkında bilgi sağlayan çeşitli yararlı yardımcı yöntemler sağlar. Bu güncelleştirmeler şunlardır:  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A>yöntemidir. Bu yöntem bir kullanır `Type` ve <xref:System.Xml.XmlQualifiedName> Bu tür kök nesne olarak seri hale getirilse kullanılacak kök öğe adı ve ad alanını temsil eden bir döndürür.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A>yöntemidir. Bu yöntem bir kullanır `Type` ve <xref:System.Xml.XmlQualifiedName> Bu tür şemaya AKTARıLıYORSA kullanılacak xsd şema türünün adını temsil eden bir döndürür. <xref:System.Xml.Serialization.IXmlSerializable>Şemada anonim türler olarak temsil edilen türler için, bu yöntem döndürür `null` .  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A>yöntemidir. Bu yöntem yalnızca <xref:System.Xml.Serialization.IXmlSerializable> şemada anonim türler olarak temsil edilen türlerle, `null` diğer tüm türler için de geçerlidir. Anonim türler için, bu yöntem verilen öğesini <xref:System.Xml.Schema.XmlSchemaType> temsil eden bir döndürür `Type` .  
  
 Dışarı aktarma seçenekleri bu yöntemlerin tümünü etkiler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Şema İçeri ve Dışarı Aktarma](schema-import-and-export.md)
- [Sınıf Oluşturmak için Şemayı İçe Aktarma](importing-schema-to-generate-classes.md)

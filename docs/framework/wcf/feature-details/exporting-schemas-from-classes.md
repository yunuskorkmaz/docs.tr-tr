---
title: Sınıflardan Şemaları Dışarı Aktarma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF, schema import and export
- schemas [WCF], exporting from classes
- schemas [WCF]
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: bb57b962-70c1-45a9-93d5-e721e340a13f
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9e63223fce7f86b0cf2a64ba4e7aa2e54ca6219
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="exporting-schemas-from-classes"></a>Sınıflardan Şemaları Dışarı Aktarma
Veri sözleşmesi modelinde kullanılan sınıflardan XML Şeması Tanım Dili (XSD) şemaları oluşturmak için kullanmak <xref:System.Runtime.Serialization.XsdDataContractExporter> sınıfı. Bu konuda şemaları oluşturma işlemi açıklanmaktadır.  
  
## <a name="the-export-process"></a>Dışa aktarma işlemi  
 Şema dışa aktarma işlemi bir veya daha fazla türleri ile başlar ve üreten bir <xref:System.Xml.Schema.XmlSchemaSet> , bu tür XML projeksiyon açıklar.  
  
 `XmlSchemaSet` Parçası olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]'s şema nesne modeli (XSD şema belgeleri kümesini temsil eden SOM). XSD belgelerden oluşturmak için bir `XmlSchemaSet`, şemalar topluluğu kullanmak <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği `XmlSchemaSet` sınıfı. Her seri <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Serialization.XmlSerializer>.  
  
#### <a name="to-export-schemas"></a>Şemaları dışarı aktarmak için  
  
1.  Bir örneğini oluşturmak <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2.  İsteğe bağlı. Geçirmek bir <xref:System.Xml.Schema.XmlSchemaSet> oluşturucuda. Bu durumda, şema dışa aktarma sırasında oluşturulan şema için eklenir <xref:System.Xml.Schema.XmlSchemaSet> örneği yerine boş bir ile başlayan <xref:System.Xml.Schema.XmlSchemaSet>.  
  
3.  İsteğe bağlı. Birini çağırın <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> yöntemleri. Yöntemi, belirtilen tür dışarı olup olmadığını belirler. Yöntemi olarak aynı aşırı yüklemeye sahip `Export` sonraki adımda yöntemi.  
  
4.  Birini çağırın <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> yöntemleri. Alma üç aşırı bir <xref:System.Type>, <xref:System.Collections.Generic.List%601> , `Type` nesneleri veya <xref:System.Collections.Generic.List%601> , <xref:System.Reflection.Assembly> nesneleri. Son durumda, tüm belirtilen derlemelere içindeki tüm türler dışarı aktarılır.  
  
     Birden çok çağrılar `Export` aynı eklenmekte olan birden çok öğe sonuçlanıyor yöntemi `XmlSchemaSet`. Bir tür halinde oluşturulmaz `XmlSchemaSet` , zaten varsa. Bu nedenle, çağırma `Export` birden çok kez üzerinde aynı `XsdDataContractExporter` birden çok örneğini oluşturmak için tercih edilir `XsdDataContractExporter` sınıfı. Bu yinelenen şema türü oluşturulmasını önler.  
  
    > [!NOTE]
    >  Dışa aktarma sırasında bir hata olduğunda `XmlSchemaSet` öngörülemeyen durumda olacaktır.  
  
5.  Erişim <xref:System.Xml.Schema.XmlSchemaSet> aracılığıyla <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> özelliği.  
  
## <a name="export-options"></a>Dışa aktarma seçenekleri  
 Ayarlayabileceğiniz <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> özelliği <xref:System.Runtime.Serialization.XsdDataContractExporter> örneğine <xref:System.Runtime.Serialization.ExportOptions> verme işlemi çeşitli yönlerini denetlemek için sınıf. Özellikle, aşağıdaki seçenekleri ayarlayabilirsiniz:  
  
-   <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Bu koleksiyonu `Type` dışarı aktarılan türleri için bilinen türleri temsil eder. (Daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) Bu bilinen türleri üzerinde dışarı her `Export` geçirilen türlerine ek olarak çağrı `Export` yöntemi.  
  
-   <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. Bir <xref:System.Runtime.Serialization.IDataContractSurrogate> verme işlemi özelleştirmek bu özelliği aracılığıyla sağlanabilir. Daha fazla bilgi için bkz: [veri sözleşmesi yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Varsayılan olarak, hiçbir yedek kullanılır.  
  
## <a name="helper-methods"></a>Yardımcı yöntemler  
 Şema, verme birincil rolü yanı sıra `XsdDataContractExporter` türleri hakkında bilgi sağlayan çeşitli yararlı yardımcı yöntemler sağlar. Bu güncelleştirmeler şunlardır:  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> yöntem. Bu yöntem alır bir `Type` ve döndüren bir <xref:System.Xml.XmlQualifiedName> kök öğe adı ve bu tür kök nesnesi olarak seri hale getirilmiş, kullanılacak ad alanını temsil eden.  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> yöntem. Bu yöntem alır bir `Type` ve döndüren bir <xref:System.Xml.XmlQualifiedName> bu tür şemaya aktarılmış, kullanılacak XSD şema türü adını temsil eder. İçin <xref:System.Xml.Serialization.IXmlSerializable> şemasında anonim türler olarak gösterilen türleri, bu yöntem `null`.  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> yöntem. Bu yöntem yalnızca çalışır <xref:System.Xml.Serialization.IXmlSerializable> şema ve döndürür anonim türleri olarak temsil edilir türleri `null` diğer tüm türler için. Anonim türler için bu yöntem bir <xref:System.Xml.Schema.XmlSchemaType> temsil eden bir verilen `Type`.  
  
 Dışarı aktarma seçeneklerini tüm bu yöntemlerin etkiler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [Şema İçeri ve Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)  
 [Sınıf Oluşturmak için Şemayı İçeri Aktarma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)

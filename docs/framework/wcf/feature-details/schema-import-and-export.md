---
title: Şema İçeri ve Dışarı Aktarma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: a14ee9e5916133be3979650055cf3e57899a4cca
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591803"
---
# <a name="schema-import-and-export"></a>Şema İçeri ve Dışarı Aktarma
Windows Communication Foundation (WCF) içeren yeni bir serileştirme motoruna <xref:System.Runtime.Serialization.DataContractSerializer>. `DataContractSerializer` .NET Framework nesneleri ve XML arasında (her iki yönde) çevirir. Serileştirici kendisini ek olarak, WCF, ilişkili şema içeri ve dışarı aktarma mekanizması şema içerir. *Şema* seri hale getirici üretir veya seri durumdan çıkarıcı erişip XML şeklini resmi, kesin ve makine tarafından okunabilir bir açıklaması. WCF World Wide Web Consortium (W3C) XML Şeması Tanım Dili (XSD) çok sayıda üçüncü taraf platformlarıyla çalışabilen yaygın olarak, şema gösterimi olarak kullanır.  
  
 Şema içeri aktarma bileşen <xref:System.Runtime.Serialization.XsdDataContractImporter>oluşturur ve bir XSD şema belgesi alır .NET Framework sınıfları (normalde veri sözleşme sınıflar) sağlayacak şekilde serileştirilmiş forms belirtilen şemaya karşılık gelir.  
  
 Örneğin, aşağıdaki şema parçası:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 (daha iyi okunabilirlik açısından biraz Basitleştirilmiş) aşağıdaki türü oluşturur.  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Oluşturulan tür birkaç veri sözleşme en iyi izlediğini unutmayın (bulunan [en iyi uygulamalar: Veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
- Türün uyguladığı <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Daha fazla bilgi için [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
- Veri üyeleri, özel alanlar sarmalayan genel özellikleri olarak uygulanır.  
  
- Kısmi bir sınıf sınıftır ve eklemeler oluşturulan kodu değiştirmeden yapılabilir.  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> Ters yapmanıza olanak tanır; ile seri hale getirilebilir bir tür `DataContractSerializer` ve bir XSD şema belgesi oluşturabilirsiniz.  
  
## <a name="fidelity-is-not-guaranteed"></a>Güvenilirlik garanti edilmez  
 Bu şema veya türleri toplam doğruluk ile gidiş dönüş yapmak kesin değildir. (A *gidiş dönüş* bir şema sınıfları kümesi oluşturun ve sonucu bir şema oluşturmayı yeniden dışarı aktarmayı anlamına gelir.) Aynı şemaya döndürülemez. İşlemi ters da uygunluğunu korumak için garanti edilmez. (Şemasına üretmek için bir türünü dışarı aktarın ve sonra türü geri alın. Bu aynı türü döndürülür düşüktür.)  
  
## <a name="supported-types"></a>Desteklenen türler  
 Veri sözleşmesi modeli yalnızca sınırlı bir alt kümesini WC3 şemayı destekler. Bu alt kümesine uymayan herhangi bir şema içeri aktarma işlemi sırasında bir özel durum neden olur. Örneğin, bir veri anlaşması veri üyesi bir XML özniteliği olarak seri olduğunu belirtmek için hiçbir yolu yoktur. Bu nedenle, XML öznitelikleri kullanımını zorunlu şemaları desteklenmez ve bir veri anlaşması doğru XML projeksiyon ile oluşturmak olanaksız olduğundan içeri aktarma sırasında özel durumlar neden olur.  
  
 Örneğin, aşağıdaki şema parçası kullanarak varsayılan ayarları içeri aktarılamaz.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Daha fazla bilgi için [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bir şema veri sözleşme kuralları için uygun değil, farklı serileştirme motoruna kullanın. Örneğin, <xref:System.Xml.Serialization.XmlSerializer> kendi ayrı şema içeri aktarma mekanizması kullanır. Ayrıca, bir özel içeri aktarma modu, desteklenen şema aralığını genişletilir yoktur. Bölüm oluşturma hakkında daha fazla bilgi için bkz. <xref:System.Xml.Serialization.IXmlSerializable> türlerini [sınıfları oluşturmak için şema alma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 `XsdDataContractExporter` İle seri hale getirilebilir herhangi bir .NET Framework türlerini destekler `DataContractSerializer`. Daha fazla bilgi için [veri sözleşme seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Bu şema kullanılarak oluşturulan unutmayın `XsdDataContractExporter` normalde geçerli veriler, `XsdDataContractImporter` kullanabilirsiniz (sürece <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> şema özelleştirmek için kullanılır).  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Runtime.Serialization.XsdDataContractImporter>, bkz: [sınıfları oluşturmak için şema alma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Runtime.Serialization.XsdDataContractExporter>, bkz: [sınıflardan Şemaları dışarı aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Sınıf Oluşturmak için Şemayı İçeri Aktarma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
- [Sınıflardan Şemaları Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)

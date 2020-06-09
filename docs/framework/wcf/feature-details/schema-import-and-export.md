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
ms.openlocfilehash: 942ade69d92d8a213f65a3a2e463b6924e2f986e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590221"
---
# <a name="schema-import-and-export"></a>Şema İçeri ve Dışarı Aktarma
Windows Communication Foundation (WCF) yeni bir serileştirme altyapısı içerir, <xref:System.Runtime.Serialization.DataContractSerializer> . `DataContractSerializer`.NET Framework nesneleri Ile XML arasında çevirir (her iki yönde). Seri hale getirici 'nin buna ek olarak WCF, ilişkili şema içeri aktarma ve şema dışa aktarma mekanizmalarını içerir. *Şema* , seri hale getiricinin oluşturduğu veya seri hale GETIRICININ erişebileceği XML şeklinin resmi, kesin ve makine tarafından okunabilen bir açıklamasıdır. WCF, World Wide Web Konsorsiyumu (W3C) XML şeması tanım dili (XSD) kullanır ve bu, çok sayıda üçüncü taraf platformda yaygın olarak birlikte çalışabilir.  
  
 Şema içeri aktarma bileşeni, <xref:System.Runtime.Serialization.XsdDataContractImporter> BIR xsd şema belgesi alır ve seri hale getirilmiş formlar verilen şemaya karşılık gelen .NET Framework sınıfları (normalde veri sözleşme sınıfları) oluşturur.  
  
 Örneğin, aşağıdaki şema parçası:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 Aşağıdaki türü üretir (daha iyi okunabilirlik için biraz Basitleştirilmiş).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Oluşturulan türün çeşitli veri sözleşmesi en iyi uygulamaları ( [En Iyi uygulamalar: veri sözleşmesi sürümü oluşturma](../best-practices-data-contract-versioning.md)) takip edin:  
  
- Türü, arabirimini uygular <xref:System.Runtime.Serialization.IExtensibleDataObject> . Daha fazla bilgi için bkz. [Ileri uyumlu veri sözleşmeleri](forward-compatible-data-contracts.md).  
  
- Veri üyeleri özel alanları kaydırmak için ortak özellikler olarak uygulanır.  
  
- Sınıfı kısmi bir sınıftır ve oluşturulan kod değiştirilerek eklemeler yapılabilir.  
  
 , <xref:System.Runtime.Serialization.XsdDataContractExporter> , İle seri hale getirilebilir `DataContractSerializer` ve bir xsd şeması belgesi üreten türler alma işlemini yapmanızı sağlar.  
  
## <a name="fidelity-is-not-guaranteed"></a>Uygunluk garantisi garanti edilmez  
 Şemanın veya türlerin toplam uygunluk ile gidiş dönüş yaptığı garanti edilmez. ( *Gidiş dönüş* , bir sınıf kümesi oluşturmak için şemayı içeri aktarma ve bir şemayı yeniden oluşturmak için sonucu dışarı aktarma anlamına gelir.) Aynı şema döndürülmeyebilir. İşlemi ters çevirme, uygunluğu korumak için de garanti edilmez. (Şemasını oluşturmak için bir türü dışarı aktarın ve ardından türü geri alın. Aynı tür döndürülmemiş olabilir.)  
  
## <a name="supported-types"></a>Desteklenen türler  
 Veri anlaşması modeli, WC3 şemasının yalnızca sınırlı bir alt kümesini destekler. Bu alt kümeyle uyumlu olmayan herhangi bir şema, içeri aktarma işlemi sırasında bir özel duruma neden olur. Örneğin, bir veri sözleşmesinin veri üyesinin bir XML özniteliği olarak serileştirilmesi gerektiğini belirtmenin bir yolu yoktur. Bu nedenle, XML özniteliklerinin kullanılmasını gerektiren şemalar desteklenmez ve doğru XML projeksiyonu ile bir veri sözleşmesi oluşturmak imkansız olduğundan içeri aktarma sırasında özel durumlara neden olur.  
  
 Örneğin, aşağıdaki şema parçası varsayılan içeri aktarma ayarları kullanılarak içeri aktarılamaz.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Daha fazla bilgi için bkz. [veri sözleşmesi şema başvurusu](data-contract-schema-reference.md). Bir şema veri sözleşmesi kurallarına uygun değilse, farklı bir serileştirme altyapısı kullanın. Örneğin, <xref:System.Xml.Serialization.XmlSerializer> kendi ayrı şema içeri aktarma mekanizmasını kullanır. Ayrıca, desteklenen şemanın aralığının genişletildiği özel bir içeri aktarma modu vardır. Daha fazla bilgi için, <xref:System.Xml.Serialization.IXmlSerializable> [sınıfları oluşturmak Için şema içeri aktarma](importing-schema-to-generate-classes.md)bölümünde türleri oluşturma hakkında bölümüne bakın.  
  
 , `XsdDataContractExporter` İle serileştirileolabilecek .NET Framework türlerini destekler `DataContractSerializer` . Daha fazla bilgi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](types-supported-by-the-data-contract-serializer.md). Kullanılarak oluşturulan şemanın, `XsdDataContractExporter` genellikle `XsdDataContractImporter` kullanabileceği ( <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Şemayı özelleştirmek için kullanılmadıkları takdirde) geçerli veriler olduğunu unutmayın.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Runtime.Serialization.XsdDataContractImporter> bkz. [sınıfları oluşturmak Için şemayı içeri aktarma](importing-schema-to-generate-classes.md).  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Runtime.Serialization.XsdDataContractExporter> bkz. [sınıflardan şemaları dışarı aktarma](exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Sınıf Oluşturmak için Şemayı İçe Aktarma](importing-schema-to-generate-classes.md)
- [Sınıflardan Şemaları Dışarı Aktarma](exporting-schemas-from-classes.md)

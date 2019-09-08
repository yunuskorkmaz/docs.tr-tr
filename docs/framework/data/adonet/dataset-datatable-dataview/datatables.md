---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: 12255f738dea0a4713389e599468d1a7fab67d23
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784696"
---
# <a name="datatables"></a>DataTables
Bir <xref:System.Data.DataSet> tablo, ilişki ve kısıtlama koleksiyonundan oluşur. ADO.net ' de <xref:System.Data.DataTable> nesneler, bir **veri kümesindeki**tabloları temsil etmek için kullanılır. **DataTable** , bellek içi ilişkisel verilerin bir tablosunu temsil eder; verileri yereldir. İçinde bulunduğu, ancak **DataAdapter** kullanarak Microsoft SQL Server bir veri kaynağından doldurulabilen, daha fazla bilgi için bkz. veri [kümesini DataAdapter 'tan doldurma](../populating-a-dataset-from-a-dataadapter.md).  
  
 **DataTable** sınıfı, .NET Framework sınıf kitaplığı içindeki **System. Data** ad alanının bir üyesidir. Bir **DataTable** 'ı bağımsız olarak veya bir **veri kümesinin**üyesi olarak oluşturabilir ve kullanabilirsiniz ve **datatable** nesneleri de dahil diğer <xref:System.Data.DataView>.NET Framework nesneleriyle birlikte kullanılabilir. **DataSet nesnesinin** **Tables** özelliği aracılığıyla bir **veri kümesindeki** tablo koleksiyonuna erişirsiniz.  
  
 Bir tablonun şeması veya yapısı, sütunlar ve kısıtlamalar ile temsil edilir. <xref:System.Data.DataColumn> Nesneleri<xref:System.Data.UniqueConstraint> ve nesneleri kullanarak bir DataTable şemasını tanımlarsınız. <xref:System.Data.ForeignKeyConstraint> Bir tablodaki sütunlar bir veri kaynağındaki sütunlarla eşlenir, deyimlerden hesaplanan değerler içerebilir, değerlerini otomatik olarak artırır veya birincil anahtar değerleri içerebilir.  
  
 Bir şemanın yanı sıra, bir **DataTable** 'ın de verileri içermesi ve sıralamak için satırları olması gerekir. <xref:System.Data.DataRow> Sınıfı, bir tabloda bulunan gerçek verileri temsil eder. Bir tablodaki verileri almak, değerlendirmek ve işlemek için **DataRow** ve özelliklerini ve yöntemlerini kullanırsınız. Bir satır içindeki verileri erişirken ve değiştirirken, **DataRow** nesnesi hem geçerli hem de orijinal durumunu korur.  
  
 Tablolarda bir veya daha fazla ilişkili sütun kullanarak tablolar arasında üst-alt ilişkileri oluşturabilirsiniz. Kullanarak<xref:System.Data.DataRelation> **DataTable** nesneleri arasında bir ilişki oluşturursunuz. Daha sonra, belirli bir satırın ilişkili alt veya üst satırlarını döndürmek için **DataRelation** nesneleri kullanılabilir. Daha fazla bilgi için bkz. [DataRelation 'ı ekleme](adding-datarelations.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataTable Oluşturma](creating-a-datatable.md)  
 **DataTable** oluşturmayı ve bir **veri kümesine**eklemeyi açıklar.  
  
 [DataTable Şema Tanımı](datatable-schema-definition.md)  
 **DataColumn** nesneleri ve kısıtlamalarını oluşturma ve kullanma hakkında bilgi sağlar.  
  
 [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)  
 Bir tablodaki verilerin nasıl ekleneceğini, değiştirileceğini ve silineceğini açıklar. Tablodaki verilerde yapılan değişiklikleri incelemek için **DataTable** olaylarının nasıl kullanılacağını açıklar.  
  
 [DataTable Olaylarını İşleme](handling-datatable-events.md)  
 Sütun değerleri değiştirildiğinde ve satırlar eklendiğinde veya silindiğinde olaylar da dahil olmak üzere, bir **DataTable**ile kullanılabilecek olaylar hakkında bilgi sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET](../index.md)  
 ADO.NET mimarisini ve bileşenlerini ve bunların mevcut veri kaynaklarına erişmek ve uygulama verilerini yönetmek için nasıl kullanılacağını açıklar.  
  
 [DataSets, DataTables ve DataViews](index.md)  
 Tablolar arasında ilişki oluşturma dahil olmak üzere ADO.NET **veri kümesi** hakkında bilgiler sağlar.  
  
 <xref:System.Data.Constraint>  
 **Kısıtlama** nesnesi hakkında başvuru bilgileri sağlar.  
  
 <xref:System.Data.DataColumn>  
 **DataColumn** nesnesi hakkında başvuru bilgileri sağlar.  
  
 <xref:System.Data.DataSet>  
 **DataSet** nesnesi hakkında başvuru bilgileri sağlar.  
  
 <xref:System.Data.DataTable>  
 **DataTable** nesnesi hakkında başvuru bilgileri sağlar.  
  
 [Sınıf Kitaplığına Genel Bakış](../../../../standard/class-library-overview.md)  
 **Sistem** ad alanı ve **System. Data**dahil olmak üzere, .NET Framework sınıf kitaplığına genel bir bakış sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: f0f429d7f28360fd76dfff0e7d4a4eba019e5acf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653260"
---
# <a name="datatables"></a>DataTables
A <xref:System.Data.DataSet> tablolarını, ilişkileri ve kısıtlamalar koleksiyonu oluşur. ADO.NET, <xref:System.Data.DataTable> nesneler tablolarında temsil etmek için kullanılan bir **veri kümesi**. Bir **DataTable** bellek içi ilişkisel verileri; bir tablosunu temsil eden yerel bir veridir. Burada yer alıyor, ancak Microsoft SQL Server'ı kullanarak gibi bir veri kaynağından doldurulabilir NET tabanlı uygulama bir **DataAdapter** daha fazla bilgi için [dataadapter'dan bir DataSet doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .  
  
 **DataTable** sınıf üyesi olduğu **System.Data** ad alanı .NET Framework sınıf kitaplığı içinde. Oluşturma ve kullanma bir **DataTable** bağımsız olarak veya bir üyesi olarak bir **veri kümesi**, ve **DataTable** nesneleri de kullanılabilir diğer .NET Framework nesneleri ile birlikte dahil olmak üzere <xref:System.Data.DataView>. Tablo koleksiyonu erişim bir **veri kümesi** aracılığıyla **tabloları** özelliği **veri kümesi** nesne.  
  
 Şema veya bir tablonun yapısını, sütunları ve kısıtlamaları tarafından temsil edilir. Şemasını tanımlayan bir **DataTable** kullanarak <xref:System.Data.DataColumn> nesneleri olarak <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint> nesneleri. Bir tablodaki sütunları bir veri kaynağındaki sütun eşleme, ifadeleri hesaplanan değerleri içeren, otomatik olarak değerlerini artırın veya birincil anahtar değerlerini içerir.  
  
 Bir şema, ek bir **DataTable** de içeren ve verileri sıralamak için satır olması gerekir. <xref:System.Data.DataRow> Sınıfı, bir tabloda yer alan gerçek verileri temsil eder. Kullandığınız **DataRow** almak için yöntemler ve özellikleri değerlendirmek ve bir tablodaki verileri işlemek ve. Erişim ve bir satırdaki verileri değiştirmek **DataRow** nesne hem geçerli ve orijinal durumuna tutar.  
  
 Üst-alt kullanarak tablolar arasında ilişkiler oluşturabilirsiniz veya tablolardaki sütunlara ilgili daha fazla. Arasında bir ilişki oluşturmamız **DataTable** kullanarak nesneleri bir <xref:System.Data.DataRelation>. **DataRelation** nesneleri belirli bir satır ilişkili alt veya üst satırları döndürmek için kullanılabilecek. Daha fazla bilgi için [DataRelations ekleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataTable Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Nasıl oluşturulacağını açıklayan bir **DataTable** ve eklemeniz bir **veri kümesi**.  
  
 [DataTable Şema Tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Oluşturma ve kullanma hakkında bilgi sağlar **DataColumn** nesneleri ve kısıtlamalar.  
  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Eklemek, değiştirmek ve tablo verilerini silme açıklanmaktadır. Nasıl kullanılacağını açıklar **DataTable** değişiklikleri tablosundaki verileri incelemek için olayları.  
  
 [DataTable Olaylarını İşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 İle kullanmak için kullanılabilir olaylar hakkında bilgi sağlayan bir **DataTable**, sütun değerler değiştirildiğinde satır eklendiğinde veya silindi ve ne zaman olayları dahil.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 ADO.NET açıklar mimarisi ve bileşenleri ve mevcut veri kaynaklarına erişim ve uygulama verilerini yönetmek için bunları kullanmayı öğrenin.  
  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 ADO.NET hakkında bilgi sağlar **veri kümesi** tablolar arasında ilişki oluşturma da dahil olmak üzere.  
  
 <xref:System.Data.Constraint>  
 Hakkında başvuru bilgileri sağlar **kısıtlaması** nesne.  
  
 <xref:System.Data.DataColumn>  
 Hakkında başvuru bilgileri sağlar **DataColumn** nesne.  
  
 <xref:System.Data.DataSet>  
 Hakkında başvuru bilgileri sağlar **veri kümesi** nesne.  
  
 <xref:System.Data.DataTable>  
 Hakkında başvuru bilgileri sağlar **DataTable** nesne.  
  
 [Sınıf Kitaplığına Genel Bakış](../../../../../docs/standard/class-library-overview.md)  
 .NET Framework sınıf kitaplığına genel bakış sağlar dahil olmak üzere **sistem** ad alanı, ikinci düzey ad alanı yanı sıra **System.Data**.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

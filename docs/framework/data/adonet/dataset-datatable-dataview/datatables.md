---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3803d550fe345c6f485dd204cc119f8a927a3501
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="datatables"></a>DataTables
A <xref:System.Data.DataSet> tabloları, ilişkileri ve kısıtlamalar koleksiyonu oluşur. ADO.NET, <xref:System.Data.DataTable> nesneleri tablolarda belirtmek için kullanılan bir **DataSet**. A **DataTable** bellek içi ilişkisel veri; bir tablo temsil eden veri yerel olması. Burada yer alıyor, ancak Microsoft SQL Server'ı kullanarak gibi bir veri kaynağından doldurulmuş NET tabanlı uygulama bir **DataAdapter** daha fazla bilgi için bkz: [DataAdapter kümesinden doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .  
  
 **DataTable** sınıf üyesi olduğu **System.Data** ad alanı .NET Framework sınıf kitaplığı içinde. Oluşturma ve kullanma bir **DataTable** bağımsız olarak veya bir üyesi olarak bir **DataSet**, ve **DataTable** nesneler de kullanılabilir diğer .NET Framework nesneleri ile birlikte dahil olmak üzere <xref:System.Data.DataView>. Tablo koleksiyonu erişim bir **DataSet** aracılığıyla **tabloları** özelliği **DataSet** nesnesi.  
  
 Şema veya bir tablonun yapısını sütunlar ve kısıtlamalar ile temsil edilir. Şemasını tanımlayan bir **DataTable** kullanarak <xref:System.Data.DataColumn> nesneleri yanı <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint> nesneleri. Bir tablodaki sütun bir veri kaynağındaki sütunları eşlemek, ifadeler hesaplanan değerler içeren, otomatik olarak değerlerine artırın veya birincil anahtar değerlerini içeriyor.  
  
 Bir şema, ek bir **DataTable** de içerir ve veri sipariş satır olması gerekir. <xref:System.Data.DataRow> Sınıfı, bir tabloda bulunan gerçek verileri temsil eder. Kullandığınız **DataRow** ve onun özelliklerini ve yöntemlerini almak için değerlendirmek ve bir tablodaki verileri değiştirmek. Bir satır içindeki verilere erişmek ve değiştikçe **DataRow** nesne hem geçerli ve özgün durumuna korur.  
  
 Üst-alt kullanarak tablolar arasında ilişkiler oluşturun veya tablolardaki sütunların ilgili daha fazla. Arasında bir ilişki Oluştur **DataTable** kullanarak nesneleri bir <xref:System.Data.DataRelation>. **DataRelation** nesneleri sonra belirli bir satır ilgili alt veya üst satırlarını dönmek için kullanılabilir. Daha fazla bilgi için bkz: [ekleme DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataTable Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 Nasıl oluşturulacağını açıklar bir **DataTable** ve ekleyebilmek için bir **DataSet**.  
  
 [DataTable Şema Tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 Oluşturma ve kullanma hakkında bilgi sağlar **DataColumn** nesneleri ve kısıtlamalar.  
  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 Ekleme, değiştirme ve bir tablodaki verileri silme açıklanmaktadır. Nasıl kullanılacağı açıklanmaktadır **DataTable** tablosundaki verilerde yapılan değişiklikleri incelemek için olaylar.  
  
 [DataTable Olaylarını İşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 İle kullanmak için kullanılabilir olan olaylar hakkında bilgi sağlayan bir **DataTable**, sütun değerlerini değiştirildiğinde ve satır eklenmiş veya silinmiş olaylar dahil olmak üzere.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 ADO.NET açıklar mimarisi ve bileşenleri ve bunları mevcut veri kaynaklarına erişmek ve uygulama verilerini yönetmek için kullanma.  
  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 ADO.NET hakkında bilgi sağlar **DataSet** tablolar arasında ilişkiler oluşturmak nasıl dahil olmak üzere.  
  
 <xref:System.Data.Constraint>  
 Hakkında başvuru bilgileri sağlar **kısıtlaması** nesnesi.  
  
 <xref:System.Data.DataColumn>  
 Hakkında başvuru bilgileri sağlar **DataColumn** nesnesi.  
  
 <xref:System.Data.DataSet>  
 Hakkında başvuru bilgileri sağlar **DataSet** nesnesi.  
  
 <xref:System.Data.DataTable>  
 Hakkında başvuru bilgileri sağlar **DataTable** nesnesi.  
  
 [Sınıf Kitaplığına Genel Bakış](../../../../../docs/standard/class-library-overview.md)  
 .NET Framework sınıf kitaplığı genel bir bakış sağlar dahil olmak üzere **sistem** ad alanı, ikinci düzey ad alanı yanı sıra **System.Data**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

---
title: (LINQ to DataSet) sorgudan DataTable oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 0f750f2d23430691016fc2cf1e5e9d44d80da2a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204087"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>(LINQ to DataSet) sorgudan DataTable oluşturma
Veri bağlama yaygın olan <xref:System.Data.DataTable> nesne. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi sorgunun sonuçlarını alır ve verileri kopyalayan bir <xref:System.Data.DataTable>, ardından kullanılabileceği için veri bağlama. Ne zaman veri işlemleri gerçekleştirdi, yeni <xref:System.Data.DataTable> kaynağa geri birleştirilmiş <xref:System.Data.DataTable>.  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi oluşturmak için aşağıdaki işlemi kullanır bir <xref:System.Data.DataTable> sorgudan:  
  
1.  <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi klonlar bir <xref:System.Data.DataTable> kaynak tablosundan (bir <xref:System.Data.DataTable> uygulayan nesne <xref:System.Linq.IQueryable%601> arabirimi). <xref:System.Collections.IEnumerable> Kaynak genellikle alanından kaynaklanan bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu ifadesi veya yöntemi.  
  
2.  Kopyalanan şemasını <xref:System.Data.DataTable> ilk sütunlarından yerleşik numaralandırılan <xref:System.Data.DataRow> nesnedir kaynak tablosu ve kopyalanan tablosunun adı "query", eklenmiş şekilde bir sözcükle kaynak tablosunun adı.  
  
3.  Kaynak tablodaki her satır için içerik satır yeni bir kopyalanır <xref:System.Data.DataRow> sonra kopyalanan tabloya eklenen nesne. <xref:System.Data.DataRow.RowState%2A> Ve <xref:System.Data.DataRow.RowError%2A> özelliklerini kopyalama işlemi korunur. Bir <xref:System.ArgumentException> oluşturulur <xref:System.Data.DataRow> nesnelerdir kaynağındaki farklı tablolardan.  
  
4.  Kopyalanan <xref:System.Data.DataTable> sonuçta döndürülen <xref:System.Data.DataRow> sorgulanabilir giriş tablosundaki nesneler kopyalanır. Kaynak sırası herhangi içermiyorsa <xref:System.Data.DataRow> nesneler, yöntem boş bir döndürür <xref:System.Data.DataTable>.  
  
 Çağırmanın Not <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi yürütmek için kaynak tabloda bağlı sorgu neden olur.  
  
 Zaman <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi, bir null başvuru veya null yapılabilir değer türü kaynak tablosunda bir satıra karşılaştığında, değeri ile değiştirir <xref:System.DBNull.Value>. Bu şekilde, boş değerlerin işlenme düzgün biçimde döndürülen <xref:System.Data.DataTable>.  
  
 Not: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi, birden çok satırlar döndüren bir sorgu girdi olarak kabul <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> nesneleri. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi kaynaktan kopyalar veriler ancak özellikleri <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> döndürülen nesnelere <xref:System.Data.DataTable>. Özellikleri döndürülen üzerinde açıkça ayarlamak ihtiyacınız olacak <xref:System.Data.DataTable>, gibi <xref:System.Data.DataTable.Locale%2A> ve <xref:System.Data.DataTable.TableName%2A>.  
  
 Aşağıdaki örnek, 8 Ağustos 2001'den sonra siparişleri SalesOrderHeader tabloyu sorgular ve kullandığı <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi oluşturmak için bir <xref:System.Data.DataTable> Bu sorgudan. <xref:System.Data.DataTable> Sonra bağlı bir <xref:System.Windows.Forms.BindingSource>, proxy olarak görev yapan bir <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Özel CopyToDataTable oluşturma\<T > yöntemi  
 Varolan <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemleri yalnızca çalışan bir <xref:System.Collections.Generic.IEnumerable%601> kaynak yeri genel parametre `T` türünde <xref:System.Data.DataRow>. Bu faydalı olsa da bir dizi skaler türler, anonim türler döndüren sorgular veya tablo birleştirmeler gerçekleştirme sorguları oluşturulacak tablolar izin vermez. İki özel uygulamak nasıl bir örnek için `CopyToDataTable` bir skaler veya anonim türü dizisinden bir tablo yükleme yöntemlerini [nasıl yapılır: CopyToDataTable uygulamak\<T > Burada T genel türünün DataRow olmadığı](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Bu bölümdeki örneklerde, aşağıdaki özel türlerini kullanır:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Örnek  
 Bu örnek üzerinde birleştirme gerçekleştirir `SalesOrderHeader` ve `SalesOrderDetail` çevrimiçi siparişler Ağustos ay almak için tablolar ve sorgudan bir tablo oluşturur.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyon için fiyat $9.99 büyük öğelerin sorgular ve öğesinden gelen soru sonuçları bir tablo oluşturur.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, fiyat 9,99 büyük öğelerinin bir koleksiyonu sorgular ve sonuçları projeleri. Anonim türdeki döndürülen dizinin var olan bir tabloya yüklenir.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyon öğelerinin fiyat $9.99 büyük sorgular ve sonuçları projeleri. Anonim türdeki döndürülen dizinin var olan bir tabloya yüklenir. Tablo şemasını olduğundan otomatik olarak genişletildiğinden `Book` ve `Movies` sınıfından türetilen türler `Item` türü.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyon için fiyat $9.99 büyük öğelerin sorgular ve bir dizisini döndürür <xref:System.Double>, yeni bir tabloya yüklendi.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [Genel Alan ve SetField Yöntemleri](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
- [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)

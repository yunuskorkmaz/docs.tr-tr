---
title: DataTable bir sorgu (LINQ-DataSet) oluşturuluyor
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: f4ea8749c6e1c853f87f17e735887bbdd4d72e2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>DataTable bir sorgu (LINQ-DataSet) oluşturuluyor
Veri bağlama olduğu ortak bir kullanımını <xref:System.Data.DataTable> nesnesi. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi bir sorgunun sonuçlarını alır ve verileri kopyalayan bir <xref:System.Data.DataTable>, ardından kullanılabileceği için veri bağlama. Veri işlemleri zaman gerçekleştirmiş, yeni <xref:System.Data.DataTable> yeniden kaynağına birleştirilmiş <xref:System.Data.DataTable>.  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi oluşturmak için aşağıdaki işlemi kullanan bir <xref:System.Data.DataTable> sorgudan:  
  
1.  <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi klonlar bir <xref:System.Data.DataTable> kaynak tablosundan (bir <xref:System.Data.DataTable> uygulayan nesne <xref:System.Linq.IQueryable%601> arabirimi). <xref:System.Collections.IEnumerable> Kaynak genellikle alanından kaynaklanan bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ifadesi veya yöntemi sorgu.  
  
2.  Kopyalanan şeması <xref:System.Data.DataTable> ilk sütunlarından yerleşik numaralandırılan <xref:System.Data.DataRow> nesnesidir kaynak tablosu ve kopyalanan tablosunun adı "query", eklenmiş şekilde sözcüğünün kaynak tablosunun adı.  
  
3.  Kaynak tablodaki her satır için satır içeriğini yeni bir dosyaya kopyalanır <xref:System.Data.DataRow> sonra kopyalanan tabloya eklenen nesne. <xref:System.Data.DataRow.RowState%2A> Ve <xref:System.Data.DataRow.RowError%2A> özellikleri arasında kopyalama işlemi korunur. Bir <xref:System.ArgumentException> erişilirse durum <xref:System.Data.DataRow> nesneleridir kaynağındaki farklı tablolardan.  
  
4.  Kopyalanan <xref:System.Data.DataTable> sonuçta döndürülen <xref:System.Data.DataRow> nesneleri giriş sorgulanabilir tablosundaki kopyalanır. Kaynak sıradaki herhangi içermiyorsa <xref:System.Data.DataRow> nesneleri, yöntem boş bir <xref:System.Data.DataTable>.  
  
 Bu arama Not <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi yürütmek için kaynak tabloda ilişkili sorgu neden olur.  
  
 Zaman <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi karşılaştığı bir null başvuru veya kaynak tabloda satırda boş değer atanabilir değer türü, değeri ile değiştirir <xref:System.DBNull.Value>. Bu şekilde, null değerler işlenir doğru şekilde döndürülen <xref:System.Data.DataTable>.  
  
 Not: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi kabul giriş olarak birden çok from satır döndürebilir bir sorgu <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> nesneleri. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi kaynaktan kopyalar verileri ancak özellikleri <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> döndürülen nesnelere <xref:System.Data.DataTable>. Açıkça özellikleri döndürülen üzerinde ayarlamanız gerekir <xref:System.Data.DataTable>, gibi <xref:System.Data.DataTable.Locale%2A> ve <xref:System.Data.DataTable.TableName%2A>.  
  
 Aşağıdaki örnek siparişleri SalesOrderHeader Tablo 8 Ağustos 2001'den sonra sorgular ve kullandığı <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi oluşturmak için bir <xref:System.Data.DataTable> Bu sorgudan. <xref:System.Data.DataTable> Sonra bağlı bir <xref:System.Windows.Forms.BindingSource>, için proxy olarak görev yapan bir <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Özel CopyToDataTable oluşturma\<T > yöntemi  
 Varolan <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemleri yalnızca çalışan bir <xref:System.Collections.Generic.IEnumerable%601> kaynak yeri genel parametresini `T` türü <xref:System.Data.DataRow>. Bu yararlı olsa da, bir dizi skaler türler, anonim türleri döndüren sorgular veya tablo birleştirmeler gerçekleştirme sorguları oluşturulacak tabloları izin vermiyor. İki özel uygulamak nasıl bir örnek için `CopyToDataTable` skaler veya anonim türleri dizisinden bir tablo yükleme yöntemlerini görmek [nasıl yapılır: uygulama CopyToDataTable\<T > burada genel türü T değil bir DataRow satırının](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Bu bölümdeki örnekleri aşağıdaki özel türler kullanın:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Örnek  
 Bu örnek üzerinde birleştirme gerçekleştirir `SalesOrderHeader` ve `SalesOrderDetail` Ağustos, month çevrimiçi olarak sipariş almak için tabloları ve sorgudan bir tablo oluşturur.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, fiyat 9.99 büyük öğelerinin bir koleksiyonu sorgular ve sorgu sonuçlarından bir tablo oluşturur.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, fiyat 9.99 büyük öğelerinin bir koleksiyonu sorgular ve sonuçları projeleri. Anonim türler döndürülen dizi var olan bir tabloya yüklenir.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, fiyat 9.99 büyük öğelerinin bir koleksiyonu sorgular ve sonuçları projeleri. Anonim türler döndürülen dizi var olan bir tabloya yüklenir. Tablo şemasını olduğundan otomatik olarak genişletilir `Book` ve `Movies` öğesinden türetilmiş tür `Item` türü.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, fiyat 9.99 büyük öğelerinin bir koleksiyonu sorgular ve bir dizi döndürür <xref:System.Double>, yeni bir tabloya yüklendi.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [Genel Alan ve SetField Yöntemleri](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)

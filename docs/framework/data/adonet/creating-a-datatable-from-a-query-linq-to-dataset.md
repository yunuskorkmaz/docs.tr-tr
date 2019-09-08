---
title: Sorgudan DataTable oluşturma (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 4b95ec5a3e83fa5553a154ed64704312726153cf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785637"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Sorgudan DataTable oluşturma (LINQ to DataSet)
Veri bağlama, <xref:System.Data.DataTable> nesnenin yaygın bir kullanımı. Yöntemi bir sorgunun sonuçlarını alır ve verileri ' a <xref:System.Data.DataTable>kopyalar ve bu da veri bağlama için kullanılabilir. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Veri işlemleri gerçekleştirildiğinde, yeni <xref:System.Data.DataTable> kaynak <xref:System.Data.DataTable>geri birleştirilir.  
  
 Yöntemi bir sorgudan <xref:System.Data.DataTable> oluşturmak için aşağıdaki işlemi kullanır: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>  
  
1. Yöntemi kaynak tablodan ( <xref:System.Data.DataTable> arabirimini<xref:System.Linq.IQueryable%601> uygulayan bir <xref:System.Data.DataTable> nesne) bir klonlar. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Kaynak <xref:System.Collections.IEnumerable> , genellikle bir LINQ to DataSet ifadesi veya yöntem sorgusundan kaynaklı.  
  
2. Klonlanmış <xref:System.Data.DataTable> öğesinin şeması, kaynak tablodaki ilk numaralandırılmış <xref:System.Data.DataRow> nesnenin sütunlarından oluşturulur ve kopyalanan tablonun adı, "Query" sözcüğünün eklendiği kaynak tablonun adıdır.  
  
3. Kaynak tablodaki her satır için, satırın içeriği yeni <xref:System.Data.DataRow> bir nesneye kopyalanır ve kopyalanan tabloya eklenir. <xref:System.Data.DataRow.RowState%2A> Ve<xref:System.Data.DataRow.RowError%2A> özellikleri kopyalama işlemi boyunca korunur. <xref:System.ArgumentException> Kaynaktaki <xref:System.Data.DataRow> nesneler farklı tablolardan ise oluşturulur.  
  
4. Kopyalanan <xref:System.Data.DataTable> , giriş sorgulanabilir tablosundaki tüm <xref:System.Data.DataRow> nesneler kopyalandıktan sonra döndürülür. Kaynak dizisi herhangi <xref:System.Data.DataRow> bir nesne içermiyorsa, yöntem boş <xref:System.Data.DataTable>döndürür.  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi çağırmanın kaynak tabloya bağlanan sorgunun yürütülmesine neden olacağını unutmayın.  
  
 Yöntem, kaynak tablodaki bir satırda null ya da null değer türü ile karşılaştığında değeri ile <xref:System.DBNull.Value>değiştirir. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Bu şekilde, null değerler döndürülen <xref:System.Data.DataTable>içinde doğru işlenir.  
  
 Not: Yöntemi <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> , birden fazla <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> nesnesinden satırları döndüresağlayan bir sorgu girişi olarak kabul eder. Yöntemi verileri kopyalama, ancak özellikleri kaynak <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> nesnelerden geri döndürülecek <xref:System.Data.DataTable>şekilde değil. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Döndürülen <xref:System.Data.DataTable> ,ve<xref:System.Data.DataTable.TableName%2A>gibiözellikleri açıkça ayarlamanız gerekecektir. <xref:System.Data.DataTable.Locale%2A>  
  
 Aşağıdaki örnek, 5 Ağustos 2001 ' den sonraki siparişler için SalesOrderHeader tablosunu sorgular ve bu sorgudan <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> bir <xref:System.Data.DataTable> oluşturmak için yöntemini kullanır. Daha sonra bir için proxy <xref:System.Windows.Forms.DataGridView>görevi <xref:System.Windows.Forms.BindingSource>gören bir öğesine bağlanır. <xref:System.Data.DataTable>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Özel bir CopyToDataTable\<T > yöntemi oluşturma  
 Mevcut <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemler yalnızca genel parametrenin <xref:System.Collections.Generic.IEnumerable%601> `T` türü<xref:System.Data.DataRow>olan bir kaynak üzerinde çalışır. Bu faydalı olsa da, tabloların, anonim türler döndüren sorgulardan veya tablo birleştirmelerini gerçekleştiren sorgulardan bir skalar türler dizisinden oluşturulmasını izin vermez. Skalar veya anonim türler dizisinden bir tablo yükleyen iki `CopyToDataTable` özel yöntemin nasıl uygulanacağı hakkında bir örnek için bkz [. nasıl yapılır: Genel tür t 'in\<bir DataRow](implement-copytodatatable-where-type-not-a-datarow.md)olmadığından CopyToDataTable T > uygulayın.  
  
 Bu bölümdeki örneklerde aşağıdaki özel türler kullanılır:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Örnek  
 Bu örnek, Ağustos ayında çevrimiçi siparişleri `SalesOrderHeader` almak `SalesOrderDetail` ve sorgudan bir tablo oluştururken, ve tabloları üzerinde bir JOIN gerçekleştirir.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, $9,99 'den büyük bir fiyat öğeleri için bir koleksiyonu sorgular ve sorgu sonuçlarından bir tablo oluşturur.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyonu 9,99 ' den büyük bir fiyat öğeleri için sorgular ve sonuçları projeler için sorgular. Döndürülen anonim türler dizisi varolan bir tabloya yüklenir.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyonu $9,99 ' den büyük bir fiyat öğeleri için sorgular ve sonuçları projeler için sorgular. Döndürülen anonim türler dizisi varolan bir tabloya yüklenir. `Book` Ve`Movies` türleri türündentüretildiğindentabloşemasıotomatikolarakgenişletilir.`Item`  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyonu $9,99 ' den büyük olan öğeler için sorgular ve yeni bir tabloya yüklenen <xref:System.Double>bir dizisini döndürür.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
- [Genel Alan ve SetField Yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)

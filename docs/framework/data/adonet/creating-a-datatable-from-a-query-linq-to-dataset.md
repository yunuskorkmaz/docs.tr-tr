---
title: Sorgudan DataTable oluşturma (LINQ to DataSet)
description: Bir sorgunun sonuçlarını almak ve verileri bir DataTable 'a kopyalamak için, daha sonra veri bağlama için kullanılabilecek CopyToDataTable metodunu kullanmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 0a7c8f005b90484ef2f9c7e48218bda40533696a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287018"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Sorgudan DataTable oluşturma (LINQ to DataSet)
Veri bağlama, nesnenin yaygın bir kullanımı <xref:System.Data.DataTable> . <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Yöntemi bir sorgunun sonuçlarını alır ve verileri ' a kopyalar ve <xref:System.Data.DataTable> Bu da veri bağlama için kullanılabilir. Veri işlemleri gerçekleştirildiğinde, yeni <xref:System.Data.DataTable> kaynak geri birleştirilir <xref:System.Data.DataTable> .  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Yöntemi bir sorgudan oluşturmak için aşağıdaki işlemi kullanır <xref:System.Data.DataTable> :  
  
1. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Yöntemi <xref:System.Data.DataTable> kaynak tablodan ( <xref:System.Data.DataTable> arabirimini uygulayan bir nesne) bir klonlar <xref:System.Linq.IQueryable%601> . <xref:System.Collections.IEnumerable>Kaynak, genellikle bir LINQ to DataSet ifadesi veya yöntem sorgusundan kaynaklı.  
  
2. Klonlanmış öğesinin şeması, <xref:System.Data.DataTable> kaynak tablodaki ilk numaralandırılmış nesnenin sütunlarından oluşturulur <xref:System.Data.DataRow> ve kopyalanan tablonun adı, "Query" sözcüğünün eklendiği kaynak tablonun adıdır.  
  
3. Kaynak tablodaki her satır için, satırın içeriği yeni bir <xref:System.Data.DataRow> nesneye kopyalanır ve kopyalanan tabloya eklenir. <xref:System.Data.DataRow.RowState%2A>Ve <xref:System.Data.DataRow.RowError%2A> özellikleri kopyalama işlemi boyunca korunur. <xref:System.ArgumentException> <xref:System.Data.DataRow> Kaynaktaki nesneler farklı tablolardan ise oluşturulur.  
  
4. Kopyalanan, <xref:System.Data.DataTable> <xref:System.Data.DataRow> giriş sorgulanabilir tablosundaki tüm nesneler kopyalandıktan sonra döndürülür. Kaynak dizisi herhangi bir <xref:System.Data.DataRow> nesne içermiyorsa, yöntem boş döndürür <xref:System.Data.DataTable> .  
  
Yöntemi çağırmak, <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> kaynak tabloya bağlantılı sorgunun yürütülmesine neden olur.  
  
 Yöntem, <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> kaynak tablodaki bir satırda null ya da null değer türü ile karşılaştığında değeri ile değiştirir <xref:System.DBNull.Value> . Bu şekilde, null değerler döndürülen içinde doğru işlenir <xref:System.Data.DataTable> .  
  
 Note: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi, birden fazla veya nesneden satır döndürebileceğini bir sorgu girişi olarak kabul eder <xref:System.Data.DataTable> <xref:System.Data.DataSet> . <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Yöntemi verileri kopyalama, ancak özellikleri kaynak <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> nesnelerden geri döndürülecek şekilde değil <xref:System.Data.DataTable> . Döndürülen, ve gibi özellikleri açıkça ayarlamanız gerekecektir <xref:System.Data.DataTable> <xref:System.Data.DataTable.Locale%2A> <xref:System.Data.DataTable.TableName%2A> .  
  
 Aşağıdaki örnek, 5 Ağustos 2001 ' den sonraki siparişler için SalesOrderHeader tablosunu sorgular ve <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Bu sorgudan bir oluşturmak için yöntemini kullanır <xref:System.Data.DataTable> . <xref:System.Data.DataTable>Daha sonra bir <xref:System.Windows.Forms.BindingSource> için proxy görevi gören bir öğesine bağlanır <xref:System.Windows.Forms.DataGridView> .  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Özel bir CopyToDataTable \<T> yöntemi oluşturma  
 Mevcut <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemler yalnızca <xref:System.Collections.Generic.IEnumerable%601> genel parametrenin türü olan bir kaynak üzerinde çalışır `T` <xref:System.Data.DataRow> . Bu faydalı olsa da, tabloların, anonim türler döndüren sorgulardan veya tablo birleştirmelerini gerçekleştiren sorgulardan bir skalar türler dizisinden oluşturulmasını izin vermez. Skalar veya anonim türler dizisinden bir tablo yükleyen iki özel yöntemin nasıl uygulanacağı hakkında bir örnek için `CopyToDataTable` bkz. [nasıl yapılır: \<T> genel tür T bir DataRow değil, CopyToDataTable uygulama](implement-copytodatatable-where-type-not-a-datarow.md).  
  
 Bu bölümdeki örneklerde aşağıdaki özel türler kullanılır:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Örnek  
 Bu örnek, `SalesOrderHeader` `SalesOrderDetail` Ağustos ayında çevrimiçi siparişleri almak ve sorgudan bir tablo oluştururken, ve tabloları üzerinde bir JOIN gerçekleştirir.  
  
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
 Aşağıdaki örnek, bir koleksiyonu $9,99 ' den büyük bir fiyat öğeleri için sorgular ve sonuçları projeler için sorgular. Döndürülen anonim türler dizisi varolan bir tabloya yüklenir. `Book`Ve `Movies` türleri türünden türetildiğinden tablo şeması otomatik olarak genişletilir `Item` .  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyonu $9,99 ' den büyük olan öğeler için sorgular ve yeni bir tabloya yüklenen bir dizisini döndürür <xref:System.Double> .  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
- [Genel Alan ve SetField Yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)

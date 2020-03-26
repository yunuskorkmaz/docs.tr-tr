---
title: Sorgudan Veri Tablosu Oluşturma (LINQ'dan DataSet'e)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 46e977088cd6eca7842565ae6b258f70ca5920a9
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111822"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Sorgudan Veri Tablosu Oluşturma (LINQ'dan DataSet'e)
Veri bağlama nesnenin <xref:System.Data.DataTable> yaygın bir kullanımıdır. Yöntem, <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> bir sorgunun sonuçlarını alır ve verileri <xref:System.Data.DataTable>veri bağlama için kullanılabilecek bir , Veri işlemleri gerçekleştirildiğinde, yeni <xref:System.Data.DataTable> kaynakla <xref:System.Data.DataTable>yeniden birleştirilir.  
  
 Yöntem, <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> bir sorgudan bir <xref:System.Data.DataTable> sözcük oluşturmak için aşağıdaki işlemi kullanır:  
  
1. Yöntem <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> kaynak tablodan <xref:System.Data.DataTable> <xref:System.Linq.IQueryable%601> (arabirimi <xref:System.Data.DataTable> uygulayan bir nesne) a klonlar. <xref:System.Collections.IEnumerable> Kaynak genellikle bir LINQ'dan DataSet ifadesine veya yöntem sorgusuna kadar kaynaklanmaktadır.  
  
2. Klonlanan <xref:System.Data.DataTable> şema, kaynak tablodaki ilk numaralandırılmış <xref:System.Data.DataRow> nesnenin sütunlarından oluşturulur ve klonlanan tablonun adı, "sorgu" sözcüğünün eklenmiş olduğu kaynak tablonun adıdır.  
  
3. Kaynak tablodaki her satır için, satırın içeriği yeni <xref:System.Data.DataRow> bir nesneye kopyalanır ve daha sonra klonlanmış tabloya eklenir. Ve <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRow.RowError%2A> özellikleri kopyalama işlemi boyunca korunur. Kaynaktaki <xref:System.ArgumentException> <xref:System.Data.DataRow> nesneler farklı tablolardan geliyorsa bir atılmıştır.  
  
4. Klonlama, <xref:System.Data.DataTable> giriş sorgulanabilir <xref:System.Data.DataRow> tablosundaki tüm nesneler kopyalandıktan sonra döndürülür. Kaynak sıra herhangi bir <xref:System.Data.DataRow> nesne içermiyorsa, <xref:System.Data.DataTable>yöntem boş bir .  
  
<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntemi çağırmak, sorgunun yürütülmesi için kaynak tabloya bağlı neden olur.  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntem, kaynak tablodaki bir satırda null reference veya nullable değer türüyle <xref:System.DBNull.Value>karşılaştığında, değeri . Bu şekilde, null değerleri döndürülen <xref:System.Data.DataTable>doğru işlenir.  
  
 Not: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Yöntem, birden çok <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> nesneden satır döndürebilen bir sorgu yu girdi olarak kabul eder. Yöntem <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> verileri kopyalar, ancak kaynaktan <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> nesnelerden döndürülen <xref:System.Data.DataTable>özellikleri kopyalamaz. İade <xref:System.Data.DataTable>edilen özellikleri açıkça ayarlamanız gerekir , <xref:System.Data.DataTable.Locale%2A> örneğin <xref:System.Data.DataTable.TableName%2A>ve .  
  
 Aşağıdaki örnek, 8 Ağustos 2001'den sonra siparişler için SalesOrderHeader tablosunu sorgular ve bu sorgudan bir yöntem <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> <xref:System.Data.DataTable> oluşturmak için yöntemi kullanır. Daha <xref:System.Data.DataTable> sonra bir <xref:System.Windows.Forms.BindingSource>için proxy olarak hareket <xref:System.Windows.Forms.DataGridView>eden bir bağlıdır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Özel CopyToDataTable\<T> Yöntemi Oluşturma  
 Varolan <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemler yalnızca <xref:System.Collections.Generic.IEnumerable%601> genel parametrenin `T` türünde <xref:System.Data.DataRow>olduğu bir kaynakta çalışır. Bu yararlı olsa da, tabloların skaler türleri dizisinden, anonim türleri döndüren sorgulardan veya tablo birleştirmelerini gerçekleştiren sorgulardan oluşturulmasına izin vermez. Bir tabloyu skaler veya `CopyToDataTable` anonim türler dizisinden yükleyen iki özel yöntemin nasıl uygulanacağı hakkında bkz [>.\<](implement-copytodatatable-where-type-not-a-datarow.md)  
  
 Bu bölümdeki örnekler aşağıdaki özel türleri kullanır:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Örnek  
 Bu örnek, Ağustos `SalesOrderHeader` ayından `SalesOrderDetail` çevrimiçi sipariş almak için tablolar ve tablolar üzerinde birbirleştirme gerçekleştirir ve sorgudan bir tablo oluşturur.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, 9,99 TL'den büyük fiyat öğeleri için bir koleksiyon sorgular ve sorgu sonuçlarından bir tablo oluşturur.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, 9,99'dan büyük fiyat kalemleri için bir koleksiyonu sorgular ve sonuçları projeleri. Döndürülen anonim türler dizisi varolan bir tabloya yüklenir.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, 9,99 TL'den büyük fiyat kalemleri için bir koleksiyonu sorgular ve sonuçları projeleri. Döndürülen anonim türler dizisi varolan bir tabloya yüklenir. Tablo şeması otomatik olarak genişletilir, `Book` `Movies` çünkü türler ve `Item` türler türden türetilmiştir.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, 9,99 TL'den büyük fiyatlı öğeler için bir <xref:System.Double>koleksiyon sorgular ve yeni bir tabloya yüklenen bir dizi döndürür.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)
- [Genel Alan ve SetField Yöntemleri](generic-field-and-setfield-methods-linq-to-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)

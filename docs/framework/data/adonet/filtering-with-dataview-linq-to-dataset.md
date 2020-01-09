---
title: DataView ile filtreleme (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: 426e8c43f0ff8af94ab56230cf002637f351cd75
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634865"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>DataView ile filtreleme (LINQ to DataSet)
Belirli ölçütlere göre verileri filtreleyebilme ve sonra verileri bir kullanıcı arabirimi denetimi aracılığıyla bir istemciye sunma özelliği, veri bağlamanın önemli bir yönüdür. <xref:System.Data.DataView>, verileri filtrelemeye ve belirli filtre ölçütlerine uyan veri satırlarının alt kümelerini döndürmeye yönelik çeşitli yollar sağlar. Dize tabanlı filtreleme özelliklerine ek olarak, <xref:System.Data.DataView> filtreleme ölçütlerine yönelik LINQ ifadelerini kullanma olanağı da sağlar. LINQ ifadeleri, dize tabanlı filtrelemeden çok daha karmaşık ve güçlü filtreleme işlemlerine izin verir.  
  
 <xref:System.Data.DataView>kullanarak verileri filtrelemek için iki yol vardır:  
  
- WHERE yan tümcesi içeren bir LINQ to DataSet sorgusundan <xref:System.Data.DataView> oluşturun.  
  
- <xref:System.Data.DataView>için mevcut, dize tabanlı filtreleme yeteneklerini kullanın.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Filtreleme bilgileriyle bir sorgudan DataView oluşturma  
 Bir <xref:System.Data.DataView> nesnesi, bir LINQ to DataSet sorgusundan oluşturulabilir. Bu sorgu bir `Where` yan tümcesi içeriyorsa, <xref:System.Data.DataView>, sorgudan filtreleme bilgileriyle oluşturulur. `Where` yan tümcesindeki ifade, <xref:System.Data.DataView>hangi veri satırlarının ekleneceğini ve filtrenin temelini olduğunu belirlemede kullanılır.  
  
 İfade tabanlı filtreler, daha basit dize tabanlı filtrelerle daha güçlü ve karmaşık filtreleme sağlar. Dize tabanlı ve ifade tabanlı filtreler birbirini dışlıyor. Bir sorgudan bir <xref:System.Data.DataView> oluşturulduktan sonra dize tabanlı <xref:System.Data.DataView.RowFilter%2A> ayarlandığında, sorgudan çıkarılan ifade tabanlı filtre temizlenir.  
  
> [!NOTE]
> Çoğu durumda, filtreleme için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir. Ayrıca, filtreleme işlemleri herhangi bir sayıda yürütülemediğinden, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderDetail tablosunu 2 ' den büyük ve 6 ' dan az bir miktara sahip siparişler için sorgular. Bu sorgudan bir <xref:System.Data.DataView> oluşturur; ve <xref:System.Data.DataView> bir <xref:System.Windows.Forms.BindingSource>bağlar:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, 6 Haziran 2001 ' den sonra verilen siparişler için bir sorgudan bir <xref:System.Data.DataView> oluşturur:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Örnek  
 Filtreleme, sıralama ile de birleştirilebilir. Aşağıdaki örnek, son adı "S" ile başlayan ve son ada göre sıralanan kişiler için bir sorgudan bir <xref:System.Data.DataView> oluşturur, sonra adı:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, son adı "Zhu" ile benzer olan kişileri bulmak için SoundEx algoritmasını kullanır. SoundEx algoritması, SoundEx yönteminde uygulanır.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx, ilk başta ABD Census Bürosu tarafından geliştirilen Ingilizce 'ye göre, adları sese göre dizine ekleme için kullanılan bir fonetik algoritmadır. SoundEx yöntemi, Ingilizce harfinden sonra üç sayıdan oluşan bir ad için dört karakter kodu döndürür. Harf, adın ilk harftir ve sayıların adı kalan ünsüzler kodlayın. Benzer bir sounding adı aynı SoundEx kodunu paylaşır. Önceki örnekte bulunan SoundEx yönteminde kullanılan SoundEx uygulamasının şurada gösterildiği:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>RowFilter özelliğini kullanma  
 <xref:System.Data.DataView> dize tabanlı filtreleme işlevselliği LINQ to DataSet bağlamında hala işe yarar. Dize tabanlı <xref:System.Data.DataView.RowFilter%2A> filtreleme hakkında daha fazla bilgi için bkz. [verileri sıralama ve filtreleme](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Aşağıdaki örnek, kişi tablosundan bir <xref:System.Data.DataView> oluşturur ve sonra <xref:System.Data.DataView.RowFilter%2A> özelliğini, kişinin en son adının "Zhu" olduğu satırları döndürecek şekilde ayarlar:  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Bir <xref:System.Data.DataTable> veya LINQ to DataSet sorgusundan bir <xref:System.Data.DataView> oluşturulduktan sonra, sütun değerlerine göre satır alt kümelerini belirtmek için <xref:System.Data.DataView.RowFilter%2A> özelliğini kullanabilirsiniz. Dize tabanlı ve ifade tabanlı filtreler birbirini dışlıyor. <xref:System.Data.DataView.RowFilter%2A> özelliğinin ayarlanması, LINQ to DataSet sorgusundan çıkarılan filtre ifadesini temizler ve filtre ifadesi sıfırlanamaz.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Verilerin bir alt kümesinin dinamik görünümünü sağlamanın aksine, veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, <xref:System.Data.DataView.RowFilter%2A> özelliğini ayarlamak yerine <xref:System.Data.DataView><xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerini kullanabilirsiniz. <xref:System.Data.DataView.RowFilter%2A> özelliği, bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır. <xref:System.Data.DataView.RowFilter%2A> özelliğini ayarlamak, verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır. <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemleri, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizini kullanır. <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yalnızca bir kez çağrıyorsa, var olan <xref:System.Data.DataView>kullanmanız gerekir. <xref:System.Data.DataView.Find%2A> veya birden çok kez <xref:System.Data.DataView.FindRows%2A> çağrmanız durumunda, arama yapmak istediğiniz sütunda dizini yeniden oluşturmak için yeni bir <xref:System.Data.DataView> oluşturmanız ve ardından <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerini çağırmanız gerekir. <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemleri hakkında daha fazla bilgi için bkz. [satırları bulma](./dataset-datatable-dataview/finding-rows.md) ve [DataView performansı](dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Filtre temizleniyor  
 <xref:System.Data.DataView> filtresi, filtreleme <xref:System.Data.DataView.RowFilter%2A> özelliği kullanılarak ayarlandıktan sonra temizlenir. <xref:System.Data.DataView> filtresi iki farklı şekilde temizlenebilir:  
  
- Ayarlama <xref:System.Data.DataView.RowFilter%2A> özelliğini `null`.  
  
- <xref:System.Data.DataView.RowFilter%2A> özelliğini boş bir dizeye ayarlayın.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorgudan bir <xref:System.Data.DataView> oluşturur ve sonra <xref:System.Data.DataView.RowFilter%2A> özelliğini `null`olarak ayarlayarak filtreyi temizler:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek bir tablosundan bir <xref:System.Data.DataView> oluşturur <xref:System.Data.DataView.RowFilter%2A> özelliğini ayarlar ve sonra <xref:System.Data.DataView.RowFilter%2A> özelliğini boş bir dize olarak ayarlayarak filtreyi temizler:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [DataView ile Sıralama](sorting-with-dataview-linq-to-dataset.md)

---
title: DataView ile filtreleme (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: 9b4c8e9730dde7d19df9e6a11052ae4591465ea7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177468"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>DataView ile filtreleme (LINQ to DataSet)

Belirli ölçütlere göre verileri filtreleyebilme ve sonra verileri bir kullanıcı arabirimi denetimi aracılığıyla bir istemciye sunma özelliği, veri bağlamanın önemli bir yönüdür. <xref:System.Data.DataView> Verileri filtrelemeye ve belirli filtre ölçütlerine uyan veri satırlarının alt kümelerini döndürmeye yönelik çeşitli yollar sağlar. Dize tabanlı filtreleme özelliklerine ek olarak, <xref:System.Data.DataView> filtreleme ölçütleri IÇIN LINQ ifadeleri kullanma olanağı da sağlar. LINQ ifadeleri, dize tabanlı filtrelemeden çok daha karmaşık ve güçlü filtreleme işlemlerine izin verir.  
  
 Kullanarak verileri filtrelemek için iki yol vardır <xref:System.Data.DataView> :  
  
- <xref:System.Data.DataView>WHERE yan tümcesiyle bir LINQ to DataSet sorgusundan oluştur.  
  
- Öğesinin mevcut, dize tabanlı filtreleme yeteneklerini kullanın <xref:System.Data.DataView> .  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Filtreleme bilgileriyle bir sorgudan DataView oluşturma  

 Bir <xref:System.Data.DataView> nesne, bir LINQ to DataSet sorgusundan oluşturulabilir. Bu sorgu bir yan tümce içeriyorsa, bu `Where` , <xref:System.Data.DataView> sorgudaki filtreleme bilgileriyle oluşturulur. Yan tümcesindeki ifade, `Where` hangi veri satırlarının ekleneceğini <xref:System.Data.DataView> ve filtrenin temelini olduğunu belirlemede kullanılır.  
  
 İfade tabanlı filtreler, daha basit dize tabanlı filtrelerle daha güçlü ve karmaşık filtreleme sağlar. Dize tabanlı ve ifade tabanlı filtreler birbirini dışlıyor. Dize tabanlı, bir <xref:System.Data.DataView.RowFilter%2A> sorgudan oluşturulduktan sonra ayarlandığında <xref:System.Data.DataView> , sorgudan çıkarılan ifade tabanlı filtre temizlenir.  
  
> [!NOTE]
> Çoğu durumda, filtreleme için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir. Ayrıca, filtreleme işlemleri herhangi bir sayıda yürütülemediğinden, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, SalesOrderDetail tablosunu 2 ' den büyük ve 6 ' dan az bir miktara sahip siparişler için sorgular. <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' a bağlar <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource> :  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek <xref:System.Data.DataView> , 6 haziran 2001 ' den sonra verilen siparişler için bir sorgudan bir sorgu oluşturur:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Örnek  

 Filtreleme, sıralama ile de birleştirilebilir. Aşağıdaki örnek, <xref:System.Data.DataView> son adı "S" ile başlayan ve son ada göre sıralanan kişiler için bir sorgudan bir sorgu oluşturur ve sonra adı:  
  
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

 Mevcut dize tabanlı filtreleme işlevselliği <xref:System.Data.DataView> LINQ to DataSet bağlamda hala işe yarar. Dize tabanlı filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView.RowFilter%2A> bkz. [verileri sıralama ve filtreleme](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Aşağıdaki örnek, <xref:System.Data.DataView> kişi tablosundan bir oluşturur ve sonra <xref:System.Data.DataView.RowFilter%2A> özelliği, kişinin en son adının "Zhu" olduğu satırları döndürecek şekilde ayarlar:  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Bir <xref:System.Data.DataView> <xref:System.Data.DataTable> veya LINQ to DataSet sorgusundan oluşturulduktan sonra, <xref:System.Data.DataView.RowFilter%2A> sütun değerlerine göre satır alt kümelerini belirtmek için özelliğini kullanabilirsiniz. Dize tabanlı ve ifade tabanlı filtreler birbirini dışlıyor. Özelliği ayarlamak <xref:System.Data.DataView.RowFilter%2A> LINQ to DataSet sorgusundan çıkarılan filtre ifadesini temizler ve filtre ifadesi sıfırlanamaz.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Verilerin bir alt kümesinin dinamik görünümünü sağlamanın aksine, veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, <xref:System.Data.DataView.Find%2A> özelliği ayarlamak yerine, veya <xref:System.Data.DataView.FindRows%2A> yöntemlerini kullanabilirsiniz <xref:System.Data.DataView> <xref:System.Data.DataView.RowFilter%2A> . <xref:System.Data.DataView.RowFilter%2A>Özelliği, bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır. Özelliği ayarlamak <xref:System.Data.DataView.RowFilter%2A> , verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır. <xref:System.Data.DataView.Find%2A>Ve <xref:System.Data.DataView.FindRows%2A> yöntemleri, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizini kullanır. <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> Yalnızca bir kez çağrıyorsa, var olanı kullanmanız gerekir <xref:System.Data.DataView> . Arayacağım <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez arıyorsanız, <xref:System.Data.DataView> arama yapmak istediğiniz sütunda dizini yeniden oluşturmak için yeni bir oluşturmanız ve ardından <xref:System.Data.DataView.Find%2A> veya yöntemlerini çağırmanız gerekir <xref:System.Data.DataView.FindRows%2A> . Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> bkz. [satırları bulma](./dataset-datatable-dataview/finding-rows.md) ve [DataView performansı](dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Filtre temizleniyor  

 Filtre, <xref:System.Data.DataView> özelliği kullanılarak filtrelemeden sonra temizlenir <xref:System.Data.DataView.RowFilter%2A> . Bir üzerinde filtre <xref:System.Data.DataView> iki farklı şekilde temizlenebilir:  
  
- <xref:System.Data.DataView.RowFilter%2A>Özelliğini olarak ayarlayın `null` .  
  
- <xref:System.Data.DataView.RowFilter%2A>Özelliği boş bir dizeye ayarlayın.  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek bir sorgudan bir <xref:System.Data.DataView> sorgu oluşturur ve sonra özelliği şu şekilde ayarlayarak filtreyi temizler <xref:System.Data.DataView.RowFilter%2A> `null` :  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek bir tablodan bir oluşturur <xref:System.Data.DataView> <xref:System.Data.DataView.RowFilter%2A> , özelliği ayarlar ve sonra <xref:System.Data.DataView.RowFilter%2A> özelliği boş bir dizeye ayarlayarak filtreyi temizler:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [DataView ile Sıralama](sorting-with-dataview-linq-to-dataset.md)

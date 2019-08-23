---
title: DataView ile filtreleme (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: aaa9ac0514f3e79f101bbcd9cbab60929f91d4fd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959126"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>DataView ile filtreleme (LINQ to DataSet)
Belirli ölçütlere göre verileri filtreleyebilme ve sonra verileri bir kullanıcı arabirimi denetimi aracılığıyla bir istemciye sunma özelliği, veri bağlamanın önemli bir yönüdür. <xref:System.Data.DataView>Verileri filtrelemeye ve belirli filtre ölçütlerine uyan veri satırlarının alt kümelerini döndürmeye yönelik çeşitli yollar sağlar. Dize tabanlı filtreleme özelliklerine <xref:System.Data.DataView> ek olarak, filtreleme ölçütlerine yönelik ifadeler kullanma [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] olanağı da sağlar. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]ifadeler, dize tabanlı filtrelemeden çok daha karmaşık ve güçlü filtreleme işlemlerine izin verir.  
  
 Kullanarak verileri filtrelemek için iki yol vardır <xref:System.Data.DataView>:  
  
- <xref:System.Data.DataView> WHERE yan tümcesiyle bir LINQ to DataSet sorgusundan oluştur.  
  
- Öğesinin <xref:System.Data.DataView>mevcut, dize tabanlı filtreleme yeteneklerini kullanın.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Filtreleme bilgileriyle bir sorgudan DataView oluşturma  
 Bir <xref:System.Data.DataView> nesne, bir LINQ to DataSet sorgusundan oluşturulabilir. Bu sorgu bir `Where` yan tümce içeriyorsa, bu <xref:System.Data.DataView> , sorgudaki filtreleme bilgileriyle oluşturulur. `Where` Yan tümcesindeki ifade, hangi veri satırlarının ekleneceğini <xref:System.Data.DataView>ve filtrenin temelini olduğunu belirlemede kullanılır.  
  
 İfade tabanlı filtreler, daha basit dize tabanlı filtrelerle daha güçlü ve karmaşık filtreleme sağlar. Dize tabanlı ve ifade tabanlı filtreler birbirini dışlıyor. Dize tabanlı <xref:System.Data.DataView.RowFilter%2A> , bir sorgudan oluşturulduktan <xref:System.Data.DataView> sonra ayarlandığında, sorgudan çıkarılan ifade tabanlı filtre temizlenir.  
  
> [!NOTE]
> Çoğu durumda, filtreleme için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir. Ayrıca, filtreleme işlemleri herhangi bir sayıda yürütülemediğinden, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderDetail tablosunu 2 ' den büyük ve 6 ' dan az bir miktara sahip siparişler için sorgular. Bu sorgudan <xref:System.Data.DataView> bir oluşturur ve ' a <xref:System.Data.DataView> bağlar <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, 6 Haziran <xref:System.Data.DataView> 2001 ' den sonra verilen siparişler için bir sorgudan bir sorgu oluşturur:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Örnek  
 Filtreleme, sıralama ile de birleştirilebilir. Aşağıdaki örnek, son adı <xref:System.Data.DataView> "S" ile başlayan ve son ada göre sıralanan kişiler için bir sorgudan bir sorgu oluşturur ve sonra adı:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, son adı "Zhu" ile benzer olan kişileri bulmak için SoundEx algoritmasını kullanır. SoundEx algoritması, SoundEx yönteminde uygulanır.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx, ilk başta ABD tarafından geliştirilen ve Ingilizce olarak gösterildiği gibi, adları sese göre dizine ekleme için kullanılan bir fonetik algoritmadır. Census Bürosu. SoundEx yöntemi, Ingilizce harfinden sonra üç sayıdan oluşan bir ad için dört karakter kodu döndürür. Harf, adın ilk harftir ve sayıların adı kalan ünsüzler kodlayın. Benzer bir sounding adı aynı SoundEx kodunu paylaşır. Önceki örnekte bulunan SoundEx yönteminde kullanılan SoundEx uygulamasının şurada gösterildiği:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>RowFilter özelliğini kullanma  
 Mevcut dize tabanlı filtreleme işlevselliği <xref:System.Data.DataView> LINQ to DataSet bağlamda hala işe yarar. Dize tabanlı <xref:System.Data.DataView.RowFilter%2A> filtreleme hakkında daha fazla bilgi için bkz. [verileri sıralama ve filtreleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Aşağıdaki örnek, kişi tablosundan <xref:System.Data.DataView> bir oluşturur ve sonra <xref:System.Data.DataView.RowFilter%2A> özelliği, kişinin en son adının "Zhu" olduğu satırları döndürecek şekilde ayarlar:  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Bir veya LINQ to DataSet sorgusundan oluşturulduktan sonra <xref:System.Data.DataView.RowFilter%2A> , sütun değerlerine göre satır alt kümelerini belirtmek için özelliğini kullanabilirsiniz. <xref:System.Data.DataTable> <xref:System.Data.DataView> Dize tabanlı ve ifade tabanlı filtreler birbirini dışlıyor. <xref:System.Data.DataView.RowFilter%2A> Özelliği ayarlamak LINQ to DataSet sorgusundan çıkarılan filtre ifadesini temizler ve filtre ifadesi sıfırlanamaz.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Verilerin bir alt kümesinin dinamik görünümünü sağlamanın aksine, veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek <xref:System.Data.DataView.Find%2A> istiyorsanız, <xref:System.Data.DataView.RowFilter%2A> özelliği ayarlamak yerine, veya <xref:System.Data.DataView.FindRows%2A> yöntemlerini <xref:System.Data.DataView>kullanabilirsiniz. Özelliği <xref:System.Data.DataView.RowFilter%2A> , bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır. <xref:System.Data.DataView.RowFilter%2A> Özelliği ayarlamak, verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır. Ve <xref:System.Data.DataView.Find%2A> yöntemleri <xref:System.Data.DataView.FindRows%2A> , dizinin yeniden oluşturulmasını gerektirmeden geçerli dizini kullanır. Yalnızca bir kez çağrıyorsa <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView>, var olanı kullanmanız gerekir. <xref:System.Data.DataView.FindRows%2A> Arayacağım <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez arıyorsanız, arama <xref:System.Data.DataView.Find%2A> yapmak istediğiniz sütunda dizini yeniden oluşturmak <xref:System.Data.DataView> için yeni bir oluşturmanız ve ardından veya <xref:System.Data.DataView.FindRows%2A> yöntemlerini çağırmanız gerekir. <xref:System.Data.DataView.Find%2A> Ve<xref:System.Data.DataView.FindRows%2A> yöntemleri hakkında daha fazla bilgi için bkz. [satırları bulma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md) ve [DataView performansı](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Filtre temizleniyor  
 Filtre, <xref:System.Data.DataView.RowFilter%2A> özelliği kullanılarak filtrelemeden sonra temizlenir. <xref:System.Data.DataView> Bir <xref:System.Data.DataView> üzerinde filtre iki farklı şekilde temizlenebilir:  
  
- Ayarlama <xref:System.Data.DataView.RowFilter%2A> özelliğini `null`.  
  
- <xref:System.Data.DataView.RowFilter%2A> Özelliği boş bir dizeye ayarlayın.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek bir sorgudan bir <xref:System.Data.DataView> sorgu oluşturur ve sonra özelliği şu şekilde `null`ayarlayarak <xref:System.Data.DataView.RowFilter%2A> filtreyi temizler:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek bir tablodan bir <xref:System.Data.DataView> oluşturur, <xref:System.Data.DataView.RowFilter%2A> özelliği ayarlar ve sonra <xref:System.Data.DataView.RowFilter%2A> özelliği boş bir dizeye ayarlayarak filtreyi temizler:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [DataView ile Sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)

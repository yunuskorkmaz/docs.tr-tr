---
title: (LINQ to DataSet) DataView ile filtreleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: 41e099cdca4f02231fd4b1cc8bce2c4b1e511c71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878832"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>(LINQ to DataSet) DataView ile filtreleme
Ardından bir UI denetimine üzerinden bir istemciye verileri sunmak ve belirli ölçütleri kullanarak veri filtreleme olanağı, veri bağlama, önemli bir yönüdür. <xref:System.Data.DataView> verileri filtreleme ve toplantı belirli filtre ölçütlerini veri satırları kümelerine döndürmek için birçok yol sağlar. Dize tabanlı yanı sıra filtreleme yetenekleri <xref:System.Data.DataView> kullanma olanağı da sağlar [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] ifadeleri filtreleme ölçütlerine. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] ifadeler, dize tabanlı filtreleme daha çok daha karmaşık ve güçlü filtreleme işlemleri için izin verin.  
  
 Kullanarak verilere filtre uygulamak iki yolla bir <xref:System.Data.DataView>:  
  
- Oluşturma bir <xref:System.Data.DataView> gelen bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu ile bir Where yan tümcesi.  
  
- Var olan ve dize tabanlı filtreleme yeteneklerini kullanın <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Bir sorgunun filtre bilgilerle DataView oluşturma  
 A <xref:System.Data.DataView> nesne öğesinden oluşturulabilir bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu. Bu sorgu içeriyorsa bir `Where` yan tümcesi <xref:System.Data.DataView> sorguyu filtreleme bilgilerle oluşturulur. İfadede `Where` yan tümcesi hangi veri satırları dahil edilecek belirlemek için kullanılan <xref:System.Data.DataView>, ve filtre temelini oluşturur.  
  
 İfade tabanlı filtreler daha basit dize tabanlı filtreler daha güçlü ve karmaşık filtreleme sağlar. Dize ve ifade tabanlı filtreler karşılıklı olarak birbirini dışlar. Zaman dize tabanlı <xref:System.Data.DataView.RowFilter%2A> sonra ayarlanmış bir <xref:System.Data.DataView> sorgudan çıkarılan göre filtre temizlendiğinde ifade bir sorgudan oluşturulur.  
  
> [!NOTE]
>  Çoğu durumda, filtreleme için kullanılan ifadeler yan etkileri olmamalıdır ve belirleyici olmalıdır. Ayrıca, ifadeleri herhangi içermemelidir filtreleme işlemleri olabileceğinden yürütmeleri kümesi sayısına bağlıdır mantığı yürütülen tüm sayısı.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte, 2. ve 6'değerinden büyük bir sayı siparişleri satış siparişi ayrıntısını tabloyu sorgular; oluşturur bir <xref:System.Data.DataView> Bu sorgudan; ve bağlar <xref:System.Data.DataView> için bir <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> 6 Haziran 2001'den sonra yerleştirilen siparişler sorgusundan:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Örnek  
 Filtreleme, ayrıca sıralama ile birleştirilebilir. Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> kişiler için bir sorgunun ayarlanmış son adı Başlat "S" ile ve Soyadı, ardından ad tarafından sıralanır:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, Soyadı, "Zhu için" benzer kişiler bulmak için SoundEx algoritması kullanır. SoundEx algoritması SoundEx yöntemine uygulanmıştır.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 İngilizce, başlangıçta ABD geliştirilmiş belirgin olarak adları sesi tarafından dizin oluşturma için kullanılan bir ses algoritması SoundEx olduğu Sayım kuruluşu. SoundEx yöntemi üç sayı tarafından izlenen bir İngilizce harfin oluşan bir ad dört karakter kodunu döndürür. Adının ilk harfi harfi olduğu ve kalan ünsüzler adında sayıları kodlayın. Benzer görünen adları aynı SoundEx kod paylaşın. Önceki örnekte SoundEx yönteminde kullanılan SoundEx uygulama aşağıda gösterilmiştir:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>RowFilter özelliğini kullanma  
 Var olan dize tabanlı filtreleme işlevselliğini <xref:System.Data.DataView> çalışmaya devam ettiğinden [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bağlamı. Dize tabanlı hakkında daha fazla bilgi için <xref:System.Data.DataView.RowFilter%2A> filtreleme, bkz: [sıralama ve filtreleme veri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> kişi tablosunu ve ardından ayarlar <xref:System.Data.DataView.RowFilter%2A> özelliği kişinin soyadı "Zhu" olduğu satırları döndürür:  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Sonra bir <xref:System.Data.DataView> öğesinden oluşturulan bir <xref:System.Data.DataTable> veya [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanabileceğiniz sorgu <xref:System.Data.DataView.RowFilter%2A> satır kümelerine belirtmek için özellik sütun değerlerine bağlı. Dize ve ifade tabanlı filtreler karşılıklı olarak birbirini dışlar. Ayarı <xref:System.Data.DataView.RowFilter%2A> özelliğini içinden gösterilen filtre ifadesi temizleyin [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu ve filtre ifadesi sıfırlanamıyor.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Şirket veriler için karşılıklı verilerin bir alt kümesini, dinamik bir görünüm, kullandığınız sağlayan belirli bir sorgunun sonuçlarını döndürmek isterseniz <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView>, ayar yerine <xref:System.Data.DataView.RowFilter%2A> özelliği. <xref:System.Data.DataView.RowFilter%2A> Özelliği en iyi şekilde kullanılır verilere bağlı uygulamada nereye bağlantılı denetim filtrelenmiş sonuçları görüntüler. Ayarı <xref:System.Data.DataView.RowFilter%2A> özelliği yükü uygulamanıza ekleme ve performansı azaltarak veri dizini oluşturur. <xref:System.Data.DataView.Find%2A> Ve <xref:System.Data.DataView.FindRows%2A> yöntemlerini yeniden oluşturulması için dizini gerek kalmadan geçerli dizini kullanın. Çağırmak için kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yalnızca bir kez daha sonra mevcut kullanmalısınız <xref:System.Data.DataView>. Çağırmak için kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez, yeni bir oluşturmanız gerekir <xref:System.Data.DataView> üzerinde arama yapın ve ardından çağırmak için istediğiniz sütunu dizini yeniden <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemleri. Hakkında daha fazla bilgi için <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemlerini [satırları bulma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md) ve [DataView performansı](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Filtre temizleniyor  
 Filtre bir <xref:System.Data.DataView> filtreleme kullanarak ayarlandıktan sonra temizlenebilir <xref:System.Data.DataView.RowFilter%2A> özelliği. Filtre bir <xref:System.Data.DataView> iki farklı yolla silinebilir:  
  
- Ayarlama <xref:System.Data.DataView.RowFilter%2A> özelliğini `null`.  
  
- Ayarlama <xref:System.Data.DataView.RowFilter%2A> boş bir dize özelliği.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> sorgudan ve ardından filtre ayarlayarak temizler <xref:System.Data.DataView.RowFilter%2A> özelliğini `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> tablodan ayarlar <xref:System.Data.DataView.RowFilter%2A> özelliği ve ardından filtre ayarlayarak temizler <xref:System.Data.DataView.RowFilter%2A> boş bir dize özelliğini:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [DataView ile Sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)

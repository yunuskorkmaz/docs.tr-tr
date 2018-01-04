---
title: DataView (LINQ-DataSet) ile filtreleme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d578c36500af6f388e63ad921a4dbb8acac225f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="filtering-with-dataview-linq-to-dataset"></a>DataView (LINQ-DataSet) ile filtreleme
Belirli bir ölçüte kullanarak veri filtreleme ve bir kullanıcı Arabirimi denetim üzerinden bir istemciye veri sunmak olanağı veri bağlama önemli bir yönüdür. <xref:System.Data.DataView>verileri filtreleme ve toplantı belirli filtre ölçütlerini veri satır kümelerine dönmek için çeşitli yöntemler sağlar. Dize tabanlı yanı sıra filtreleme yetenekleri <xref:System.Data.DataView> kullanma olanağı da sağlar [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] ifadeleri filtre ölçütlerini için. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]ifadeler dize tabanlıdır filtreleme daha çok daha karmaşık ve güçlü filtreleme işlemleri için izin verin.  
  
 İki yolla kullanarak filtre veri için bir <xref:System.Data.DataView>:  
  
-   Oluşturma bir <xref:System.Data.DataView> gelen bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu ile bir Where yan tümcesi.  
  
-   Var olan, dize tabanlı filtreleme özelliklerini kullanmak <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a>Filtre bilgileri içeren bir sorgu DataView oluşturuluyor  
 A <xref:System.Data.DataView> nesnesi, gelen oluşturulabilir bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu. Bu sorgu içeriyorsa bir `Where` yan tümcesi <xref:System.Data.DataView> Sorgu filtreleme bilgilerle oluşturulur. İfade `Where` yan tümcesi, hangi veri satırların dahil edilecek belirlemek için kullanılır <xref:System.Data.DataView>, ve filtre temelini oluşturur.  
  
 İfade tabanlı filtreler daha güçlü ve karmaşık daha basit dize tabanlı filtreler filtreleme sağlar. Dize ve ifade tabanlı filtreler karşılıklı olarak birbirini dışlar. Olduğunda dize tabanlı <xref:System.Data.DataView.RowFilter%2A> sonra ayarlanmış bir <xref:System.Data.DataView> sorgudan çıkarımı yapılan göre filtre temizlendiğinde ifadesi bir sorgudan oluşturulur.  
  
> [!NOTE]
>  Çoğu durumda, filtre uygulamak için kullanılan ifadeleri yan etkileri olmamalıdır ve belirleyici olması gerekir. Ayrıca, ifadeleri herhangi içermemelidir filtreleme işlemleri olabilir çünkü yürütmeleri, kümesi sayısına bağlıdır mantığı yürütülen tüm sayısı.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek 2 değerinden 6'dan büyük ve bir miktar siparişleri için satış siparişi ayrıntısını tablosunu sorgular; oluşturur bir <xref:System.Data.DataView> Bu sorgudan; ve bağlar <xref:System.Data.DataView> için bir <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Data.DataView> siparişleri için sorgudan yerleştirilen 6 Haziran 2001'den sonra:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a>Örnek  
 Filtreleme, ayrıca sıralama ile birleştirilebilir. Aşağıdaki örnekte bir <xref:System.Data.DataView> kişiler için sorgudan özelliği adı Başlat "S" ile en son ve Soyadı, ardından ad tarafından sıralanır:  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek SoundEx algoritmasını Soyadı "Zhu" benzer kişiler bulmak için kullanır. SoundEx algoritması SoundEx yöntemine uygulanmıştır.  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx İngilizce, başlangıçta ABD ticaret geliştirilmiş belirgin olarak adları sesle, dizin oluşturma işlemi için kullanılan bir ses algoritmasıdır Census kuruluşu. SoundEx yöntemi bir İngilizce harfini üç numaralarına göre izleyen oluşan bir ad dört karakter kodunu döndürür. Harfi adının ilk harfi ve sayıları adında kalan ünsüzler kodlayın. Benzer görünen adları aynı SoundEx kodu paylaşır. Önceki örnekte SoundEx yönteminde kullanılan SoundEx uygulaması burada gösterilir:  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a>RowFilter özelliğini kullanma  
 Varolan dize tabanlı filtreleme işlevselliğini <xref:System.Data.DataView> çalışmaya devam ettiğinden [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bağlamı. Dize tabanlı hakkında daha fazla bilgi için <xref:System.Data.DataView.RowFilter%2A> filtreleme, bkz: [sıralama ve filtreleme verilerini](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Aşağıdaki örnekte bir <xref:System.Data.DataView> başvurun ve ardından ayarlar <xref:System.Data.DataView.RowFilter%2A> özelliği kişinin soyadını "Zhu" olduğu satırları döndürür:  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 Sonra bir <xref:System.Data.DataView> gelen oluşturulan bir <xref:System.Data.DataTable> veya [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanabileceğiniz sorgu <xref:System.Data.DataView.RowFilter%2A> satır kümelerine belirtmek üzere özelliğe dayalı sütun değerlerine göre. Dize ve ifade tabanlı filtreler karşılıklı olarak birbirini dışlar. Ayarı <xref:System.Data.DataView.RowFilter%2A> özelliğini gelen çıkarımı yapılan filtre ifadesi temizleyin [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu ve filtre ifadesi sıfırlanamıyor.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 Bir veri alt kümesini, dinamik bir görünümü, kullandığınız sağlanması karşılıklı için olarak veriler üzerinde belirli bir sorgu sonuçlarını döndürmek istiyorsanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView>, ayar yerine <xref:System.Data.DataView.RowFilter%2A> özelliği. <xref:System.Data.DataView.RowFilter%2A> Özelliği en iyi kullanılır verilere bağlı uygulamada burada bağlantılı denetim filtrelenen sonuçları görüntüler. Ayar <xref:System.Data.DataView.RowFilter%2A> özelliği veri yükü uygulamanıza ekleme ve performans azaltmak için dizini yeniden oluşturur. <xref:System.Data.DataView.Find%2A> Ve <xref:System.Data.DataView.FindRows%2A> yöntemleri yeniden oluşturulması için dizin gerek kalmadan geçerli dizini kullanın. Çağrı kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yalnızca bir kez daha sonra varolan kullanmanız gereken <xref:System.Data.DataView>. Çağrı kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez, yeni bir oluşturmalısınız <xref:System.Data.DataView> arayın ve ardından arama yapmak istediğiniz sütunu dizini yeniden oluşturmak için <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemleri. Hakkında daha fazla bilgi için <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemlerini görmek [bulma satırları](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md) ve [DataView performans](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
## <a name="clearing-the-filter"></a>Filtre temizleme  
 Üzerindeki filtre bir <xref:System.Data.DataView> filtreleme kullanarak ayarlandıktan sonra temizlenebilir <xref:System.Data.DataView.RowFilter%2A> özelliği. Üzerindeki filtre bir <xref:System.Data.DataView> iki farklı şekilde temizlenebilir:  
  
-   Ayarlama <xref:System.Data.DataView.RowFilter%2A> özelliğine `null`.  
  
-   Ayarlama <xref:System.Data.DataView.RowFilter%2A> boş bir dize özelliği.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Data.DataView> sorgudan ve ardından filtre ayarlayarak temizler <xref:System.Data.DataView.RowFilter%2A> özelliğine `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Data.DataView> tablodan ayarlar <xref:System.Data.DataView.RowFilter%2A> özelliği ve ardından filtre ayarlayarak temizler <xref:System.Data.DataView.RowFilter%2A> boş bir dize özelliği:  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [DataView ile Sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)

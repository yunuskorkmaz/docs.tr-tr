---
title: Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
ms.openlocfilehash: 44c985cef035e33e88ba246584efcb30fe0e9b97
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705564"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama
Sanal modda uygulamak için bir neden <xref:System.Windows.Forms.DataGridView> yalnızca gerekli verileri almak üzere denetimidir. Bu adlandırılır *tam zamanında veri yükleme*.  
  
 Örneğin, çok büyük bir uzak bir veritabanı tablosu ile çalışıyorsanız, görüntüleme için gerekli olan veriler alınıyor ve yalnızca kullanıcı görünüme yeni satırlar kaydırdığında ek veriler alınırken başlangıç gecikmeleri önlemek isteyebilirsiniz. Sınırlı bir veri depolamak için kullanılabilir bellek miktarı uygulamanızı çalıştıran istemci bilgisayarları varsa, veritabanından yeni değerler alınırken kullanılmayan verileri atmak isteyebilirsiniz.  
  
 Aşağıdaki bölümlerde nasıl kullanılacağını bir <xref:System.Windows.Forms.DataGridView> just-ın-time önbellek denetimi.  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Windows tam zamanında veri yükleme ile sanal modu uygulama Forms DataGridView denetiminde](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Formu  
 Aşağıdaki kod örneği, salt okunur içeren bir formu tanımlar <xref:System.Windows.Forms.DataGridView> ile etkileşime giren denetimi bir `Cache` nesnesi aracılığıyla bir <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olay işleyicisi. `Cache` Nesne yerel olarak depolanan değerler yönetir ve kullandığı bir `DataRetriever` Northwind örnek veritabanını Siparişler tablosundan değerleri almak için nesne. `DataRetriever` Uygulayan nesne `IDataPageRetriever` tarafından gerekli arabirim `Cache` sınıfı, aynı zamanda başlatmak için kullanılan <xref:System.Windows.Forms.DataGridView> satırları ve sütunları denetler.  
  
 `IDataPageRetriever`, `DataRetriever`, Ve `Cache` türleri, bu konunun ilerleyen bölümlerinde açıklanmıştır.  
  
> [!NOTE]
>  Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>IDataPageRetriever arabirimi  
 Aşağıdaki kod örneği tanımlar `IDataPageRetriever` tarafından uygulanan arabirimi `DataRetriever` sınıfı. Bu arabirimde bildirilen tek yöntemdir `SupplyPageOfData` yöntemi bir ilk satır dizini ve tek bir sayfada veri satırı sayısını gerektirir. Bu değerler tarafından uygulayan bir veri alt kümesini bir veri kaynağından almak için kullanılır.  
  
 A `Cache` nesnesi veri iki başlangıç sayfası yüklemek için bu arabirimi uygulaması oluşturma sırasında kullanır. Önbellek önbelleğe alınmamış bir değer gerektiğinde, bu sayfalardan birine atar ve değeri içeren yeni bir sayfa istekleri `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever sınıfı  
 Aşağıdaki kod örneği tanımlar `DataRetriever` sınıfını `IDataPageRetriever` veri sayfasını bir sunucudan almak için arabirim. `DataRetriever` Sınıfı sağlar `Columns` ve `RowCount` özellikleri, hangi <xref:System.Windows.Forms.DataGridView> denetimi kullanan boş bir satır için uygun sayıda eklenecek ve gerekli sütun oluşturmak için <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu. Boş satırlar ekleme, böylece tablosundaki tüm verileri içerir ancak denetim davranış göstereceği gereklidir. Başka bir deyişle, kaydırma çubuğunun kaydırma kutusunun boyutuna sahip olur ve kullanıcının tablodaki her satır erişmek mümkün olacaktır. Satırları tarafından doldurulur <xref:System.Windows.Forms.DataGridView.CellValueNeeded> görünüme yalnızca kaydırılan olduğunda olay işleyicisi.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Önbellek sınıfı  
 Aşağıdaki kod örneği tanımlar `Cache` yöneten iki sayfa veri ile doldurulan bir sınıf bir `IDataPageRetriever` uygulaması. `Cache` Sınıfı tanımlayan bir iç `DataPage` içeren yapısı bir <xref:System.Data.DataTable> değerleri tek bir önbellekte depolamak için sayfa ve satır dizinleri hesaplayan sayfanın üst ve alt sınırları temsil eder.  
  
 `Cache` Sınıfı, oluşturma zamanında iki sayfa veri yükler. Her <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olay isteklerini bir değer `Cache` nesneyi belirleyen değeri kullanılabilir ise, iki birini sayfaları ve, bu durumda, döndürür. Değer yerel olarak kullanılabilir değilse, `Cache` nesneyi belirleyen iki sayfalarını hangisinin en uzak şu anda görüntülenen satır ve ardından döndürür istenen değeri içeren yeni bir sayfa değiştirir.  
  
 Veri sayfası satır sayısı ekranda aynı anda görüntülenebilir satır sayısı ile aynı olduğu varsayılarak, bu modeli aracılığıyla tablosu sayfalama kullanıcıların verimli bir şekilde en son görüntülenen sayfasına dönün olanak tanır.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Dikkat edilecek diğer noktalar  
 Yukarıdaki kod örnekleri, tam zamanında veri yükleme, bir örnek verilmiştir. En yüksek verimlilik elde etmek kendi gereksinimlerinize kodunu değiştirmeniz gerekir. En azından, önbellekte verilerin sayfa başına satır sayısı için uygun değeri seçin gerekecektir. Bu değer yöntemlere geçirilen `Cache` Oluşturucusu. Sayfa başına satır sayısı az de aynı anda görüntülenen satır sayısından olmalıdır, <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 En iyi sonuçlar için performans testi ve sisteminizin ve kullanıcılarınızın gereksinimlerini belirlemek için kullanılabilirlik testi yürütmek gerekir. Önünde bulundurmanız gereken birkaç faktör, uygulamanız, kullanılan ağ bağlantısının kullanılabilir bant genişliğini ve kullanılan sunucu gecikme süresini çalıştıran istemci makineleri bellek miktarını içerir. Bazen bant genişliği ve gecikme süresi en yüksek kullanım belirlenmesi.  
  
 Uygulamanızı'nın kayma performansını artırmak için yerel olarak depolanan veri miktarı artırabilir. Ancak, başlangıç süresini kısaltmak için başlangıçta çok fazla veri yükleme olmadığını önlemesi gerekmektedir. Değiştirmek istediğiniz `Cache` , depolayabileceğiniz veri sayısını artırmak için sınıf. Daha fazla veri sayfalarını kullanarak kayan verimliliği artırabilir, ancak veri sayfasında, kullanılabilir bant genişliğini ve sunucu gecikme süresi bağlı olarak satır ideal sayısını belirlemek ihtiyacınız olacak. Daha küçük sayfalarıyla sunucusu daha sık erişilen, ancak istenen veri döndürülemiyor daha az zaman alır. Daha fazla bant genişliği daha sorun gecikme ise, büyük veri sayfaları kullanmak isteyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](implementing-virtual-mode-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde tam zamanında veri yükleme ile sanal modu uygulama](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)

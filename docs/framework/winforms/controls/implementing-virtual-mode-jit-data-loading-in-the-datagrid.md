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
ms.openlocfilehash: ad3ec7fb2e0012459bcf597ac9abee76c20b767e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama
Sanal mod uygulamak için bir sebep <xref:System.Windows.Forms.DataGridView> denetimidir yalnızca gerektiği gibi veri alınamadı. Bu adlı *tam zamanında veri yükleme*.  
  
 Örneğin, bir uzak veritabanı çok büyük bir tabloda ile çalışıyorsanız, görüntü için gerekli olan veri alma ve yalnızca kullanıcı görünüme yeni satırlar kaydırdığında ek veri alma başlangıç gecikmelerden kaçınmak isteyebilirsiniz. Uygulamanızı çalıştıran istemci bilgisayarlar sınırlı miktarda veri depolamak için kullanılabilir bellek varsa, yeni değerleri veritabanından alınırken kullanılmayan verileri atmak isteyebilirsiniz.  
  
 Aşağıdaki bölümlerde nasıl kullanılacağını bir <xref:System.Windows.Forms.DataGridView> denetimi yalnızca zaman önbellek ile.  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Windows Forms DataGridView denetimini Just-In-Time veri yükleme ile sanal modu uygulama](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Formu  
 Aşağıdaki kod örneğinde salt okunur içeren bir form tanımlar <xref:System.Windows.Forms.DataGridView> etkileşimde denetim bir `Cache` nesnesi aracılığıyla bir <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olay işleyicisi. `Cache` Nesne yerel olarak depolanmış değerlerini yönetir ve kullandığı bir `DataRetriever` örnek Northwind veritabanı Siparişler tablosundan değerleri almak için nesne. `DataRetriever` Uygulayan nesne `IDataPageRetriever` gerektirdiği arabirimi `Cache` sınıfı, ayrıca başlatmak için kullanılan <xref:System.Windows.Forms.DataGridView> kontrol satırları ve sütunları.  
  
 `IDataPageRetriever`, `DataRetriever`, Ve `Cache` türleri, bu konunun ilerleyen bölümlerinde açıklanmıştır.  
  
> [!NOTE]
>  Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>IDataPageRetriever arabirimi  
 Aşağıdaki kod örneğinde tanımlar `IDataPageRetriever` tarafından uygulanan arabirimi `DataRetriever` sınıfı. Bu arabirimde bildirilen tek yöntemdir `SupplyPageOfData` ilk satır dizini ve verilerin tek bir sayfayla satır sayısını gerektirir yöntemi. Bu değerleri tarafından uygulayan bir veri alt kümesini bir veri kaynağından veri almak için kullanılır.  
  
 A `Cache` nesnesi iki ilk sayfa veri yüklemek için bu arabirimi uygulaması oluşturma sırasında kullanır. Önbellek önbelleğe alınmamış bir değer gerekli olduğunda, bu sayfaları birini atar ve değerini içeren yeni bir sayfa istekleri `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever sınıfı  
 Aşağıdaki kod örneğinde tanımlar `DataRetriever` sınıfı, hangi uygulayan `IDataPageRetriever` bir sunucudan sayfa veri almak için arabirim. `DataRetriever` Sınıfı sağlar `Columns` ve `RowCount` özellikler, hangi <xref:System.Windows.Forms.DataGridView> ekleyeceğini gerekli sütunları oluşturun ve boş satırlar için uygun sayıda eklemek için <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu. Boş satır ekleme, böylece denetimi tablosundaki tüm verileri içerir ancak gibi davranacak gereklidir. Bunun anlamı kaydırma çubuğunun kaydırma kutusuna uygun boyuta sahip olur ve kullanıcı tablodaki herhangi bir satır erişebilir. Satırları tarafından doldurulur <xref:System.Windows.Forms.DataGridView.CellValueNeeded> görünüme yalnızca kaydırılan olduğunda olay işleyicisi.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Önbellek sınıfı  
 Aşağıdaki kod örneğinde tanımlar `Cache` iki sayfa aracılığıyla doldurulmuş veri yöneten sınıf bir `IDataPageRetriever` uygulaması. `Cache` Sınıfı tanımlayan bir iç `DataPage` içeren yapısı bir <xref:System.Data.DataTable> değerleri tek bir önbellekte depolamak için sayfa ve satır dizinler hesaplar sayfanın üst ve alt sınırlarını temsil eder.  
  
 `Cache` Sınıfı yapım aynı anda iki sayfa veri yükler. Her <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olay isteklerini bir değer `Cache` nesne belirleyen değeri kullanılabilir ise, iki birini sayfaları ve, varsa, döndürür. Değer yerel olarak kullanılabilir değilse `Cache` nesne belirler, iki sayfalarını en uzak şu anda görüntülenen satır ve sayfa sonra döndürür istenen değeri içeren yeni bir tane ile değiştirir.  
  
 Veri sayfası satır sayısı ekranda aynı anda görüntülenecek satırların sayısı ile aynı olduğu varsayılarak, bu model verimli bir şekilde en son görüntülenen sayfaya geri dönmek kullanıcıların tabloda disk belleği sağlar.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Ek hususlar  
 Yukarıdaki kod örnekleri, tam zamanında veri yükleme Tanıtımı sağlanır. En yüksek verimlilik elde etmek kendi gereksinimlerine göre kodu değiştirmeniz gerekir. En azından, önbellekte veri sayfa başına satır sayısı için uygun bir değer seçin gerekecektir. Bu değer içine geçirilir `Cache` Oluşturucusu. Sayfa başına satır sayısı az aynı anda görüntülenen satır sayısından olmalıdır, <xref:System.Windows.Forms.DataGridView> denetim.  
  
 En iyi sonuçlar için performans testi ve kullanılabilirlik sisteminizi ve kullanıcılarınızın gereksinimlerini belirlemek için sınama gerçekleştir gerekecektir. Dikkate gerekecek birkaç etkene bellek miktarı, uygulamanızın, kullanılan ağ bağlantısının kullanılabilir bant genişliğini ve kullanılan Server gecikme çalıştıran istemci makinelerinizde içerir. Gecikme süresi ve bant genişliği bazen en yüksek kullanım belirlenmesi.  
  
 Kaydırma, uygulamanızın performansını artırmak için yerel olarak depolanan veri miktarını artırabilirsiniz. Ancak, başlangıç zamanını geliştirmek için çok fazla veri başlangıçta yüklenirken olmadığını kaçının gerekir. Değiştirmek istediğiniz `Cache` , onu saklayabilir veri sayfaların sayısını artırmak için sınıf. Daha fazla veri sayfalarını kullanarak kaydırma verimliliği artırabilir, ancak ideal bir veri sayfasında, kullanılabilir bant genişliğini ve sunucu gecikme süresi bağlı olarak satır sayısı belirlemeniz gerekir. Daha küçük sayfaları ile sunucunun daha sık erişilen, ancak istenen veri döndürülemiyor daha az zaman alır. Gecikme süresi daha fazla bant genişliği daha ilgili bir sorun varsa, daha büyük veri sayfaları kullanmak isteyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Windows Forms DataGridView Denetiminde Performans Ayarlaması](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Sanal Mod](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)

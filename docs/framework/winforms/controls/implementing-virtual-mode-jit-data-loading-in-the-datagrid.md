---
title: DataGridView denetiminde tam zamanında veri yükleme ile sanal modu uygulama
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
ms.openlocfilehash: 85c6877a9fc6a92752eb039da9d36e34811f8b77
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745061"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama
<xref:System.Windows.Forms.DataGridView> denetiminde sanal mod uygulamak için bir neden, verileri yalnızca gerektiğinde almak. Bu, *tam zamanında veri yükleme*olarak adlandırılır.  
  
 Örneğin, uzak bir veritabanında çok büyük bir tabloyla çalışıyorsanız, yalnızca Kullanıcı yeni satırları görünüme kaydırdığında yalnızca görüntülemek için gerekli olan verileri alarak ve ek verileri almak için başlatma gecikmelerini önlemek isteyebilirsiniz. Uygulamanızı çalıştıran istemci bilgisayarların, verileri depolamak için sınırlı miktarda belleği varsa, veritabanından yeni değerler alırken kullanılmayan verileri de atmak isteyebilirsiniz.  
  
 Aşağıdaki bölümlerde, tam zamanında önbelleğiyle <xref:System.Windows.Forms.DataGridView> denetiminin nasıl kullanılacağı açıklanır.  
  
 Bu konudaki kodu tek bir liste olarak kopyalamak için, bkz. [nasıl yapılır: Windows Forms DataGridView denetiminde tam zamanında veri yükleme Ile sanal modu uygulama](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Form  
 Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olay işleyicisi aracılığıyla `Cache` nesnesiyle etkileşim kuran salt okunurdur <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form tanımlar. `Cache` nesnesi, yerel olarak depolanan değerleri yönetir ve örnek Northwind veritabanının Orders tablosundan değerleri almak için bir `DataRetriever` nesnesi kullanır. `Cache` sınıfının gerektirdiği `IDataPageRetriever` arabirimini uygulayan `DataRetriever` nesnesi, <xref:System.Windows.Forms.DataGridView> denetim satırlarını ve sütunlarını başlatmak için de kullanılır.  
  
 `IDataPageRetriever`, `DataRetriever`ve `Cache` türleri bu konunun ilerleyen kısımlarında açıklanmıştır.  
  
> [!NOTE]
> Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Idatapageretriever arabirimi  
 Aşağıdaki kod örneği, `DataRetriever` sınıfı tarafından uygulanan `IDataPageRetriever` arabirimini tanımlar. Bu arabirimde bildirildiği tek yöntem, bir başlangıç satırı dizini ve tek bir veri sayfasındaki satır sayısı için gereken `SupplyPageOfData` yöntemidir. Bu değerler, bir veri kaynağından verilerin bir alt kümesini almak için uygulayıcısı tarafından kullanılır.  
  
 `Cache` nesnesi, verilerin iki başlangıç sayfasını yüklemek için oluşturma sırasında bu arabirimin bir uygulamasını kullanır. Önbelleğe alınmamış bir değer gerekli olduğunda, önbellek bu sayfalardan birini atar ve `IDataPageRetriever`değeri içeren yeni bir sayfa ister.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever sınıfı  
 Aşağıdaki kod örneği, bir sunucudan veri sayfalarını almak için `IDataPageRetriever` arabirimini uygulayan `DataRetriever` sınıfını tanımlar. `DataRetriever` sınıfı ayrıca, <xref:System.Windows.Forms.DataGridView> denetiminin gereken sütunları oluşturmak ve uygun sayıda boş satırı <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonuna eklemek için kullandığı `Columns` ve `RowCount` özelliklerini de sağlar. Boş satırları eklemek, denetimin tablodaki tüm verileri içermekle birlikte davranmasını sağlamak için gereklidir. Bu, kaydırma çubuğundaki kaydırma kutusunun uygun boyutta olacağı ve kullanıcının tablodaki herhangi bir satıra erişebileceği anlamına gelir. Satırlar yalnızca görünüme kaydırıldığında <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olay işleyicisi tarafından doldurulur.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Cache sınıfı  
 Aşağıdaki kod örneği, bir `IDataPageRetriever` uygulamasıyla doldurulan iki sayfa verisini yöneten `Cache` sınıfını tanımlar. `Cache` sınıfı, değerleri tek bir önbellek sayfasında depolayan ve sayfanın üst ve alt sınırlarını temsil eden satır dizinlerini hesaplayan bir <xref:System.Data.DataTable> içeren bir iç `DataPage` yapısını tanımlar.  
  
 `Cache` sınıfı, oluşturma sırasında iki sayfa veri yükler. <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olay bir değer istediğinde, `Cache` nesnesi değerin iki sayfadan birinde kullanılabilir olup olmadığını belirler ve varsa onu döndürür. Değer yerel olarak kullanılabilir değilse, `Cache` nesnesi, iki sayfanın en son görüntülenen satırlardan hangisinin en çok olduğunu belirler ve daha sonra döndürdüğü istenen değeri içeren yeni bir tane ile sayfanın yerini alır.  
  
 Bir veri sayfasındaki satır sayısının aynı anda ekranda görüntülenebilen satır sayısıyla aynı olduğu varsayıldığında, bu model, kullanıcıların tablo üzerinde sayfalama sırasında son görüntülenen sayfaya etkin bir şekilde geri dönmesi için izin verir.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Ek konular  
 Önceki kod örnekleri, tam zamanında veri yükleme gösterimi olarak sağlanır. En yüksek verimliliği elde etmek için kendi gereksinimlerinize göre kodu değiştirmeniz gerekir. En azından, önbellekteki veri sayfası başına satır sayısı için uygun bir değer seçmeniz gerekir. Bu değer `Cache` oluşturucusuna geçirilir. Sayfa başına satır sayısı, <xref:System.Windows.Forms.DataGridView> denetialarınızın aynı anda görüntülenebilen satır sayısından az olmamalıdır.  
  
 En iyi sonuçlar için, sisteminizin ve kullanıcılarınızın gereksinimlerini belirleyebilmek için performans testi ve kullanılabilirlik testi yapmanız gerekir. Dikkate almanız gereken birkaç etken, uygulamanızı çalıştıran istemci makinelerdeki bellek miktarını, kullanılan ağ bağlantısının kullanılabilir bant genişliğini ve kullanılan sunucunun gecikmesini içerir. Bant genişliği ve gecikme süresi en yüksek kullanım saatlerinde belirtilmelidir.  
  
 Uygulamanızın kayan performansını geliştirmek için, yerel olarak depolanan veri miktarını artırabilirsiniz. Ancak, başlangıç süresini artırmak için başlangıçta çok fazla veri yüklemekten kaçınmanız gerekir. `Cache` sınıfını, depolayabileceği veri sayfalarının sayısını artırmak için değiştirmek isteyebilirsiniz. Daha fazla veri sayfası kullanılması, kaydırma verimliliğini iyileştirebilirler, ancak kullanılabilir bant genişliğine ve sunucu gecikmesine bağlı olarak bir veri sayfasında ideal satır sayısını belirlemeniz gerekir. Daha küçük sayfalarla, sunucuya daha sık erişilir, ancak istenen verilerin döndürülmesi daha az zaman alır. Gecikme süresi bant genişliğinden daha fazlaysa, daha büyük veri sayfalarını kullanmak isteyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma](implementing-virtual-mode-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)

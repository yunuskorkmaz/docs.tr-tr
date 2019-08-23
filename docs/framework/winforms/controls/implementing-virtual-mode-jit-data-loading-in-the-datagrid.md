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
ms.openlocfilehash: fa40f1657a433f5f4ade3de25648ca04c37dfa67
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962596"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama
<xref:System.Windows.Forms.DataGridView> Denetimde sanal mod uygulamak için bir neden, verileri yalnızca gerektiğinde almak olur. Bu, *tam zamanında veri yükleme*olarak adlandırılır.  
  
 Örneğin, uzak bir veritabanında çok büyük bir tabloyla çalışıyorsanız, yalnızca Kullanıcı yeni satırları görünüme kaydırdığında yalnızca görüntülemek için gerekli olan verileri alarak ve ek verileri almak için başlatma gecikmelerini önlemek isteyebilirsiniz. Uygulamanızı çalıştıran istemci bilgisayarların, verileri depolamak için sınırlı miktarda belleği varsa, veritabanından yeni değerler alırken kullanılmayan verileri de atmak isteyebilirsiniz.  
  
 Aşağıdaki bölümlerde, tam zamanında önbelleğe sahip bir <xref:System.Windows.Forms.DataGridView> denetimin nasıl kullanılacağı açıklanır.  
  
 Bu konudaki kodu tek bir liste olarak kopyalamak için bkz [. nasıl yapılır: Windows Forms DataGridView denetiminde](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)tam zamanında veri yükleme ile sanal modu uygulayın.  
  
## <a name="the-form"></a>Form  
 Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olay işleyicisi aracılığıyla bir `Cache` nesneyle etkileşen salt okunurdur bir denetim içeren bir form tanımlar. Nesnesi, yerel olarak depolanan değerleri yönetir ve örnek Northwind `DataRetriever` veritabanının Orders tablosundan değerleri almak için bir nesnesi kullanır. `Cache` Sınıfının gerektirdiği `IDataPageRetriever` arabirimi uygulayan `DataRetriever` nesne, Denetimsatırlarınıvesütunlarınıbaşlatmakiçindekullanılır.<xref:System.Windows.Forms.DataGridView> `Cache`  
  
 `IDataPageRetriever`, Vetürleri`Cache` bu konunun ilerleyen kısımlarında açıklanmıştır. `DataRetriever`  
  
> [!NOTE]
> Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Idatapageretriever arabirimi  
 Aşağıdaki kod örneği, `IDataPageRetriever` `DataRetriever` sınıfı tarafından uygulanan arabirimini tanımlar. Bu arabirimde `SupplyPageOfData` belirtilen tek yöntem, bir başlangıç satırı dizini ve tek bir veri sayfasında bulunan satır sayısı için olan yöntemdir. Bu değerler, bir veri kaynağından verilerin bir alt kümesini almak için uygulayıcısı tarafından kullanılır.  
  
 Bir `Cache` nesne, verilerin iki başlangıç sayfasını yüklemek için oluşturma sırasında bu arabirimin bir uygulamasını kullanır. Önbelleğe alınmamış bir değer gerekli olduğunda, önbellek bu sayfalardan birini atar ve öğesinden `IDataPageRetriever`değeri içeren yeni bir sayfa ister.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever sınıfı  
 Aşağıdaki kod örneği, bir sunucusundan `DataRetriever` veri sayfalarını almak için `IDataPageRetriever` arabirimini uygulayan sınıfını tanımlar. `RowCount` Sınıfıayrıca<xref:System.Windows.Forms.DataGridView.Rows%2A> , `Columns` denetimingereklisütunlarıoluşturmakveuygunsayıdaboşsatırıkoleksiyonaeklemekiçinkullandığıözelliklerdesağlar.<xref:System.Windows.Forms.DataGridView> `DataRetriever` Boş satırları eklemek, denetimin tablodaki tüm verileri içermekle birlikte davranmasını sağlamak için gereklidir. Bu, kaydırma çubuğundaki kaydırma kutusunun uygun boyutta olacağı ve kullanıcının tablodaki herhangi bir satıra erişebileceği anlamına gelir. Satırlar yalnızca görünüme kaydırıldığında <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olay işleyicisi tarafından doldurulur.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Cache sınıfı  
 Aşağıdaki kod örneği, bir `Cache` `IDataPageRetriever` uygulamayla doldurulmuş iki veri sayfasını yöneten sınıfını tanımlar. Sınıfı, değerleri tek bir `DataPage` önbellek sayfasında depolayan ve sayfanın <xref:System.Data.DataTable> üst ve alt sınırlarını temsil eden satır dizinlerini hesaplayan bir iç yapıyı tanımlar. `Cache`  
  
 Sınıfı `Cache` , oluşturma sırasında iki sayfa veri yükler. Olay bir değer istediğinde `Cache` , nesne değerin iki sayfadan birinde kullanılabilir olup olmadığını belirler ve varsa onu döndürür. <xref:System.Windows.Forms.DataGridView.CellValueNeeded> Değer yerel olarak kullanılamıyorsa, `Cache` nesne, iki sayfanın hangisinin görüntülenmekte olan satırlardan en çok olduğunu belirler ve daha sonra geri döndürülen istenen değeri içeren yeni bir tane ile sayfanın yerini alır.  
  
 Bir veri sayfasındaki satır sayısının aynı anda ekranda görüntülenebilen satır sayısıyla aynı olduğu varsayıldığında, bu model, kullanıcıların tablo üzerinde sayfalama sırasında son görüntülenen sayfaya etkin bir şekilde geri dönmesi için izin verir.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Ek konular  
 Önceki kod örnekleri, tam zamanında veri yükleme gösterimi olarak sağlanır. En yüksek verimliliği elde etmek için kendi gereksinimlerinize göre kodu değiştirmeniz gerekir. En azından, önbellekteki veri sayfası başına satır sayısı için uygun bir değer seçmeniz gerekir. Bu değer `Cache` oluşturucuya geçirilir. Sayfa başına satır sayısı, denetiinizdeki <xref:System.Windows.Forms.DataGridView> eşzamanlı olarak görüntülenebilen satır sayısından az olmamalıdır.  
  
 En iyi sonuçlar için, sisteminizin ve kullanıcılarınızın gereksinimlerini belirleyebilmek için performans testi ve kullanılabilirlik testi yapmanız gerekir. Dikkate almanız gereken birkaç etken, uygulamanızı çalıştıran istemci makinelerdeki bellek miktarını, kullanılan ağ bağlantısının kullanılabilir bant genişliğini ve kullanılan sunucunun gecikmesini içerir. Bant genişliği ve gecikme süresi en yüksek kullanım saatlerinde belirtilmelidir.  
  
 Uygulamanızın kayan performansını geliştirmek için, yerel olarak depolanan veri miktarını artırabilirsiniz. Ancak, başlangıç süresini artırmak için başlangıçta çok fazla veri yüklemekten kaçınmanız gerekir. Sınıfını, `Cache` depolayabileceği veri sayfalarının sayısını artırmak için değiştirmek isteyebilirsiniz. Daha fazla veri sayfası kullanılması, kaydırma verimliliğini iyileştirebilirler, ancak kullanılabilir bant genişliğine ve sunucu gecikmesine bağlı olarak bir veri sayfasında ideal satır sayısını belirlemeniz gerekir. Daha küçük sayfalarla, sunucuya daha sık erişilir, ancak istenen verilerin döndürülmesi daha az zaman alır. Gecikme süresi bant genişliğinden daha fazlaysa, daha büyük veri sayfalarını kullanmak isteyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](implementing-virtual-mode-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde tam zamanında veri yükleme ile sanal modu uygulama](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)

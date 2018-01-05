---
title: "Nasıl yapılır: Bir Alt Tabloda Seçilen Satırın Doğru Konumda Kalmasını Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c06692f19fe31bfcf2ae1f9778d847f412a007e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a>Nasıl yapılır: Bir Alt Tabloda Seçilen Satırın Doğru Konumda Kalmasını Sağlama
Görmemeleri ile Windows Forms veri bağlama çalışırken, verileri ne üst/alt adında veya ana/Ayrıntılar görünümü görüntülenir. Bu aynı kaynaktan veri iki denetimlerinde görüntülendiği bir veri bağlama senaryosu ifade eder. Bir denetim seçim değiştirme değiştirmek için ikinci denetiminde gösterilen veriler neden olur. Örneğin, ilk denetim müşteriler ve ilk denetimindeki seçili müşteri siparişleri listesini ilgili ikinci bir listesini içerebilir.  
  
 Alt tabloda seçilen olan satır tablonun ilk satırını sıfırlanmaz emin olmak için ek adımlar gerekebilir bir üst/alt görünüm verileri görüntülerken .NET Framework sürüm 2.0 ile başlatılıyor. Bunu yapmak için alt tablo konum önbelleğe ve üst tablo değişikliklerinden sonra sıfırlamak alması gerekir. Genellikle alt sıfırlama üst tablosu değişiklikleri satırının alanında ilk kez oluşur.  
  
### <a name="to-cache-the-current-child-position"></a>Geçerli alt konum önbelleğe almak için  
  
1.  Alt listesi konum depolamak için bir tamsayı değişken ve alt konum önbelleğe verilip depolamak için bir Boole değişken bildirin.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  İşleme <xref:System.Windows.Forms.CurrencyManager.ListChanged> bağlamanın için olay <xref:System.Windows.Forms.CurrencyManager> ve denetleme bir <xref:System.ComponentModel.ListChangedType> , <xref:System.ComponentModel.ListChangedType.Reset>.  
  
3.  Geçerli konumunu denetleyin <xref:System.Windows.Forms.CurrencyManager>. Listedeki ilk giriş büyük olup (genellikle 0), bir değişkene kaydedin.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  Üst listenin işlemek <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> üst para birimi Yöneticisi için olay. İşleyicisinde önbelleğe alma bir senaryo değildir belirtmek için Boolean değeri ayarlayın. Varsa <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> üst değişikliktir listesi konumu değiştirme ve madde değer değişikliği oluşur.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a>Alt konumu sıfırlama  
  
1.  İşleme <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> alt olay bağlamanın <xref:System.Windows.Forms.CurrencyManager>.  
  
2.  Önceki yordamda kaydedilmiş önbelleğe alınan konuma alt tablo konum sıfırlayın.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçerli konuma kaydetmek gösterilmiştir <xref:System.Windows.Forms.CurrencyManager>kullanımına bir alt tablo ve sıfırlama bir düzen üst tablo üzerinde tamamlandıktan sonra konumu. Bu örnek iki içeren <xref:System.Windows.Forms.DataGridView> denetimleri bağlı iki tablo için bir <xref:System.Data.DataSet> kullanarak bir <xref:System.Windows.Forms.BindingSource> bileşeni. İki tablo arasında bir ilişki kurulur ve ilişki eklenir <xref:System.Data.DataSet>. Alt tablo konumda başlangıçta tanıtım amacıyla üçüncü satır ayarlanır.  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 Kod örneği test etmek için aşağıdaki adımları gerçekleştirin:  
  
1.  Örneği çalıştırın.  
  
2.  Emin olun **önbellek ve konumlandırmak sıfırlama** onay kutusu seçilidir.  
  
3.  Tıklatın **Temizle üst alan** üst tablo alanına bir değişikliğe neden düğmesi. Alt tabloda seçilen satırın değişmeyen dikkat edin.  
  
4.  Kapatın ve örnek yeniden çalıştırın. Sıfırlama davranışı yalnızca üst sıradaki ilk değişiklik meydana gelme çünkü bunu yapmanız gerekir.  
  
5.  Clear **önbellek ve konumlandırmak sıfırlama** onay kutusu.  
  
6.  Tıklatın **Temizle üst alan** düğmesi. Alt tabloda seçilen satırın ilk satırın değiştiğine dikkat edin.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing, System.Windows.Forms ve System.XML derlemelerine başvurular.  
  
 Bu örnek için komut satırından derleme hakkında bilgi için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı yapı ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Aynı Veri Kaynağına Bağlanan Birden Çok Denetimin Eşitlenmiş Kalmasını Sağlama](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [BindingSource Bileşeni](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Veri Bağlama ve Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)

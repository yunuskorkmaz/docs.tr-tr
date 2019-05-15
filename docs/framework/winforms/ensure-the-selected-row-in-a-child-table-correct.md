---
title: 'Nasıl yapılır: Bir Alt Tabloda Seçilen Satırın Doğru Konumda Kalmasını Sağlama'
ms.date: 03/30/2017
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
ms.openlocfilehash: 1047958a5600d8e6ee0ba461305e09395151ab14
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592280"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a>Nasıl yapılır: Bir Alt Tabloda Seçilen Satırın Doğru Konumda Kalmasını Sağlama
Aktardığınızda genellikle, Windows Forms veri bağlama ile çalışırken, verilerin ne üst/alt adlı veya ana/Ayrıntılar görünümü görüntülenir. Bu iki denetimlerinde aynı kaynaktan verilerin görüntülendiği bir veri bağlama senaryosu ifade eder. Bir denetim seçimini değiştirmeden değiştirmek için ikinci denetimde görüntülenen veri neden olur. Örneğin, ilk denetim müşteriler ve siparişler listesi ilk denetiminde ise seçili müşterilerle ilgili ikinci bir listesini içerebilir.  
  
 Alt tabloda seçilen olan satır tablonun ilk satırına sıfırlanmaz emin olmak için ek adımlar gerekebilir üst/alt görünüm verileri görüntülerken .NET Framework sürüm 2.0 ile başlatılıyor. Bunu yapmak için önbelleğe alma alt tablo konum ve üst tablo değiştikten sonra sıfırlamak alması gerekir. Genellikle alt sıfırlama bir alanda bir üst tablosu değişiklikleri satırının ilk kez gerçekleşir.  
  
### <a name="to-cache-the-current-child-position"></a>Geçerli alt konum önbelleğe almak için  
  
1. Bağımlı liste konumu depolamak için bir tam sayı değişkeni ve alt konum önbelleğe verilip verilmeyeceğini depolamak için bir Boolean değişkeni bildirir.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2. Tanıtıcı <xref:System.Windows.Forms.CurrencyManager.ListChanged> bağlama için olay <xref:System.Windows.Forms.CurrencyManager> ve denetlemek için bir <xref:System.ComponentModel.ListChangedType> , <xref:System.ComponentModel.ListChangedType.Reset>.  
  
3. Geçerli konumunu denetleyin <xref:System.Windows.Forms.CurrencyManager>. Listedeki ilk girdi'dan büyük olup olmadığı (genellikle 0), bir değişkene kaydedin.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4. Üst listenin işlemek <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> ana para birimi Yöneticisi için olay. İşleyicisinde bir önbelleğe alma bir senaryo değildir belirtmek için Boolean değeri ayarlayın. Varsa <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> üst değişikliktir liste konumu değiştirme ve öğe değeri değişikliği oluşur.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a>Alt konumu sıfırlama  
  
1. Tanıtıcı <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> alt için olay bağlamanın <xref:System.Windows.Forms.CurrencyManager>.  
  
2. Önceki yordamda kaydedilen önbelleğe alınmış konumuna alt tablo konum sıfırlayın.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçerli konum kaydetmek gösterilmiştir <xref:System.Windows.Forms.CurrencyManager>sunulabilen bir alt tabloda ve sıfırlama üst tablosunda bir düzenleme tamamlandıktan sonra konumu. Bu örnek iki tane <xref:System.Windows.Forms.DataGridView> iki tablo ilişkili bir <xref:System.Data.DataSet> kullanarak bir <xref:System.Windows.Forms.BindingSource> bileşeni. İki tablo arasında bir ilişki kurulur ve ilişki eklendiğinden <xref:System.Data.DataSet>. Tanıtım amacıyla üçüncü satır alt tablo konumu başlangıçta ayarlanır.  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 Örnek kodu test etmek için aşağıdaki adımları gerçekleştirin:  
  
1. Örneği çalıştırın.  
  
2. Emin **önbellek ve konumlandırma sıfırlama** onay kutusu seçilidir.  
  
3. Tıklayın **Temizle üst alan** üst tablo bir alanda bir değişiklik neden düğme. Alt tabloda seçilen satırın değişmez dikkat edin.  
  
4. Kapatın ve örneği tekrar çalıştırın. Yalnızca üst satırdaki ilk değişiklik üzerinde sıfırlama davranışı oluştuğu için bunu yapmak gerekir.  
  
5. NET **önbellek ve konumlandırma sıfırlama** onay kutusu.  
  
6. Tıklayın **Temizle üst alan** düğmesi. Alt tabloda seçilen satırın ilk satırın değiştiğine dikkat edin.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Data System.Drawing, System.Windows.Forms ve System.XML derlemesine ilişkin başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Birden çok denetimin eşitlenmiş kalmasını aynı veri kaynağına bağlama](multiple-controls-bound-to-data-source-synchronized.md)
- [BindingSource Bileşeni](./controls/bindingsource-component.md)
- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)

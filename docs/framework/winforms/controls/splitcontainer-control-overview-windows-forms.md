---
title: SplitContainer Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 81898e09ff513043b205cde13378ae24ee755226
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45583284"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SplitContainer> denetim düşünülebilir bileşik; taşınabilir bir çubukla ayırarak iki bölme. Çubuğu üzerine fare işaretçisi olduğunda, işaretçi şekli çubuğu taşınabilir olduğunu göstermek için değiştirir.  
  
> [!IMPORTANT]
>  İçinde **araç kutusu**, <xref:System.Windows.Forms.SplitContainer> denetim değiştirir <xref:System.Windows.Forms.Splitter> Visual Studio'nun önceki sürümünde var olan denetim. <xref:System.Windows.Forms.SplitContainer> Denetimidir üzerinden çok tercih edilen <xref:System.Windows.Forms.Splitter> denetimi. <xref:System.Windows.Forms.Splitter> Sınıfı dahil hala [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] var olan uygulamalarla uyumluluk için kullanmanızı önemle öneririz, ancak <xref:System.Windows.Forms.SplitContainer> denetimi yeni projeler için.  
  
 İle <xref:System.Windows.Forms.SplitContainer> denetim, karmaşık kullanıcı arabirimleri oluşturabilirsiniz; genellikle, hangi nesneler diğer panelinde gösterilir bir bölmede bir seçim belirler. Bu düzenleme, görüntüleme ve gözatma bilgilerinin oldukça etkilidir. İki panel sağlar sahip alanlarda bilgi toplamak ve çubuğuna ya da "ayırıcı," paneller yeniden boyutlandırmak kullanıcılar için kolay kılar.  
  
 Birden fazla <xref:System.Windows.Forms.SplitContainer> denetimi ayrıca iç içe geçirilemez, ikinci <xref:System.Windows.Forms.SplitContainer> denetim yönelik yatay panel üst ve alt oluşturmak için.  
  
 Unutmayın, <xref:System.Windows.Forms.SplitContainer> denetimi varsayılan klavye tarafından erişilemeyen; kullanıcıların Bölümlendirici taşımak için ok tuşlarını basabilirsiniz <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği `false`.  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Özelliği <xref:System.Windows.Forms.SplitContainer> denetimi Bölümlendiricinin, Denetim'ın yönü belirler. Bu nedenle, bu özelliği ayarlandığında <xref:System.Windows.Forms.Orientation.Vertical>, bölümlendirici üstten sol ve sağ bölmeleri oluşturma altına çalıştırır.  
  
 Ayrıca, dikkat, değerini <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> özellik değerini bağlı olarak değişir <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliği. Daha fazla bilgi için <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> özelliği.  
  
 Boyutu ve taşıma işlemini de kısıtlayabilirsiniz <xref:System.Windows.Forms.SplitContainer> denetimi. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Özellik, hangi panele sonra aynı boyutta kalacağını belirler <xref:System.Windows.Forms.SplitContainer> denetim değişirse ve <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği, bölme klavye veya fare tarafından taşınabilir olup olmadığını belirler.  
  
> [!NOTE]
>  Bile <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği `true`, bölümlendirici hala programlı olarak; Örneğin, kullanarak taşınabilir <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> özelliği.  
  
 Son olarak, her panelinin <xref:System.Windows.Forms.SplitContainer> denetim bireysel boyutunu belirlemek için özelliklere sahiptir.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Yaygın olarak kullanılan özellikleri, yöntemleri ve olayları  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Özelliği|Hangi panele aynı kalacak belirler sonra Boyut <xref:System.Windows.Forms.SplitContainer> denetimi yeniden boyutlandırılır.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Özelliği|Ayırıcı klavye veya fare ile taşınıp taşınamayacağını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> Özelliği|Bölümlendirici yatay veya dikey olarak düzenlenmiş, belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Özelliği|Taşınabilir ayırıcıyı için sol veya üst kenarından piksel cinsinden uzaklığı belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Özelliği|Bölümlendirici kullanıcı tarafından taşınabilir piksel cinsinden en düşük bir uzaklık belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> Özelliği|Ayırıcının piksel cinsinden kalınlığı belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> Olay|Bölümlendirici taşıma olduğunda gerçekleşir.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> Olay|Bölümlendirici taşıdığınızda gerçekleşir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer Denetimi](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [SplitContainer denetimi örneği](https://msdn.microsoft.com/library/9015fad0-7108-4d85-a83a-a72d038c4f65)

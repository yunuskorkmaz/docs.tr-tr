---
title: SplitContainer Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 76299d9bbd2b3eac4e765dfacf579c9979721fff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963204"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SplitContainer> denetimi bileşik olarak düşünülebilir; taşınabilir bir çubukla ayrılmış iki paneldir. Fare işaretçisi çubuğun üzerindeyken, işaretçiyi çubuğun taşınabilir olduğunu göstermek için şeklini değiştirir.  
  
> [!IMPORTANT]
> **Araç kutusunda** <xref:System.Windows.Forms.SplitContainer> denetim, Visual Studio 'nun <xref:System.Windows.Forms.Splitter> önceki sürümünde bulunan denetimin yerini almıştır. Denetim, denetimin <xref:System.Windows.Forms.Splitter> üzerinde çok tercih edilir. <xref:System.Windows.Forms.SplitContainer> Sınıfı, var olan uygulamalarla uyumluluk için .NET Framework dahil edilmiştir, ancak yeni projeler için <xref:System.Windows.Forms.SplitContainer> denetimi kullanmanızı kesinlikle öneririz. <xref:System.Windows.Forms.Splitter>  
  
 <xref:System.Windows.Forms.SplitContainer> Denetimle, karmaşık kullanıcı arabirimleri oluşturabilirsiniz; genellikle, bir panelde seçim diğer panelde hangi nesnelerin gösterileceğini belirler. Bu düzenleme bilgileri görüntülemek ve göz atmak için oldukça etkilidir. İki panel olması, alanlarda bilgi toplamanıza olanak sağlar ve çubuk veya "Bölümlendirici", kullanıcıların panoları yeniden boyutlandırmasını kolaylaştırır.  
  
 <xref:System.Windows.Forms.SplitContainer> İkinci<xref:System.Windows.Forms.SplitContainer> Denetim yatay olarak, üst ve alt panel oluşturmak için aynı zamanda birden fazla denetim de iç içe olabilir.  
  
 <xref:System.Windows.Forms.SplitContainer> Denetimin varsayılan olarak klavyeden erişilebilir olduğunu unutmayın; kullanıcılar, <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özellik olarak `false`ayarlandıysa ayırıcıyı taşımak için ok tuşlarına basabilir.  
  
 <xref:System.Windows.Forms.SplitContainer> Denetimin özelliği, denetimin kendisinin değil, ayırıcının yönünü belirler. <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Bu nedenle, bu özellik olarak <xref:System.Windows.Forms.Orientation.Vertical>ayarlandığında, Bölümlendirici yukarıdan aşağıya doğru çalışır ve sol ve sağ panolar oluşturur.  
  
 Ayrıca, <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> özelliğin değerinin <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliğin değerine göre değiştiğini unutmayın. Daha fazla bilgi için bkz <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> . özellik.  
  
 Ayrıca, <xref:System.Windows.Forms.SplitContainer> denetimin boyutunu ve hareketini de kısıtlayabilirsiniz. Özelliği, denetim yeniden boyutlandırılırken hangi panelin aynı boyutta kalacağınıbelirlervebuözellik,ayırıcınınklavyeveyafaretarafındantaşınabilirolupolmadığınıbelirler.<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> <xref:System.Windows.Forms.SplitContainer> <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>  
  
> [!NOTE]
> Özelliği olarak `true`ayarlanmış olsa bile, Bölümlendirici yine de program aracılığıyla taşınabilir veya <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Örneğin, özelliğini kullanarak. <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>  
  
 Son olarak, <xref:System.Windows.Forms.SplitContainer> denetimin her bir panelinin kendine özgü boyutunu belirlemesi için özellikleri vardır.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Yaygın olarak kullanılan özellikler, Yöntemler ve olaylar  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>özelliði|<xref:System.Windows.Forms.SplitContainer> Denetim yeniden boyutlandırılırken hangi panelin aynı boyutta kalacağını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>özelliði|Bölümlendiricinin klavye veya fareyle taşınıp taşınamayacağını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A>özelliði|Bölümlendiricinin dikey veya yatay olarak düzenlenmesini belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>özelliði|Sol veya üst kenardan taşınabilir ayırıcı çubuğuna piksel cinsinden mesafeyi belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>özelliði|Ayırıcının Kullanıcı tarafından taşınabileceği minimum mesafeyi piksel cinsinden belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>özelliði|Ayırıcının piksel cinsinden kalınlığını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving>olay|Bölümlendirici taşınırken gerçekleşir.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved>olay|Ayırıcı taşındığında gerçekleşir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer Denetimi](splitcontainer-control-windows-forms.md)
- [SplitContainer denetim örneği](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))

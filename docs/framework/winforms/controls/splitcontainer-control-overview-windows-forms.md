---
title: SplitContainer Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 5cb5240ed4ebe3e27c20844681068711c222e9a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742915"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SplitContainer> denetimi bileşik olarak düşünülebilir; taşınabilir bir çubukla ayrılmış iki paneldir. Fare işaretçisi çubuğun üzerindeyken, işaretçiyi çubuğun taşınabilir olduğunu göstermek için şeklini değiştirir.  
  
> [!IMPORTANT]
> **Araç kutusunda**<xref:System.Windows.Forms.SplitContainer> Control, Visual Studio 'nun önceki sürümünde bulunan <xref:System.Windows.Forms.Splitter> denetimini değiştirir. <xref:System.Windows.Forms.SplitContainer> denetimi <xref:System.Windows.Forms.Splitter> denetimi üzerinde çok tercih edilir. <xref:System.Windows.Forms.Splitter> sınıfı, var olan uygulamalarla uyumluluk için yine de .NET Framework dahil edilmiştir, ancak yeni projeler için <xref:System.Windows.Forms.SplitContainer> denetimini kullanmanızı kesinlikle öneririz.  
  
 <xref:System.Windows.Forms.SplitContainer> denetimiyle, karmaşık kullanıcı arabirimleri oluşturabilirsiniz; Genellikle, bir panelde bulunan bir seçim diğer panelde hangi nesnelerin gösterileceğini belirler. Bu düzenleme bilgileri görüntülemek ve göz atmak için oldukça etkilidir. İki panel olması, alanlarda bilgi toplamanıza olanak sağlar ve çubuk veya "Bölümlendirici", kullanıcıların panoları yeniden boyutlandırmasını kolaylaştırır.  
  
 Birden fazla <xref:System.Windows.Forms.SplitContainer> denetimi aynı zamanda iç ve alt panolar oluşturmak için ikinci <xref:System.Windows.Forms.SplitContainer> denetimi yatay olarak yönelimli iç içe olabilir.  
  
 <xref:System.Windows.Forms.SplitContainer> denetimine varsayılan olarak klavyeden erişilebilen unutmayın; Kullanıcılar, <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği `false`olarak ayarlandıysa ayırıcıyı taşımak için ok tuşlarına basabilir.  
  
 <xref:System.Windows.Forms.SplitContainer> denetiminin <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliği, denetimin kendisinin değil, ayırıcının yönünü belirler. Bu nedenle, bu özellik <xref:System.Windows.Forms.Orientation.Vertical>olarak ayarlandığında, Bölümlendirici yukarıdan aşağıya doğru çalışır ve sol ve sağ panolar oluşturur.  
  
 Ayrıca, <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> özelliğinin değerinin <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliğinin değerine göre değiştiğini unutmayın. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> özelliği.  
  
 Ayrıca, <xref:System.Windows.Forms.SplitContainer> denetiminin boyutunu ve hareketini de kısıtlayabilirsiniz. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> özelliği, <xref:System.Windows.Forms.SplitContainer> denetimi yeniden boyutlandırılırken hangi panelin aynı boyutta kalacağını belirler ve <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği ayırıcının klavye veya fare tarafından taşınabilir olup olmadığını belirler.  
  
> [!NOTE]
> <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği `true`olarak ayarlanmış olsa bile, Bölümlendirici yine de programlı bir şekilde taşınabilir. Örneğin, <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> özelliğini kullanarak.  
  
 Son olarak, <xref:System.Windows.Forms.SplitContainer> denetiminin her bir paneli, tek boyutunun belirlenmesi için özelliklere sahiptir.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Yaygın olarak kullanılan özellikler, Yöntemler ve olaylar  
  
|Name|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> özelliği|<xref:System.Windows.Forms.SplitContainer> denetimi yeniden boyutlandırılırken hangi panelin aynı boyutta kalacağını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği|Bölümlendiricinin klavye veya fareyle taşınıp taşınamayacağını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliği|Bölümlendiricinin dikey veya yatay olarak düzenlenmesini belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> özelliği|Sol veya üst kenardan taşınabilir ayırıcı çubuğuna piksel cinsinden mesafeyi belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> özelliği|Ayırıcının Kullanıcı tarafından taşınabileceği minimum mesafeyi piksel cinsinden belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> özelliği|Ayırıcının piksel cinsinden kalınlığını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving> olayı|Bölümlendirici taşınırken gerçekleşir.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved> olayı|Ayırıcı taşındığında gerçekleşir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer Denetimi](splitcontainer-control-windows-forms.md)
- [SplitContainer denetim örneği](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))

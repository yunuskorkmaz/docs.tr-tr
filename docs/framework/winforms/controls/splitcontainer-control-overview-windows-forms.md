---
title: "SplitContainer Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SplitContainer
helpviewer_keywords: SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10f18c46c85ed840b6625d9ed754d1d036a80975
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="splitcontainer-control-overview-windows-forms"></a>SplitContainer Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SplitContainer> kontrol zorlayıcı bileşik olarak; iki bölme taşınabilir bir çubukla ayrılan değer. Fare işaretçisini çubuğu üzerine olduğunda çubuğu taşınabilir olduğunu göstermek için Şekil işaretçi.  
  
> [!IMPORTANT]
>  İçinde **araç**, <xref:System.Windows.Forms.SplitContainer> kontrol değiştirir <xref:System.Windows.Forms.Splitter> 'in önceki sürümlerini yoktu denetim [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. <xref:System.Windows.Forms.SplitContainer> Denetimidir üzerinden çok tercih edilen <xref:System.Windows.Forms.Splitter> denetim. <xref:System.Windows.Forms.Splitter> Sınıfı dahil hala [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] varolan uygulamalarla uyumluluk için ancak kullanmak için kesinlikle öneririz <xref:System.Windows.Forms.SplitContainer> yeni projeler için denetim.  
  
 İle <xref:System.Windows.Forms.SplitContainer> denetim, karmaşık kullanıcı arabirimleri oluşturabilirsiniz; bu genellikle, bir panelinde seçimi hangi nesneleri diğer panelinde gösterileceğini belirler. Bu düzenlemenin görüntüleme ve bilgi gözatma için çok etkili olur. İki paneller sağlar sahip alanlarda bilgi toplama ve çubuğu ya da "bölme," paneller yeniden boyutlandırmak kullanıcılar için kolaylaştırır.  
  
 Birden fazla <xref:System.Windows.Forms.SplitContainer> denetimi de iç içe geçirilemez, ikinci <xref:System.Windows.Forms.SplitContainer> denetim yönelik yatay, üst ve alt panelleri oluşturmak için.  
  
 Unutmayın, <xref:System.Windows.Forms.SplitContainer> denetim klavye varsayılan olarak erişilebilen; kullanıcıların Bölümlendirici taşımak için ok tuşlarını basabilirsiniz <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği ayarlanmış `false`.  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Özelliği <xref:System.Windows.Forms.SplitContainer> denetimi Bölümlendirici, Denetim, değil yönünü belirler. Bu nedenle, bu özellik ayarlandığında <xref:System.Windows.Forms.Orientation.Vertical>, bölümlendirici üstten sol ve sağ paneller oluşturma altına çalıştırır.  
  
 Ayrıca, unutmayın, değeri <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> özellik değeri bağlı olarak değişir <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliği. Daha fazla bilgi için bkz: <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> özelliği.  
  
 Boyut ve hareketini de kısıtlayabilirsiniz <xref:System.Windows.Forms.SplitContainer> denetim. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Özelliği belirler hangi panele sonra aynı boyutta kalacak <xref:System.Windows.Forms.SplitContainer> denetim yeniden boyutlandırılır ve <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği, bölümlendirici klavye veya fare tarafından taşınabilir olup olmadığını belirler.  
  
> [!NOTE]
>  Olsa bile <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> özelliği ayarlanmış `true`, bölümlendirici hala program aracılığıyla; Örneğin, kullanarak taşındığı <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> özelliği.  
  
 Son olarak, her panelinin <xref:System.Windows.Forms.SplitContainer> denetimi tek tek boyutunu belirlemek için özellikler vardır.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Yaygın olarak kullanılan özellikleri, yöntemleri ve olayları  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>özelliği|Hangi panele aynı kalacaksa belirler sonra Boyut <xref:System.Windows.Forms.SplitContainer> denetim yeniden boyutlandırılır.|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>özelliği|Bölümlendirici klavye veya fare taşınıp taşınamayacağını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.Orientation%2A>özelliği|Bölümlendirici dikey veya yatay olarak düzenlenmiş varsa belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>özelliği|Taşınabilir Bölümlendirici çubuğuna sol veya üst kenarından piksel cinsinden uzaklığı belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>özelliği|Bölümlendirici kullanıcı tarafından taşınabilmesi piksel cinsinden minimum uzaklığını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>özelliği|Ayırıcının piksel cinsinden kalınlığı belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoving>Olay|Bölümlendirici taşıma olduğunda oluşur.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterMoved>Olay|Bölümlendirici taşındı oluşur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer denetimi](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [SplitContainer denetimi örnek](http://msdn.microsoft.com/en-us/9015fad0-7108-4d85-a83a-a72d038c4f65)

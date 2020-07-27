---
title: DataGrid Denetimindeki Boyutlandırma Seçenekleri
description: Windows Presentation Foundation DataGrid denetimindeki ayrı satırları ve sütunları, içeriklerine veya belirli değerlere göre nasıl ayarlayabileceğinizi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 0f10e385cbf18a26989614363ca6cd9f92bc83ec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164738"
---
# <a name="sizing-options-in-the-datagrid-control"></a>DataGrid Denetimindeki Boyutlandırma Seçenekleri
Boyutların kendisini denetlemek için çeşitli seçenekler mevcuttur <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>İçindeki ve tek tek satırları ve sütunları, <xref:System.Windows.Controls.DataGrid> otomatik olarak içeriklerine veya belirli değerlere ayarlanabilir şekilde ayarlanabilir. Varsayılan olarak, <xref:System.Windows.Controls.DataGrid> içeriği boyutuna sığacak şekilde büyür ve küçülecektir.  
  
## <a name="sizing-the-datagrid"></a>DataGrid 'i boyutlandırma  
  
### <a name="cautions-when-using-automatic-sizing"></a>Otomatik boyutlandırma kullanırken dikkatli olun  
 Varsayılan olarak, <xref:System.Windows.FrameworkElement.Height%2A> öğesinin ve <xref:System.Windows.FrameworkElement.Width%2A> ÖZELLIKLERI <xref:System.Windows.Controls.DataGrid> <xref:System.Double.NaN?displayProperty=nameWithType> (XAML 'de "") olarak ayarlanır `Auto` ve bu, <xref:System.Windows.Controls.DataGrid> içeriğinin boyutuna ayarlanır.  
  
 Ya da gibi alt öğelerinin boyutunu kısıtlamayan bir kapsayıcının içine yerleştirildiğinde, <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.DataGrid> kapsayıcının görünür sınırlarının ötesine uzatıp, kaydırma çubukları gösterilmez. Bu koşulun kullanılabilirliği ve performans etkileri vardır.  
  
 Bir veri kümesine bağlandığında, ' <xref:System.Windows.FrameworkElement.Height%2A> nin <xref:System.Windows.Controls.DataGrid> kısıtlanmazsa, bağlantılı veri kümesindeki her bir veri öğesi için bir satır eklemeye devam eder. Bu, <xref:System.Windows.Controls.DataGrid> satır eklendikçe uygulamanızın görünür sınırlarının dışına büyümesine neden olabilir. , <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.FrameworkElement.Height%2A> Yeni satırlara uyum sağlayacak şekilde büyümeye devam ettiğinden, bu durumda kaydırma çubuklarını göstermez.  
  
 İçindeki her satır için bir nesne oluşturulur <xref:System.Windows.Controls.DataGrid> . Büyük bir veri kümesiyle çalışıyorsanız ve öğesinin <xref:System.Windows.Controls.DataGrid> kendisini otomatik olarak boyutlarına izin verirseniz, çok sayıda nesnenin oluşturulması uygulamanızın performansını etkileyebilir.  
  
 Büyük veri kümeleriyle çalışırken bu sorunlardan kaçınmak için, ' nin özel olarak ayarlamanız <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.DataGrid> veya ' ı kısıtlayan bir kapsayıcıya yerleştirmeniz önerilir <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.Grid> . Kısıtlanmış olduğunda, <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.DataGrid> yalnızca belirtilen ' ın içine sığacak satırları oluşturur <xref:System.Windows.FrameworkElement.Height%2A> ve yeni verileri göstermek için bu satırları gerektiği gibi geri dönüşüme sahip olur.  
  
### <a name="setting-the-datagrid-size"></a>DataGrid boyutunu ayarlama  
 <xref:System.Windows.Controls.DataGrid>Belirtilen sınırlar dahilinde otomatik olarak boyuta ayarlanabilir veya <xref:System.Windows.Controls.DataGrid> belirli bir boyuta ayarlanabilir. Aşağıdaki tabloda, boyutu denetlemek için ayarlanacak özellikler gösterilmektedir <xref:System.Windows.Controls.DataGrid> .  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|İçin belirli bir yükseklik ayarlar <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Yüksekliğinin üst sınırını ayarlar <xref:System.Windows.Controls.DataGrid> . , <xref:System.Windows.Controls.DataGrid> Bu yüksekliğe ulaşıncaya kadar dikey olarak büyüecektir.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Yüksekliğinin alt sınırını ayarlar <xref:System.Windows.Controls.DataGrid> . , <xref:System.Windows.Controls.DataGrid> Bu yüksekliğe ulaşıncaya kadar dikey olarak küçülecektir.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|İçin belirli bir genişlik ayarlar <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Genişliği için üst sınırı ayarlar <xref:System.Windows.Controls.DataGrid> . , <xref:System.Windows.Controls.DataGrid> Bu genişliğe ulaşana kadar yatay olarak büyüyecektir.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Genişliği için alt sınır ayarlar <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>Bu genişliğe ulaşıncaya kadar yatay olarak küçülecektir.|  
  
## <a name="sizing-rows-and-row-headers"></a>Satırları ve satır üst bilgilerini boyutlandırma  
  
### <a name="datagrid-rows"></a>DataGrid satırları  
 Varsayılan olarak, bir <xref:System.Windows.Controls.DataGrid> satırın <xref:System.Windows.FrameworkElement.Height%2A> özelliği <xref:System.Double.NaN?displayProperty=nameWithType> `Auto` xaml 'de ("") olarak ayarlanır ve satır yüksekliği içindekilerin boyutuna genişletilir. İçindeki tüm satırların yüksekliği, <xref:System.Windows.Controls.DataGrid> özelliği ayarlanarak belirtilebilir <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> . Kullanıcılar satır üst bilgisi bölücüleri sürükleyerek satır yüksekliğini değiştirebilir.  
  
### <a name="datagrid-row-headers"></a>DataGrid satır başlıkları  
 Satır üst bilgilerini göstermek için, <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> özelliğinin veya olarak ayarlanması gerekir <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType> . Varsayılan olarak, satır başlıkları görüntülenir ve otomatik olarak içeriğine uyacak şekilde boyutları vardır. Satır başlıklarına, özelliği ayarlanarak belirli bir genişlik verilebilir <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> .  
  
## <a name="sizing-columns-and-column-headers"></a>Sütunları ve sütun üstbilgilerini boyutlandırma  
  
### <a name="datagrid-columns"></a>DataGrid sütunları  
 , <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.DataGridLength> <xref:System.Windows.Controls.DataGridLengthUnitType> Mutlak veya otomatik boyutlandırma modlarını belirtmek için ve yapısının değerlerini kullanır.  
  
 Aşağıdaki tabloda yapı tarafından sunulan değerler gösterilmektedir <xref:System.Windows.Controls.DataGridLengthUnitType> .  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Varsayılan otomatik boyutlandırma modu <xref:System.Windows.Controls.DataGrid> sütunları hem hücrelerin hem de sütun üstbilgilerinin içeriğine göre boyutlandırır.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Hücre tabanlı otomatik boyutlandırma modu <xref:System.Windows.Controls.DataGrid> sütunları sütun başlıkları dahil değil, sütundaki hücrelerin içeriğine göre boyutlandırır.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Üst bilgi tabanlı otomatik boyutlandırma modu <xref:System.Windows.Controls.DataGrid> sütunları yalnızca sütun üstbilgilerinin içeriğine göre boyutlandırır.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Piksel tabanlı boyutlandırma modu, <xref:System.Windows.Controls.DataGrid> belirtilen sayısal değere göre sütunları boyutlandırır.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Yıldız boyutlandırma modu, kullanılabilir alanı ağırlıklı oranlar ile dağıtmak için kullanılır.<br /><br /> XAML 'de yıldız değerleri n * olarak ifade edilir; burada n, bir sayısal değeri temsil eder. 1 \* ile eşdeğerdir \* . Örneğin, bir içinde iki sütun <xref:System.Windows.Controls.DataGrid> genişliklerde \* ve 2 ' de varsa \* , ilk sütun kullanılabilir alanın bir kısmını alır ve ikinci sütun kullanılabilir alanın iki bölümünü alır.|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter>Sınıfı, verileri sayısal veya dize değerleri ve değerleri arasında dönüştürmek için kullanılabilir <xref:System.Windows.Controls.DataGridLength> .  
  
 Varsayılan olarak, <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> özelliği olarak ayarlanır <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A> ve <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> özelliği olarak ayarlanır <xref:System.Windows.Controls.DataGridLength.Auto%2A> . Boyutlandırma modu veya olarak ayarlandığında <xref:System.Windows.Controls.DataGridLength.Auto%2A> <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A> sütunlar, en geniş görünür içeriğinin genişliğine göre artar. Kaydırma sırasında, geçerli sütun boyutundan daha büyük olan içerik görünüme kaydırıldığında bu boyutlandırma modları sütunların genişlemesine neden olur. İçerik görünümden kaydırıldığında sütun daraltılamıyor.  
  
 İçindeki sütunlar <xref:System.Windows.Controls.DataGrid> aynı zamanda yalnızca belirtilen sınırlar dahilinde otomatik olarak boyut olarak ayarlanabilir veya sütunlar belirli bir boyuta ayarlanabilir. Aşağıdaki tabloda, sütun boyutlarını denetlemek için ayarlanılabilecek özellikler gösterilmektedir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|İçindeki tüm sütunlar için üst sınırı ayarlar <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Tek bir sütun için üst sınırı ayarlar. Geçersiz kılmalar <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType> .|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|İçindeki tüm sütunlar için alt sınır ayarlar <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Tek bir sütun için alt sınır ayarlar. Geçersiz kılmalar <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType> .|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|İçindeki tüm sütunlar için belirli bir genişlik ayarlar <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Tek bir sütun için belirli bir genişlik ayarlar. Geçersiz kılmalar <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> .|  
  
### <a name="datagrid-column-headers"></a>DataGrid sütun başlıkları  
 Varsayılan olarak, <xref:System.Windows.Controls.DataGrid> sütun başlıkları görüntülenir. Sütun üstbilgilerini gizlemek için, <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> özelliğinin veya olarak ayarlanması gerekir <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType> . Varsayılan olarak, sütun başlıkları görüntülendiğinde, içeriğine uyacak şekilde otomatik olarak boyutlarlar. Sütun başlıklarına, özelliği ayarlanarak belirli bir yükseklik verilebilir <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> .  
  
### <a name="resizing-with-the-mouse"></a>Fareyle yeniden boyutlandırma  
 Kullanıcılar <xref:System.Windows.Controls.DataGrid> satır veya sütun üst bilgisi bölücüleri sürükleyerek satırları ve sütunları yeniden boyutlandırabilir. <xref:System.Windows.Controls.DataGrid>Ayrıca satır veya sütun üst bilgisi bölücüyü çift tıklayarak satır ve sütunların otomatik olarak yeniden boyutlandırılmasını destekler. Bir kullanıcının belirli sütunları yeniden boyutlandırmasını engellemek için, <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> `false` her sütun için özelliğini olarak ayarlayın. Kullanıcıların tüm sütunları yeniden boyutlandırmasını engellemek için <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> özelliğini olarak ayarlayın `false` . Kullanıcıların tüm satırları yeniden boyutlandırmasını engellemek için <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> özelliğini olarak ayarlayın `false` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>

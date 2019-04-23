---
title: DataGrid Denetimindeki Boyutlandırma Seçenekleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 6d100fb17b1ee3e652985a637d333d9f65e20d36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769807"
---
# <a name="sizing-options-in-the-datagrid-control"></a>DataGrid Denetimindeki Boyutlandırma Seçenekleri
Denetim için çeşitli seçenekler kullanılabilir nasıl <xref:System.Windows.Controls.DataGrid> kendisini boyutları. <xref:System.Windows.Controls.DataGrid>Ve bireysel içindeki satırları ve sütunları <xref:System.Windows.Controls.DataGrid>, içerikleri için otomatik olarak boyutu ayarlanabilir veya belirli değerlere ayarlayın. Varsayılan olarak, <xref:System.Windows.Controls.DataGrid> büyütme ve içerikleri sığacak şekilde küçültmek.  
  
## <a name="sizing-the-datagrid"></a>DataGrid boyutlandırma  
  
### <a name="cautions-when-using-automatic-sizing"></a>Otomatik boyutlandırma kullanırken uyarılar  
 Varsayılan olarak, <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özelliklerini <xref:System.Windows.Controls.DataGrid> ayarlandığından <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" XAML içindeki) ve <xref:System.Windows.Controls.DataGrid> içeriğinin boyutunu ayarlar.  
  
 Alt öğeleri için boyutu gibi kısıtlamaz bir kapsayıcı içinde yerleştirildiğinde bir <xref:System.Windows.Controls.Canvas> veya <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.DataGrid> görünür kapsayıcı sınırlarının ötesine esnetir ve kaydırma çubukları gösterilmeyecek. Bu durum hem kullanılabilirliğini ve performansını etkilere sahiptir.  
  
 Ne zaman, bir veri kümesine bağlı <xref:System.Windows.FrameworkElement.Height%2A> , <xref:System.Windows.Controls.DataGrid> olduğu sınırlı değil, bu bağımlı veri kümesindeki her bir veri öğesi için bir satır eklemek devam edecektir. Bu neden <xref:System.Windows.Controls.DataGrid> kaydedildikçe uygulamanızın görünür sınırların dışında kalan satırlar eklenir. <xref:System.Windows.Controls.DataGrid> Kaydırma çubukları çünkü bu durumda gösterilmez, <xref:System.Windows.FrameworkElement.Height%2A> yeni satırlar uyum sağlayacak şekilde büyümeye devam edecektir.  
  
 Her satır için bir nesne oluşturulması <xref:System.Windows.Controls.DataGrid>. Büyük bir veri kümesiyle çalıştığınız ve izin <xref:System.Windows.Controls.DataGrid> otomatik olarak kendisini boyutlandırmak için çok sayıda nesnelerin oluşturulması, uygulamanızın performansını etkileyebilir.  
  
 Büyük veri kümeleriyle çalışırken bu sorunlarla karşılaşmamak için özellikle ayarlamanız önerilir <xref:System.Windows.FrameworkElement.Height%2A> , <xref:System.Windows.Controls.DataGrid> veya kısıtlar bir kapsayıcıda yerleştir kendi <xref:System.Windows.FrameworkElement.Height%2A>, gibi bir <xref:System.Windows.Controls.Grid>. Zaman <xref:System.Windows.FrameworkElement.Height%2A> kısıtlanmıştır <xref:System.Windows.Controls.DataGrid> yalnızca belirtilen kendi içinde uygun satırları oluşturacak <xref:System.Windows.FrameworkElement.Height%2A>ve bu satırların yeni verileri görüntülemek için gerektiği gibi geri.  
  
### <a name="setting-the-datagrid-size"></a>DataGrid boyutunu ayarlama  
 <xref:System.Windows.Controls.DataGrid> Otomatik olarak belirlenen sınırlar içinde boyutu ayarlanabilir veya <xref:System.Windows.Controls.DataGrid> için belirli bir boyutu ayarlanabilir. Aşağıdaki tablo denetimi için ayarlayabileceği özelliklerini gösterir <xref:System.Windows.Controls.DataGrid> boyutu.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Belirli bir yükseklikte için ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Yüksekliğini üst sınırını ayarlar <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Bu yükseklik ulaşana kadar dikey olarak çıkarılır.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Yüksekliği için alt sınır ayarlar <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Bu yükseklik ulaşana kadar dikey olarak küçülür.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Belirli bir genişlikte için ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Genişliğini üst sınırını ayarlar <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Bu genişliği ulaşana kadar yatay olarak çıkarılır.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Genişliği için alt sınır ayarlar <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Bu genişliği ulaşana kadar yatay olarak küçülür.|  
  
## <a name="sizing-rows-and-row-headers"></a>Boyutlandırma satırları ve satır başlıkları  
  
### <a name="datagrid-rows"></a>DataGrid satırları  
 Varsayılan olarak, bir <xref:System.Windows.Controls.DataGrid> sıranın <xref:System.Windows.FrameworkElement.Height%2A> özelliği <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" XAML içindeki), ve satır yüksekliği içeriğini boyuta genişletir. Tüm satırların yüksekliğini <xref:System.Windows.Controls.DataGrid> ayarlayarak belirtilebilir <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> özelliği. Kullanıcılar, satır yüksekliğini satır üst bilgisi Bölücü sürükleyerek değiştirebilirsiniz.  
  
### <a name="datagrid-row-headers"></a>DataGrid satır başlıkları  
 Satır üst bilgileri, görüntülenecek <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> özelliği ayarlanmalıdır <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> veya <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>. Varsayılan olarak, satır başlıkları görüntülenir ve bunlar kendi içeriğin sığması için otomatik olarak boyutu. Satır başlıklarının ayarlayarak belirli bir genişlikte verilebilir <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="sizing-columns-and-column-headers"></a>Sütunları ve sütun üst bilgilerini boyutlandırma  
  
### <a name="datagrid-columns"></a>DataGrid sütunları  
 <xref:System.Windows.Controls.DataGrid> Değerleri kullanan <xref:System.Windows.Controls.DataGridLength> ve <xref:System.Windows.Controls.DataGridLengthUnitType> yapısı mutlak veya otomatik boyutlandırma modlarını belirtin.  
  
 Tarafından sağlanan değerleri aşağıdaki tabloda gösterilmektedir <xref:System.Windows.Controls.DataGridLengthUnitType> yapısı.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Otomatik boyutlandırma modunu boyutları varsayılan <xref:System.Windows.Controls.DataGrid> sütunları hücreleri hem de sütun başlıklarını içeriğine bağlı.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Hücre tabanlı otomatik boyutlandırma modunu boyutları <xref:System.Windows.Controls.DataGrid> sütun başlıkları dahil değil sütundaki hücrelerin içeriğinin sütunları temel.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Üst bilgi tabanlı otomatik boyutlandırma modunu boyutları <xref:System.Windows.Controls.DataGrid> sütunları yalnızca sütun üst bilgilerini içeriğine bağlı.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Piksel tabanlı boyutlandırma modunu boyutları <xref:System.Windows.Controls.DataGrid> sütunları temel sağlanan sayısal değeri.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Yıldız boyutlandırma modunu ağırlıklı oranlarını tarafından kullanılabilir alanı dağıtmak için kullanılır.<br /><br /> XAML içinde yıldız değerleri n n sayısal bir değeri temsil ettiği * ifade edilir. 1\* eşdeğerdir \*. Örneğin, iki sütun bir <xref:System.Windows.Controls.DataGrid> genişlikleri vardı \* ve 2\*, ilk sütuna kadar kullanılabilir alan bir bölümü alırsınız ve ikinci sütunda kullanılabilir alanı iki bölümünü alırsınız.|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter> Sınıfı, sayı veya dize değerleri arasında verileri dönüştürmek için kullanılabilir ve <xref:System.Windows.Controls.DataGridLength> değerleri.  
  
 Varsayılan olarak, <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>ve <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Controls.DataGridLength.Auto%2A>. Boyutlandırma modunu ayarlandığında <xref:System.Windows.Controls.DataGridLength.Auto%2A> veya <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>, sütunları en geniş görünür içeriklerinin genişliğine büyüme. Kaydırma sırasında bu boyutlandırma modlarını içerik, genişletilecek sütunları sütun boyutunu geçerli görünüme kaydırılan daha büyük olan neden olur. İçerik görünümü dışında kaydırılan sonra sütunu Daralt değil.  
  
 Sütunlarda <xref:System.Windows.Controls.DataGrid> boyutu yalnızca belirtilen sınırlar içinde otomatik olarak da ayarlanabilir veya sütun için belirli bir boyutu ayarlanabilir. Aşağıdaki tabloda sütun boyutları denetlemek için ayarlanabilen özelliklerini gösterir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Tüm sütunlar için üst sınır ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Tek bir sütun üst sınırını ayarlar. Geçersiz kılmalar <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Tüm sütunlar için alt sınır ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Tek bir sütun alt sınırını ayarlar. Geçersiz kılmalar <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Tüm sütunlar için belirli bir genişlikte ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Tek bir sütun için belirli bir genişlikte ayarlar. Geçersiz kılmalar <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>.|  
  
### <a name="datagrid-column-headers"></a>DataGrid sütun başlıkları  
 Varsayılan olarak, <xref:System.Windows.Controls.DataGrid> sütun başlıkları görüntülenir. Sütun başlıklarını gizleme <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> özelliği ayarlanmalıdır <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> veya <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>. Sütun üst bilgilerini görüntülendiğinde varsayılan olarak, bunlar otomatik olarak kendi İçeriği sığdırmak için boyutu. Sütun başlıklarını ayarlayarak belirli bir yükseklikte verilebilir <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> özelliği.  
  
### <a name="resizing-with-the-mouse"></a>Fare ile yeniden boyutlandırma  
 Kullanıcıların yeniden boyutlandırılabilir <xref:System.Windows.Controls.DataGrid> satırları ve sütunları satır veya sütun üst bilgisi Bölücü sürükleyerek. <xref:System.Windows.Controls.DataGrid> Ayrıca otomatik satırları ve sütunları satır veya sütun başlık ayırıcıya çift tıklayarak yeniden boyutlandırılmasını destekler. Bir kullanıcı, belirli sütunları yeniden boyutlandırmasını önleyecek şekilde ayarlanmış <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> özelliğini `false` tek tek sütun. Kullanıcılar, tüm sütunları yeniden boyutlandırmasını önleyecek şekilde ayarlanmış <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> özelliğini `false`. Kullanıcılar, tüm satırları yeniden boyutlandırmasını önleyecek şekilde ayarlanmış <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> özelliğini `false`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>

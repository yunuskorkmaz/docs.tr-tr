---
title: "DataGrid Denetimindeki Boyutlandırma Seçenekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eee894b536b19ec38a9809ab5dc49f5682c1df9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sizing-options-in-the-datagrid-control"></a>DataGrid Denetimindeki Boyutlandırma Seçenekleri
Çeşitli seçenekleri denetlemek için kullanılabilen nasıl <xref:System.Windows.Controls.DataGrid> kendisini boyutları. <xref:System.Windows.Controls.DataGrid>Ve tek tek satır ve sütun <xref:System.Windows.Controls.DataGrid>, otomatik olarak içeriklerini için boyut için ayarlayabilirsiniz veya belirli değerler için ayarlanabilir. Varsayılan olarak, <xref:System.Windows.Controls.DataGrid> büyür ve içeriğinin boyutuna uyacak şekilde daraltma.  
  
## <a name="sizing-the-datagrid"></a>DataGrid boyutlandırma  
  
### <a name="cautions-when-using-automatic-sizing"></a>Otomatik boyutlandırma kullanırken uyarılar  
 Varsayılan olarak, <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özelliklerini <xref:System.Windows.Controls.DataGrid> ayarlanır <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" XAML'de) ve <xref:System.Windows.Controls.DataGrid> içeriğinin boyutunu ayarlayın.  
  
 Alt öğelerini boyutu gibi kısıtlamaz bir kapsayıcı yerleştirildiğinde bir <xref:System.Windows.Controls.Canvas> veya <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.DataGrid> kapsayıcı görünür sınırları uzatılır ve scrollbars değil gösterilecek. Bu durum, kullanılabilirlik ve performans etkilere sahiptir.  
  
 Bir veri kümesi için zaman bağlı <xref:System.Windows.FrameworkElement.Height%2A> , <xref:System.Windows.Controls.DataGrid> olduğu sınırlı değil, ilişkili veri kümesindeki her bir veri öğesi için bir satır eklemek devam edecektir. Bu neden <xref:System.Windows.Controls.DataGrid> satırları eklendikçe uygulamanızı görünür sınırların dışında kalan büyümeye. <xref:System.Windows.Controls.DataGrid> Scrollbars çünkü bu durumda göstermez kendi <xref:System.Windows.FrameworkElement.Height%2A> yeni satırlar uyum sağlayacak şekilde büyümeye devam edecek.  
  
 Her satır için bir nesne oluşturduğunuz <xref:System.Windows.Controls.DataGrid>. Büyük bir veri kümesi ile çalışıyorsanız ve izin <xref:System.Windows.Controls.DataGrid> otomatik olarak kendisini boyutu için çok sayıda nesneleri oluşturma, uygulamanızın performansını etkileyebilir.  
  
 Büyük veri kümeleriyle çalışırken bu sorunları önlemek için özellikle ayarlamanız önerilir <xref:System.Windows.FrameworkElement.Height%2A> , <xref:System.Windows.Controls.DataGrid> veya kısıtlar bir kapsayıcıda yerleştirin, <xref:System.Windows.FrameworkElement.Height%2A>, gibi bir <xref:System.Windows.Controls.Grid>. Zaman <xref:System.Windows.FrameworkElement.Height%2A> kısıtlandığı <xref:System.Windows.Controls.DataGrid> yalnızca kendi belirtilen içinde sığacak satırları oluşturacak <xref:System.Windows.FrameworkElement.Height%2A>ve bu satırları yeni verileri görüntülemek için gerektiği şekilde geri.  
  
### <a name="setting-the-datagrid-size"></a>DataGrid boyutunu ayarlama  
 <xref:System.Windows.Controls.DataGrid> Belirtilen sınır içinde otomatik olarak bir boyut ayarlayabilirsiniz veya <xref:System.Windows.Controls.DataGrid> belirli bir boyuta ayarlayabilirsiniz. Aşağıdaki tabloda denetimine ayarlanabilir özellikleri gösterir <xref:System.Windows.Controls.DataGrid> boyutu.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Belirli bir yükseklikte için ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Yüksekliği için üst sınır ayarlar <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Bu yükseklik ulaşana kadar dikey büyüyecektir.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Alt sınır yüksekliği için ayarlar <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Bu yükseklik ulaşana kadar dikey olarak küçülür.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Belirli bir genişlikte için ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Genişliği için üst sınır ayarlar <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Bu genişliği ulaşana kadar yatay büyüyecektir.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Genişliği için alt sınır ayarlar <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Bu genişliği ulaşana kadar yatay olarak küçülür.|  
  
## <a name="sizing-rows-and-row-headers"></a>Satırları ve satır üstbilgilerinin boyutlandırma  
  
### <a name="datagrid-rows"></a>DataGrid satırları  
 Varsayılan olarak, bir <xref:System.Windows.Controls.DataGrid> sıranın <xref:System.Windows.FrameworkElement.Height%2A> özelliği ayarlanmış <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" XAML'de), ve satır yüksekliğini içeriğinin boyutunu genişletilir. Tüm satırların yüksekliğini <xref:System.Windows.Controls.DataGrid> ayarlayarak belirtilen <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> özelliği. Kullanıcılar, Satır üstbilgisi Bölücü sürükleyerek satır yüksekliğini değiştirebilirsiniz.  
  
### <a name="datagrid-row-headers"></a>DataGrid satır üstbilgileri  
 Satır üstbilgilerinin görüntülenecek <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> özelliği ayarlanmalıdır <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> veya <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>. Varsayılan olarak, bunlar otomatik olarak kendi içeriğin sığması için boyutlandırma ve satır üstbilgilerinin görüntülenir. Satır başlıklarının ayarlayarak belirli bir genişlikte verilebilir <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="sizing-columns-and-column-headers"></a>Boyutlandırma sütunlar ve sütun üst bilgileri  
  
### <a name="datagrid-columns"></a>DataGrid sütunları  
 <xref:System.Windows.Controls.DataGrid> Değerleri kullanan <xref:System.Windows.Controls.DataGridLength> ve <xref:System.Windows.Controls.DataGridLengthUnitType> yapısı mutlak ya da otomatik boyutlandırma modlarını belirtin.  
  
 Tarafından sağlanan değerler aşağıdaki tabloda gösterilmektedir <xref:System.Windows.Controls.DataGridLengthUnitType> yapısı.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Varsayılan mod boyutları boyutlandırma otomatik <xref:System.Windows.Controls.DataGrid> sütunları hücre ve sütun üst bilgileri içeriğine bağlı.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Hücre tabanlı otomatik modu boyutları boyutlandırma <xref:System.Windows.Controls.DataGrid> sütunları temel alarak sütununda, sütun başlıkları dahil edilmez hücrelerin içeriği.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Üstbilgi tabanlı otomatik modu boyutları boyutlandırma <xref:System.Windows.Controls.DataGrid> sütunları yalnızca sütun üst bilgileri içeriğine bağlı.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Piksel tabanlı modu boyutları boyutlandırma <xref:System.Windows.Controls.DataGrid> sütunları dayalı sağlanan sayısal değer.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Yıldız boyutlandırma modunu ağırlıklı oranları tarafından kullanılabilir alan dağıtmak için kullanılır.<br /><br /> XAML'de yıldız değerleri n n sayısal bir değeri temsil ettiği * ifade edilir. 1\* eşdeğerdir \*. Örneğin, iki sütun bir <xref:System.Windows.Controls.DataGrid> genişliklerini vardı \* ve 2\*, ilk sütun kullanılabilir alan bir kısmını alacağı ve ikinci sütunda kullanılabilir alan iki bölümlerini alacaksınız.|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter> Sınıfı, sayısal veya dize değerleri arasında verileri dönüştürmek için kullanılabilir ve <xref:System.Windows.Controls.DataGridLength> değerleri.  
  
 Varsayılan olarak, <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> özelliği ayarlanmış <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>ve <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> özelliği ayarlanmış <xref:System.Windows.Controls.DataGridLength.Auto%2A>. Boyutlandırma modunu ayarlandığında <xref:System.Windows.Controls.DataGridLength.Auto%2A> veya <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>, sütunları en geniş görünür içeriklerini genişliğini büyümesine. Kaydırma sırasında bu boyutlandırma modları içerik, genişletilecek sütunları, geçerli sütun boyutu görünüme kaydırılan büyük neden olur. İçerik görünümü dışında kaydırılan sonra sütun küçülür değil.  
  
 Sütunlarda <xref:System.Windows.Controls.DataGrid> da yalnızca belirtilen sınır içinde otomatik olarak bir boyut ayarlanabilir veya belirli bir boyuta sütunları ayarlanabilir. Aşağıdaki tablo, sütun boyutlarını denetlemek için ayarlanabilir özellikleri gösterir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Tüm sütunlar için üst sınır ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Tek bir sütun için üst sınır ayarlar. Geçersiz kılmaları <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Tüm sütunlar için alt sınır ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Tek bir sütun için alt sınır ayarlar. Geçersiz kılmaları <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Tüm sütunlar için belirli bir genişlikte ayarlar <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Tek bir sütun için belirli bir genişlikte ayarlar. Geçersiz kılmaları <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>.|  
  
### <a name="datagrid-column-headers"></a>DataGrid sütun üst bilgileri  
 Varsayılan olarak, <xref:System.Windows.Controls.DataGrid> sütun üst bilgileri görüntülenir. Sütun üstbilgileri gizlemek için <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> özelliği ayarlanmalıdır <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> veya <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>. Sütun başlığı görüntülendiğinde, varsayılan olarak, bunlar otomatik olarak kendi içeriğin sığması için boyutlandırma. Sütun üstbilgileri ayarlayarak belirli bir yükseklikte verilebilir <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> özelliği.  
  
### <a name="resizing-with-the-mouse"></a>Fareyle yeniden boyutlandırma  
 Kullanıcılar yeniden boyutlandır <xref:System.Windows.Controls.DataGrid> satırları ve sütunları satır veya sütun başlığı Bölücü sürükleyerek. <xref:System.Windows.Controls.DataGrid> De otomatik satırları ve sütunları satır veya sütun başlığı ayırıcısını çift tıklatarak yeniden boyutlandırılmasını destekler. Bir kullanıcının belirli sütunları yeniden boyutlandırma önlemek için ayarlayın <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> özelliğine `false` bireysel sütunlar için. Tüm sütunları yeniden boyutlandırma kullanıcılar engelleyecek şekilde ayarlanmışsa <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> özelliğine `false`. Kullanıcılar tüm satırları yeniden boyutlandırma engelleyecek şekilde ayarlanmışsa <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> özelliğine `false`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGridColumn>  
 <xref:System.Windows.Controls.DataGridLength>  
 <xref:System.Windows.Controls.DataGridLengthConverter>

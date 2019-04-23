---
title: PresentationOptions:Freeze Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: e60c4a505db42936f188354f52edd7832fb9632b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074670"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze Özniteliği
Kümeleri <xref:System.Windows.Freezable.IsFrozen%2A> durumunu `true` çağırılarak <xref:System.Windows.Freezable> öğesi. Varsayılan davranışı bir <xref:System.Windows.Freezable> olmadan `PresentationOptions:Freeze` belirtilen özniteliği olan <xref:System.Windows.Freezable.IsFrozen%2A> olduğu `false` yükleme süresi ve genel bağlıdır <xref:System.Windows.Freezable> çalışma zamanında davranış.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`PresentationOptions`|XML 1.0 belirtimi başına herhangi bir geçerli önek dizesi olabilir bir XML ad alanı ön eki. Önek `PresentationOptions` bu belgelerde tanımlama amacıyla kullanılır.|  
|`freezableElement`|Herhangi bir örneğini oluşturan bir öğe türetilmiş sınıf <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Freeze` Tek özniteliği bir özniteliktir veya diğer programlama öğesine tanımlanan `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML ad alanı. `Freeze` Özniteliği var. Bu özel ad alanında özellikle bu şekilde yoksayılabilir, kullanarak belirlenebilir böylece [mc: Ignorable özniteliği](mc-ignorable-attribute.md) kök öğesi bildirimlerinin bir parçası olarak. Nedeni, `Freeze` yoksayılabilir olmalıdır çünkü tüm değil [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamalarıdır dondurmak için bir <xref:System.Windows.Freezable> yükleme zamanında; bu özellik değil parçası [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtimi.  
  
 İşleme yeteneği `Freeze` özniteliği özellikle yerleşik için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işler İşlemci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derlenmiş uygulamalar. Öznitelik herhangi bir sınıf tarafından desteklenmiyor ve öznitelik sözdizimi, genişletilebilir veya değiştirilebilir değildir. Kendi uyguluyorsanız, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dondurma davranışını paralel seçebilirsiniz İşlemci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlerken İşlemci `Freeze` özniteliği <xref:System.Windows.Freezable> yükleme zamanında öğeleri.  
  
 Herhangi bir değer `Freeze` dışında özniteliği `true` (büyük/küçük harfe duyarlı değil) bir yükleme zamanı hatası oluşturur. (Belirtme `Freeze` olarak özniteliği `false` bir hata değildir, ancak zaten şekilde ayarlayarak varsayılan `false` hiçbir şey yapılmaz).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Freezable>
- [Freezable Nesnelerine Genel Bakış](freezable-objects-overview.md)
- [mc:Ignorable Özniteliği](mc-ignorable-attribute.md)

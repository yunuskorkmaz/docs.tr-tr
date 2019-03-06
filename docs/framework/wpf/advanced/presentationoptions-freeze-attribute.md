---
title: PresentationOptions:Freeze Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: 3ff4a3221392d6b247d0a486e4e1f0406f539362
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378876"
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

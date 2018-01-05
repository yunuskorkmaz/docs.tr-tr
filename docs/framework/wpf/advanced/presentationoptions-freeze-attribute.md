---
title: "PresentationOptions:Freeze Özniteliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb305c69cec7c4e4766153ae64d37b19ab0bccea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze Özniteliği
Ayarlar <xref:System.Windows.Freezable.IsFrozen%2A> durumunu `true` çağırılarak <xref:System.Windows.Freezable> öğesi. Varsayılan davranışı bir <xref:System.Windows.Freezable> olmadan `PresentationOptions:Freeze` belirtilen özniteliği olan <xref:System.Windows.Freezable.IsFrozen%2A> olan `false` yükleme süresini ve genel bağımlı <xref:System.Windows.Freezable> çalışma zamanında davranışı.  
  
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
|`PresentationOptions`|XML 1.0 belirtimi başına herhangi bir geçerli önek dizesi olabilen bir XML ad alanı öneki. Önek `PresentationOptions` bu belgede tanımlama amacıyla kullanılır.|  
|`freezableElement`|Başlatır herhangi bir öğeyi türetilmiş sınıf <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Freeze` Özniteliktir yalnızca öznitelik veya diğer programlama öğenin tanımlandığı `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML ad alanı. `Freeze` Özniteliği var. Bu özel ad alanında özellikle bu şekilde yoksayılabilir, kullanarak belirlenebilir böylece [mc: yoksayılabilir özniteliği](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) kök öğesi bildirimlerinin bir parçası olarak. Nedeni, `Freeze` yoksayılabilir kurabilmesi gerekir çünkü tüm değil [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi uygulamaları Dondur mümkün bir <xref:System.Windows.Freezable> yükleme zamanında; bu özelliği değil parçası [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtimi.  
  
 İşleme yeteneği `Freeze` özniteliği özellikle yerleşik için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işler İşlemci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derlenmiş uygulamalar. Öznitelik herhangi bir sınıf tarafından desteklenmiyor ve öznitelik sözdizimi genişletilebilir veya değiştirilebilir değil. Kendi uyguluyorsanız, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dondurma davranışına paralel seçebilirsiniz İşlemci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlerken İşlemci `Freeze` özniteliği <xref:System.Windows.Freezable> yükleme zamanında öğeleri.  
  
 Herhangi bir değer `Freeze` dışında özniteliği `true` (büyük/küçük harfe duyarlı değildir) bir yükleme zamanı hatası oluşturur. (Belirtme `Freeze` olarak özniteliği `false` bir hata değildir, ancak zaten şekilde ayarlamak varsayılan `false` hiçbir şey yapmaz).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Freezable>  
 [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [mc:Ignorable Özniteliği](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)

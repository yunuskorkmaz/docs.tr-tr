---
title: PresentationOptions:Freeze Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991423"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze Özniteliği
<xref:System.Windows.Freezable.IsFrozen%2A> Durumu `true` kapsayan öğe<xref:System.Windows.Freezable> üzerinde olarak ayarlar. Belirtilen <xref:System.Windows.Freezable> özniteliğiolmadan`PresentationOptions:Freeze` bir için varsayılan davranış, yükleme zamanında ve çalışma zamanında genel <xref:System.Windows.Freezable> davranışa bağımlıdır. <xref:System.Windows.Freezable.IsFrozen%2A> `false`  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
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
|`PresentationOptions`|XML 1,0 belirtimine göre geçerli herhangi bir ön ek dizesi olabilen bir XML ad alanı öneki. Bu belgede `PresentationOptions` tanımlama amacıyla ön ek kullanılır.|  
|`freezableElement`|Türetilmiş herhangi bir sınıfını <xref:System.Windows.Freezable>örnekleyen öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 Özniteliği, `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML ad alanında tanımlanmış tek öznitelik veya diğer programlama öğesidir. `Freeze` Özniteliği `Freeze` , bu özel ad alanında özellikle, kök öğe bildirimlerinin bir parçası olarak, [mc: Ignorable özniteliği](mc-ignorable-attribute.md) kullanılarak, yoksayılabilir olarak atanabilmesi için vardır. Tüm `Freeze` <xref:System.Windows.Freezable> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamalarının yükleme süresini donduramadığı, ancak bu özellik, belirtiminin bir parçası olmadığı için, yoksayılabilir olması gereken neden olur. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `Freeze` Özniteliği işleyebilme özelliği, derlenmiş uygulamalar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] için işlenen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcide özellikle de yerleşiktir. Özniteliği hiçbir sınıf tarafından desteklenmez ve öznitelik sözdizimi genişletilebilir veya değiştirilebilir değildir. Kendi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinizi uygulamadıysanız, yükleme zamanında <xref:System.Windows.Freezable> öğelerde `Freeze` özniteliği işlerken, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin donduruyor davranışını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paralel olarak seçebilirsiniz.  
  
 (Büyük/küçük `Freeze` harfe duyarlı değil) dışındaki öznitelik için herhangi bir değer bir yükleme zamanı hatası oluşturur. `true` `Freeze` ( `false` Özniteliği bir hata değil, ancak zaten varsayılan değer, bu nedenle hiçbir şey yapmaz). `false`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Freezable>
- [Freezable Nesnelerine Genel Bakış](freezable-objects-overview.md)
- [mc:Ignorable Özniteliği](mc-ignorable-attribute.md)

---
title: UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
description: Kullanıcı Arabirimi Otomasyonu 'nda dönüşüm denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. Iransformprovider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: da11ce4cf9da10c0ebb990f9439b0bbe3621c561
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168210"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda <xref:System.Windows.Automation.Provider.ITransformProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.TransformPattern>Denetim stili, iki boyutlu bir boşluk içinde taşınabilecek, yeniden boyutlandırılabileceğini veya döndürülebilen denetimleri desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Dönüşüm denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- Bu denetim deseninin desteği masaüstündeki nesnelerle sınırlı değildir. Bu denetim deseninin ayrıca alt öğeler, kapsayıcının sınırları içinde taşınabileceği, yeniden boyutlandırılabileceği veya serbest bir şekilde döndürülebilen bir kapsayıcı nesnesinin alt öğeleri tarafından desteklenmelidir.  
  
- Bir nesne, sonuçta elde edilen ekran konumunun kendi kapsayıcısının koordinatları dışında ve bu nedenle klavye veya fareye erişilemeyen (örneğin, üst düzey bir pencere ekrandan taşındığında veya bir alt nesne kapsayıcının Görünüm penceresinin sınırları dışına taşındığında), yeniden boyutlandırılıp döndürülemez. Bu gibi durumlarda, nesne, kapsayıcı sınırları dahilinde olacak şekilde geçersiz kılınan üstteki veya soldaki koordinatlarla mümkün olduğunca istenen ekran koordinatlarına yakın şekilde yerleştirilir.  
  
- Çoklu izleyici sistemlerinde, bir nesne birleştirilmiş masaüstü ekran koordinatları dışında taşındığında, yeniden boyutlandırılırsa veya döndürülürse, nesne birincil monitöre istenen koordinatlara yakın şekilde yerleştirilir.  
  
- Tüm parametreler ve özellik değerleri mutlak ve yerel ayardan bağımsızdır.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-itransformprovider"></a>Iransformprovider için gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.ITransformProvider> .  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Yöntem|Hiçbiri|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> - <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> False ise.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> - <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> False ise.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> - <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> False ise.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)

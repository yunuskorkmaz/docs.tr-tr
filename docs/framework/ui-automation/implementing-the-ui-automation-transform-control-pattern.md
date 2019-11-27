---
title: UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: c0a46580ad2673b56fefe7228f2549a2e19d2c14
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447063"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.ITransformProvider>uygulamak için yönergeler ve kurallar tanıtılmaktadır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.TransformPattern> denetim deseninin iki boyutlu bir boşluk içinde taşınabilecek, yeniden boyutlandırılabileceği veya döndürülebilen denetimleri desteklemesi için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Dönüşüm denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- Bu denetim deseninin desteği masaüstündeki nesnelerle sınırlı değildir. Bu denetim deseninin ayrıca alt öğeler, kapsayıcının sınırları içinde taşınabileceği, yeniden boyutlandırılabileceği veya serbest bir şekilde döndürülebilen bir kapsayıcı nesnesinin alt öğeleri tarafından desteklenmelidir.  
  
- Bir nesne, sonuçta elde edilen ekran konumu kendi kapsayıcısının koordinatları dışında ve bu nedenle klavye veya fareye erişilemeyen (örneğin, üst düzey bir pencere ekrandan veya bir alt nesne, kapsayıcının Görünüm penceresinin sınırlarının dışına taşınır. Bu gibi durumlarda, nesne, kapsayıcı sınırları dahilinde olacak şekilde geçersiz kılınan üstteki veya soldaki koordinatlarla mümkün olduğunca istenen ekran koordinatlarına yakın şekilde yerleştirilir.  
  
- Çoklu izleyici sistemlerinde, bir nesne birleştirilmiş masaüstü ekran koordinatları dışında taşındığında, yeniden boyutlandırılırsa veya döndürülürse, nesne birincil monitöre istenen koordinatlara yakın şekilde yerleştirilir.  
  
- Tüm parametreler ve özellik değerleri mutlak ve yerel ayardan bağımsızdır.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Iransformprovider için gerekli Üyeler  
 <xref:System.Windows.Automation.Provider.ITransformProvider>uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Yöntem|Yok.|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -<xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> yanlışsa.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -<xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> yanlışsa.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -<xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> yanlışsa.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)

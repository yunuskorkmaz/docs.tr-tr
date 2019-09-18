---
title: UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: fbcb7b274144281d88d8fb36b9cb55043658a6a9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043106"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında <xref:System.Windows.Automation.Provider.ITransformProvider>bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.TransformPattern> Denetim stili, iki boyutlu bir boşluk içinde taşınabilecek, yeniden boyutlandırılabileceğini veya döndürülebilen denetimleri desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Dönüşüm denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- Bu denetim deseninin desteği masaüstündeki nesnelerle sınırlı değildir. Bu denetim deseninin ayrıca alt öğeler, kapsayıcının sınırları içinde taşınabileceği, yeniden boyutlandırılabileceği veya serbest bir şekilde döndürülebilen bir kapsayıcı nesnesinin alt öğeleri tarafından desteklenmelidir.  
  
- Bir nesne, sonuçta elde edilen ekran konumu kendi kapsayıcısının koordinatları dışında ve bu nedenle klavye veya fareye erişilemeyen (örneğin, üst düzey bir pencere ekrandan veya bir alt nesne, kapsayıcının Görünüm penceresinin sınırlarının dışına taşınır. Bu gibi durumlarda, nesne, kapsayıcı sınırları dahilinde olacak şekilde geçersiz kılınan üstteki veya soldaki koordinatlarla mümkün olduğunca istenen ekran koordinatlarına yakın şekilde yerleştirilir.  
  
- Çoklu izleyici sistemlerinde, bir nesne birleştirilmiş masaüstü ekran koordinatları dışında taşındığında, yeniden boyutlandırılırsa veya döndürülürse, nesne birincil monitöre istenen koordinatlara yakın şekilde yerleştirilir.  
  
- Tüm parametreler ve özellik değerleri mutlak ve yerel ayardan bağımsızdır.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Iransformprovider için gerekli Üyeler  
 Uygulamak <xref:System.Windows.Automation.Provider.ITransformProvider>için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
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
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -False ise <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> .|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -False ise <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> .|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -False ise <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)

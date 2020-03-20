---
title: UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: 5643bc85972ea33cc31b1a83ecf7615dbb275bc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180046"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, özellikler, yöntemler ve <xref:System.Windows.Automation.Provider.ITransformProvider>olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar konunun sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.TransformPattern> deseni, iki boyutlu bir boşluk içinde taşınabilen, yeniden boyutlandırılabilen veya döndürülebilen denetimleri desteklemek için kullanılır. Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Dönüşüm denetimi modelini uygularken aşağıdaki yönergeleri ve kuralları not edin:  
  
- Bu denetim deseni desteği masaüstündeki nesnelerle sınırlı değildir. Çocuklar kapsayıcının sınırları içinde taşınabilir, yeniden boyutlandırılabilir veya serbestçe döndürülebiliyorsa, bu denetim deseni bir kapsayıcı nesnesinin alt ları tarafından da desteklenmelidir.  
  
- Bir nesne, ortaya çıkan ekran konumunun kapsayıcısının koordinatlarının tamamen dışında olacağı şekilde hareket ettirilemez, yeniden boyutlandırılamaz veya döndürülemez ve bu nedenle klavye veya fare tarafından erişilemez (örneğin, üst düzey bir pencere ekrandan veya alt nesne kapsayıcının viewport sınırları nın dışına taşınır). Bu gibi durumlarda, nesne, kapsayıcı sınırları içinde olmak üzere geçersiz kılınmış üst veya sol koordinatları ile istenilen ekran koordinatlarına mümkün olduğunca yakın yerleştirilir.  
  
- Çoklu monitör sistemlerinde, bir nesne taşınır, yeniden boyutlandırılır veya birleştirilmiş masaüstü ekran koordinatlarının dışına tamamen döndürülürse, nesne istenen koordinatlara mümkün olduğunca yakın olarak birincil monitöre yerleştirilir.  
  
- Tüm parametreler ve özellik değerleri mutlak ve yerel bağımsızdır.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-itransformprovider"></a>ITransformProvider için Gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve <xref:System.Windows.Automation.Provider.ITransformProvider>yöntemler gereklidir.  
  
|Gerekli üyeler|Üye tipi|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Yöntem|None|  
  
 Bu denetim deseni ilişkili olaylar vardır.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları atmalıdır.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> - Eğer <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> yanlış.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> - Eğer <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> yanlış.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> - Eğer <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> yanlış.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)

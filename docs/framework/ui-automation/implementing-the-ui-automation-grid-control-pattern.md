---
title: UI Otomasyon Kılavuz Denetim Düzenini Uygulama
description: UI otomasyonunda Griddeseninin kılavuz denetim deseninin uygulanması için kılavuzları ve kuralları anlayın. Igrprovider arabirimini uygulamayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: c7aae8e8070c989c4b36e0581aa5f48f51416f97
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165869"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>UI Otomasyon Kılavuz Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda <xref:System.Windows.Automation.Provider.IGridProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.GridPattern>Denetim stili, alt öğelerin bir koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri, <xref:System.Windows.Automation.Provider.IGridItemProvider> satır ve sütun tarafından geçilen iki boyutlu bir mantıksal koordinat sisteminde uygulamanız ve düzenlenmelidir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Kılavuz denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Izgara koordinatları, koordinatlara sahip (0, 0) sol üst (veya yerel ayara bağlı olarak sağ üst hücre) ile sıfır tabanlıdır.  
  
- Bir hücre boşsa, bu hücrenin özelliğini desteklemek için bir UI Otomasyon öğesi döndürülmeye devam etmelidir <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> . Kılavuzdaki alt öğelerin düzeni düzensiz bir diziye benzediğinde bu mümkündür (aşağıdaki örneğe bakın).  
  
 ![Düzensiz düzeni gösteren Windows Gezgini görünümü.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Boş koordinatları olan Grid denetimine örnek  
  
- Tek bir öğe içeren bir ızgara, <xref:System.Windows.Automation.Provider.IGridProvider> mantıksal olarak bir kılavuz olarak kabul edildiğinde uygulanması gerekir. Kılavuzdaki alt öğe öğelerinin sayısı immalzemedir.  
  
- Sağlayıcı uygulamasına bağlı olarak gizli satırlar ve sütunlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaca yüklenebilir ve bu nedenle, <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> ve özelliklerine yansıtılacaktır <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> . Gizli satırlar ve sütunlar henüz yüklenmediyse, bunlar sayılmaz.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>bir kılavuzun etkin işlemesini etkinleştirmez; <xref:System.Windows.Automation.Provider.ITransformProvider>Bu işlevi etkinleştirmek için uygulanması gerekir.  
  
- <xref:System.Windows.Automation.StructureChangedEventHandler>Eklenmiş, kaldırılmış veya birleştirilmiş hücreler gibi kılavuzda yapısal veya Düzen değişikliklerini dinlemek için bir kullanın.  
  
- Bir <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> kılavuzun öğeleri veya hücreleri aracılığıyla çapraz geçişi izlemek için kullanın.  
  
<a name="Required_Members_for_IGridProvider"></a>
## <a name="required-members-for-igridprovider"></a>Igrprovider için gerekli Üyeler  
 Aşağıdaki özellikler ve Yöntemler ıgrprovider arabirimini uygulamak için gereklidir.  
  
|Gerekli Üyeler|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Yöntem|Hiçbiri|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır koordinatı öğesinden daha büyükse <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> veya sütun koordinatı öğesinden daha büyükse <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A> .|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> -İstenen satır veya sütun koordinatlarından herhangi biri sıfırdan küçükse.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon GridItem Denetim Düzeni Uygulama](implementing-the-ui-automation-griditem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)

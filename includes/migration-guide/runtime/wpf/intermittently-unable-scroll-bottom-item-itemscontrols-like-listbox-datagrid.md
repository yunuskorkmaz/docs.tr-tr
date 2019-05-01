---
ms.openlocfilehash: 9c2ee4ba66deb7c3b33698963add2b8a7e70069f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649596"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Aralıklı olarak oluşturulamıyor (örneğin, liste ve DataGrid) ItemsControls alt öğeye ilerlemek özel DataTemplates kullanırken

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, .NET Framework 4.5 hatada ItemsControls neden oluyor (gibi <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, vs.) için kendi alt öğesi özel DataTemplates kullanırken kaydırma değil. Kaydırma (Yedekleme kaydırma sonra) ikinci bir kez girişiminde bulunulursa, sonra çalışır.|
|Öneri|Bu sorun, .NET Framework 4.5.2 sabit ve bu sürümü (veya sonraki bir sürümü) .NET Framework'ün yükselterek desteklenebilir. Alternatif olarak, kullanıcılar yine de bu koleksiyonlardaki son öğelerine kaydırma çubukları sürükleyebilirsiniz, ancak iki kez başarıyla Bunu yapmak denemeniz gerekebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
